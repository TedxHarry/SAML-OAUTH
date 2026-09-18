# The first complete SP-initiated login

**ID:** SAML-001\
**Depth:** Core\
**Prerequisites:** [FND-001](../part-foundations/FND-001-login-access-and-account-lifecycle.md), [FND-002](../part-foundations/FND-002-following-the-browser-and-its-sessions.md), [FND-003](../part-foundations/FND-003-artifact-creators-and-consumers.md).\
**Outcome:** Explain how the browser carries a SAML login exchange, why the portal accepts the authentication result, and how the portal creates its own session.

> **Draft for review.** This is the narrative-first pilot with the accepted bearer explanation and relocated cookie details. All Foundations prerequisites are available; FND-003 remains Draft pending its review.

## Maya opens the employee portal

Maya works at Acme. She opens the employee portal to read her reports:

```text
https://portal.example.com/reports
```

She signed in to her Acme account earlier today, but she has not signed in to this portal. As far as the portal can tell, this browser has no authenticated session.

A **session** is how an application remembers a signed-in user across requests. In our example, the server keeps a session record and gives the browser a cookie containing an opaque identifier. On later requests, that cookie lets the server find the record.

Maya already has a session with Acme's central sign-in system, its **identity provider**, or **IdP**. The portal has an agreement with that IdP: it will accept authentication statements from it, provided those statements pass the portal's checks.

The portal cannot yet assume the visitor is Maya. It sends the browser to the IdP to obtain an authentication result. The IdP recognizes Maya through her existing session and returns a signed statement. The browser carries that statement back. The portal checks it, finds Maya's local account, and establishes its own session.

That is the job **SAML**, the Security Assertion Markup Language, performs in this login: it gives the systems a standard way to request and communicate an authentication result.

The portal is called the **service provider**, or **SP**. Because the portal starts the exchange, this is **SP-initiated login**. Maya's browser carries the messages between the SP and IdP. [OASIS technical overview, section 5.1](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0.html)

## The portal starts a login and remembers why

When Maya requests `/reports`, the portal first looks for its own authenticated session. There is none.

Before sending her elsewhere, it records a pending login. Acme's portal gives this attempt the identifier `_req_701` and remembers the requested page, `/reports`.

This matters because a response arriving later must belong to the login that is actually in progress. The portal also needs to associate the returning response with the browser interaction that started this login. In Acme's implementation, a short-lived cookie helps maintain that association.

This cookie does not mean Maya is authenticated. It only helps the portal recognize the pending login when the browser returns.

The portal then responds with a redirect. The browser follows it to Acme's IdP, carrying the authentication request.

## The IdP recognizes Maya and prepares an answer

When the browser reaches the IdP, it sends the IdP's eligible session cookie. That is a different cookie from anything the portal created.

The IdP checks its session record and recognizes Maya. It also checks the request and whether its policy permits this authentication result to be used for the portal.

In this scenario, her existing session is sufficient. She does not need to enter her password again.

The IdP prepares a successful SAML response containing an **assertion**, a structured statement about Maya's authentication. It identifies the employee and restricts where and when the statement can be accepted.

The IdP signs the assertion. The portal will use an already-trusted public key to check that signature when the response arrives.

But the IdP does not make a direct network call to the portal here. It returns a page containing a form to Maya's browser. The browser submits that form to the portal, carrying the response.

## The portal checks the answer and establishes its own session

The portal now has authentication material delivered by the browser. It cannot accept that material merely because it looks like a successful response.

It checks the trusted signature, intended application, destination, timing, and relationship to the pending login. It also checks that the assertion has not already been used.

In our working example, those checks pass. The asserted identity maps to Maya's existing, active portal account, which is permitted to use the portal.

The portal creates a fresh authenticated session, gives the browser its portal session cookie, and sends it back to `/reports`. On that request, the portal checks both the session and Maya's permission to read reports before returning the page.

That completes the login. The sequence looks like this:

```mermaid
sequenceDiagram
    actor B as Maya's browser
    participant SP as Employee portal
    participant IDP as Acme identity provider

    B->>SP: GET /reports
    Note over SP: No portal session; store pending login
    SP-->>B: 302 redirect with SAMLRequest and RelayState
    B->>IDP: GET /sso with request and IdP cookie
    Note over IDP: Check request and existing IdP session
    Note over IDP: Issue signed assertion for the portal
    IDP-->>B: HTML form containing SAMLResponse
    B->>SP: POST /saml/acs with response and RelayState
    Note over SP: Validate response and exact signed assertion
    Note over SP: Match account and establish portal session
    SP-->>B: Set portal cookie; 303 redirect to /reports
    B->>SP: GET /reports with portal cookie
    Note over SP: Check session and report permission
    SP-->>B: 200 report page
```

Every network arrow connects the browser to a server. The notes show internal work. Browser tools can show the redirect and form POST, but they cannot show the portal performing signature validation or looking up Maya's account.

## How the systems know where to send things

For that exchange to work, the teams must agree on identities, addresses, and trust before Maya arrives.

The portal needs a name the IdP can recognize. Its **entity ID** is `https://portal.example.com/saml`. Although it looks like a web address, its purpose here is identification. The browser does not visit it during this exchange.

The IdP also needs an approved place to return its answer. The portal supplies `https://portal.example.com/saml/acs`, its **Assertion Consumer Service**, or **ACS**, endpoint.

In the other direction, the portal needs the IdP's SSO endpoint, where it sends authentication requests, and the IdP's entity ID, which identifies the expected issuer.

Finally, the portal needs trusted signing material. Acme's IdP keeps a private signing key. The portal receives an approved certificate containing the corresponding public key.

SAML **metadata** can package participant identifiers, endpoints, bindings, and keys. The teams establish trust in that configuration during onboarding. A certificate supplied inside an unexpected response does not make itself trustworthy. [OASIS SAML metadata specification, sections 2.3-2.4](https://docs.oasis-open.org/security/saml/v2.0/saml-metadata-2.0-os.pdf)

Here is the agreed configuration for reference:

| Setting | Acme example |
|---|---|
| Portal entity ID | `https://portal.example.com/saml` |
| Portal ACS endpoint | `https://portal.example.com/saml/acs` |
| IdP entity ID | `https://idp.example.net/saml` |
| IdP SSO endpoint | `https://idp.example.net/sso` |
| Trusted signing material | Acme's approved IdP signing certificate |
| Account matching | Agreed persistent NameID mapped to an existing portal account |

## What the browser actually carries

The message names now have a place in the story.

The portal's question is an `AuthnRequest`. The IdP's answer is a `Response` containing an `Assertion`.

A **binding** specifies how those messages travel. Acme uses HTTP Redirect for the request and HTTP POST for the response. The browser SSO **profile** combines the relevant rules for this use.

All excerpts below are fictional and incomplete. They illustrate the exchange; they cannot be submitted to a real endpoint.

The redirect from the portal looks like this:

```http
HTTP/1.1 302 Found
Location: https://idp.example.net/sso?SAMLRequest=ENCODED_REQUEST&RelayState=OPAQUE_HANDLE
```

The browser follows the `Location` address. `SAMLRequest` contains the XML request, compressed using DEFLATE, Base64-encoded, and URL-encoded.

Acme uses `RelayState` as an unpredictable handle to its stored login context, including the approved return path. It does not accept an arbitrary return URL from the browser. The request ID and returned `InResponseTo` values provide protocol-level request correlation; RelayState does not replace those checks.

Before encoding, the request contains fields like these:

```xml
<samlp:AuthnRequest
    xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol"
    xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion"
    ID="_req_701"
    Version="2.0"
    IssueInstant="2026-09-17T18:00:00Z"
    Destination="https://idp.example.net/sso"
    AssertionConsumerServiceURL="https://portal.example.com/saml/acs"
    ProtocolBinding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST">
  <saml:Issuer>https://portal.example.com/saml</saml:Issuer>
</samlp:AuthnRequest>
```

You can now connect the fields to decisions already explained: `ID` names the request, `Issuer` identifies the portal, `Destination` names the receiving endpoint, and the ACS and binding fields describe the requested response delivery. Maya's password is absent. [OASIS SAML Core, section 3.4](https://docs.oasis-open.org/security/saml/v2.0/saml-core-2.0-os.pdf)

This fictional integration permits unsigned authentication requests. The IdP still checks the requested ACS against the portal's registered configuration.

On the return journey, the IdP supplies an HTML form containing a Base64-encoded response. The browser submits:

```http
POST /saml/acs HTTP/1.1
Host: portal.example.com
Content-Type: application/x-www-form-urlencoded

SAMLResponse=ENCODED_RESPONSE&RelayState=OPAQUE_HANDLE
```

Acme's implementation uses a separate, short-lived correlation cookie for this return. Because it is a cross-site form POST, Acme chooses `SameSite=None; Secure; HttpOnly` for that cookie. `SameSite=None` permits cross-site delivery, subject to browser policy; `Secure` restricts delivery to HTTPS; `HttpOnly` prevents ordinary page JavaScript from reading it.

These are application choices, not a session design prescribed by SAML. The temporary cookie is not an authenticated portal session. [OWASP session management guidance](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html)

This is a **bearer assertion**: the presenter does not have to prove possession of a separate cryptographic key. Someone who steals it could therefore try to use it. The portal must check its intended recipient, validity window, relationship to the pending login, and whether it has already been used before accepting it. [OASIS SAML Profiles, sections 3.3 and 4.1.4](https://docs.oasis-open.org/security/saml/v2.0/saml-profiles-2.0-os.pdf)

That makes the assertion sensitive authentication material. Base64 encoding does not make it secret; HTTPS protects its network transport. The browser applies form encoding when submitting the Base64 response value. [OASIS SAML Bindings, sections 3.4-3.5](https://docs.oasis-open.org/security/saml/v2.0/saml-bindings-2.0-os.pdf)

## Why the portal accepts this particular answer

Imagine the response arrives at `18:00:20Z` on September 17, 2026.

First, the portal needs a successful authentication result. The response reports success, so processing can continue. A success label alone does not establish trust.

Next, the portal needs confidence in the assertion's origin and integrity. It checks the issuer and verifies the signature using its trusted key. The library must validate the exact assertion from which the application reads the identity.

A failed signature check means that trust has not been established. Modification is one possible cause; a wrong trusted key or rollover problem can also cause failure. Use a maintained SAML library rather than implementing XML signature handling yourself. [OWASP SAML security guidance](https://cheatsheetseries.owasp.org/cheatsheets/SAML_Security_Cheat_Sheet.html)

The portal then asks whether the assertion is intended for it. The assertion's **audience** names the portal entity ID. Its delivery restrictions identify the ACS.

It also needs the answer to belong to this pending login. The response and bearer confirmation refer to `_req_701`; the application checks the browser association and RelayState too.

Finally, the assertion must still be usable and must not have been consumed already. Our example gives it a short validity window and a unique assertion ID.

These fictional values summarize the successful checks:

| Check | Expected value or result |
|---|---|
| Status | Success |
| Issuer and signature | Approved IdP; valid signature under its trusted key |
| Audience | `https://portal.example.com/saml` |
| Response destination and bearer recipient | `https://portal.example.com/saml/acs` |
| Response and bearer `InResponseTo` | `_req_701` |
| Conditions validity | `18:00:00Z` up to, but excluding, `18:05:00Z` |
| Bearer confirmation expiry | `18:05:00Z` |
| Replay check | Assertion `_assert_901` has not been consumed |

The selected POST browser SSO profile requires signed assertions and replay prevention. These restrictions explain why a valid signature alone is insufficient. This table introduces the principal checks; it is not a complete validator implementation checklist. [OASIS SAML Profiles, sections 4.1.4.2-4.1.4.5](https://docs.oasis-open.org/security/saml/v2.0/saml-profiles-2.0-os.pdf)

The assertion identifies its subject using the agreed persistent NameID, `acme-user-1042`, and includes an authentication statement. The subject is the identity the assertion describes. [OASIS SAML Core, sections 2.3-2.7](https://docs.oasis-open.org/security/saml/v2.0/saml-core-2.0-os.pdf)

Acme maps that identity, within the approved IdP relationship, to Maya's local account. The portal establishes the fresh session and consumes the pending login:

```http
HTTP/1.1 303 See Other
Location: /reports
Set-Cookie: portal_session=FICTIONAL_OPAQUE_VALUE; Path=/; Secure; HttpOnly; SameSite=Lax
```

The browser follows the redirect with its new portal cookie. Authentication has identified Maya; the portal's authorization decision determines whether she may read the report.

## What made this single sign-on?

Maya did not type her password again when she opened the portal. Her existing IdP session satisfied this request, allowing the IdP to issue the authentication result the portal needed.

She now has two separate sessions. The IdP recognizes its cookie; the portal recognizes its own. When Maya requests another report, the portal uses its session rather than asking the browser to submit the assertion again.

Another request might require fresh authentication under IdP policy. SSO does not guarantee that every future application visit will avoid a prompt. [OASIS technical overview, section 5.1](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0.html)

## Where this appears in Okta

If Acme's IdP is Okta, the application configuration expresses the same agreement.

Okta's **Single sign-on URL** field identifies the portal's ACS. **Audience URI (SP Entity ID)** identifies the intended application. **Name ID format** and **Application username** help specify the subject identifier supplied to it.

Notice the direction: that Single sign-on URL is the portal's receiving endpoint. It is different from the Okta-side endpoint where the portal sends its request. [Okta SAML field reference](https://help.okta.com/en-us/content/topics/apps/aiw-saml-reference.htm)

## Predict the result

Keep every detail of Maya's successful exchange, except the assertion's audience is now:

```text
https://expenses.example.com/saml
```

The assertion has a valid signature from Acme's trusted IdP. Its timestamps, recipient, and request correlation are correct.

**Should the employee portal establish a session? What would confirm the cause of rejection?**

### Worked answer

No. The assertion names the expenses application as its audience, not the employee portal.

The signature shows that the signed content verifies under the trusted key. It does not change the intended audience. Accepting the assertion would discard a required restriction.

A confirmed diagnosis needs the audience-validation result from the portal, the expected SP entity ID in its configuration, and the relevant audience value from the received assertion. A browser-visible failure alone does not prove an audience mismatch.

The likely configuration problem is the IdP application's audience value or the selection of the wrong application integration. Compare both sides before changing either.

After correcting the configuration, start a fresh login. Confirm the new assertion has the portal's audience, validation succeeds, and the portal creates the expected session. Retain a negative check showing that an assertion for the expenses application is rejected.

## Verification note

Protocol references were checked on September 17, 2026 against the cited OASIS specifications, with Okta documentation for product labels and OWASP for implementation guidance. The reviewed text was integrated into this repository on September 18, 2026.

The fictional times, identifiers, and destinations are internally consistent. The excerpts omit a complete signed response and cryptographic material, so they are not executable or cryptographically verified artifacts. GitHub rendering of the Mermaid diagram still requires verification before this draft is marked Ready.

[Part 2](README.md) | [Table of contents](../TABLE-OF-CONTENTS.md)\
**Previous in Core order:** FND-003 (Planned). **Next:** SAML-002 (Planned).
