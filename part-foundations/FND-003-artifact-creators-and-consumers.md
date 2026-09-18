# Who creates each artifact, and who consumes it?

**ID:** FND-003\
**Depth:** Core\
**Prerequisites:** [FND-001](FND-001-login-access-and-account-lifecycle.md), [FND-002](FND-002-following-the-browser-and-its-sessions.md).\
**Outcome:** Identify an artifact's issuer, carrier, intended consumer, and purpose, and explain why another credential cannot automatically replace it.

> **Draft for review.** The examples are fictional role descriptions, not executable messages or instructions for building a validator. Here, artifact means a message or value used in an exchange. It does not mean the specific SAML artifact-binding mechanism taught later.

## The browser carries it, but who said it?

Maya has reached her reports page. The portal accepted the identity provider's authentication result, matched her account, and established a session. Her next request carries the portal cookie, and the portal returns her permitted report.

Now imagine a new engineer reviewing that successful journey. They see two values arriving from the same browser: the authentication result in the returning form, then the portal cookie on the reports request. They label both values "Maya's login token."

That description hides the decisions the portal made.

The identity provider issued the authentication result. The browser carried it. The portal consumed it by checking it and using the accepted result to resolve an account. Later, the portal issued a session cookie, and the browser returned it so the portal could recognize its own session.

The carrier is the same, but the origin and purpose have changed. Receiving something from Maya's browser does not mean Maya authored it, and it does not establish who the portal should trust.

Use four questions when a new value appears: who issued it, who carried it, who is supposed to consume it, and what decision does it support? A **consumer** is the component that interprets or validates a value for its intended use. A component that merely transports it is not necessarily that consumer.

## The assertion and the session belong to different decisions

In the selected SAML login, the identity provider creates a **SAML assertion**, a structured statement about a subject. The assertion can describe authentication and carry attributes, with conditions limiting its use. The surrounding SAML response delivers the protocol result. The portal acts as the **service provider**, or SP, relying on the assertion after the required checks. [SAML Core, sections 2 and 3.4](https://docs.oasis-open.org/security/saml/v2.0/saml-core-2.0-os.pdf)

For Acme, the assertion supports the decision to accept an authentication result for this portal login. It does not by itself create Maya's local account or grant payroll administration. Those remain separate application decisions from FND-001.

After accepting the login, the portal establishes its own session. In our chosen design, the cookie contains a handle for that server-side session. The browser returns the cookie on eligible requests, as FND-002 showed. Cookies are an HTTP mechanism, not a type of SAML assertion. [RFC 6265, sections 3 and 4](https://www.rfc-editor.org/rfc/rfc6265.html)

Consequently, the portal does not need the browser to resubmit the original assertion with every report request. The session has its own lifetime and checks. This server-side session design is Acme's implementation choice; the assertion and cookie are not two names for the same object.

## When the portal needs information from another service

Suppose Acme adds a separate business API that supplies report data. An **API**, or application programming interface, lets software request operations or data from another component. Here the portal backend makes that request to the business API.

Maya's portal login still answers the portal's login question. The API has a different question: may this caller use this operation? We will use OAuth 2.0 for that separate access arrangement. This is an extension of the scenario, not an extra step required for every SAML login.

OAuth names the application seeking access the **client**, the protected API the **resource server**, and the token-issuing service the **authorization server**. Maya is the **resource owner** in this delegated example. These are roles; one product may implement more than one. [RFC 6749, section 1.1](https://www.rfc-editor.org/rfc/rfc6749.html#section-1.1)

An **access token** is the credential the client presents for protected-resource access. For an API using bearer tokens, possession of the token supplies the credential; the receiver must still validate it and enforce the applicable permissions. Acme's API receives the access token intended for it, then decides whether the requested report is permitted. A portal cookie does not acquire that role just because it already works at the portal. [RFC 6750, sections 1.2 and 2](https://www.rfc-editor.org/rfc/rfc6750.html)

## A code is an intermediate value

Before the portal has an access token, it may receive an **authorization code** through Maya's browser. In the authorization-code flow, the authorization server issues the code, and the client submits it to that server's token endpoint to obtain tokens. The code is short-lived and single-use; it is not the credential to send to the reports API. [RFC 6749, sections 1.3.1 and 4.1.2](https://www.rfc-editor.org/rfc/rfc6749.html#section-4.1.2)

For our backend example, receiving the code and exchanging it are different events. The browser carries the code to the portal. The portal backend then makes a direct request to the authorization server. This uses the front-channel and back-channel distinction you already know.

That description identifies the artifacts, not a complete implementation. Request binding, client checks, and proof key for code exchange (PKCE) protect the transaction. PKCE ties redemption to proof associated with the original request. OAUTH-002 will explain that proof before showing the full exchange. Never reduce the implementation to "accept any code and call it a login." Current OAuth security guidance strengthens the original framework. [RFC 9700, section 2.1](https://www.rfc-editor.org/rfc/rfc9700.html#section-2.1)

The authorization server may also issue a **refresh token**. The client uses it with that server to request new access tokens, subject to policy. It is optional and is not sent to the business API. [RFC 6749, section 1.5](https://www.rfc-editor.org/rfc/rfc6749.html#section-1.5)

## An authentication result for an OIDC application

Consider a clearly separate deployment: Acme chooses OpenID Connect, or **OIDC**, for the portal's login instead of SAML. OIDC adds an authentication layer to OAuth 2.0. Its **ID token** conveys claims about the user's authentication to the client. A claim is a named statement, such as an identifier or an authentication time. The issuer is the **OpenID Provider**, and the client relying on that result is the **Relying Party**. [OpenID Connect Core, sections 1 and 2](https://openid.net/specs/openid-connect-core-1_0.html#IDToken)

In this alternative, the portal validates its ID token, resolves the local account, and establishes its session. If it also calls the business API, it uses the appropriate access token there. An ID token addressed to the portal is not a substitute for the API's access credential.

OAuth alone does not define this application-login result. Seeing that an OAuth interaction involved Maya does not remove the need for a defined authentication protocol and its checks. OIDC provides that layer; it is not a second login exchange that must be added after SAML. [OpenID Connect Core, section 1](https://openid.net/specs/openid-connect-core-1_0.html#Introduction)

## Put the intended consumers beside the values

This table collects the roles just introduced. It is a comparison across the examples, not a sequence in which every row must occur.

| Value | Issued by | Carried or presented by in our examples | Intended consumer and use |
|---|---|---|---|
| SAML assertion | Acme IdP | Browser, inside the returning response | Portal SP, to evaluate the authentication statement |
| Authorization code | Authorization server | Browser to portal, then portal backend to token endpoint | Authorization server, for code redemption |
| Access token | Authorization server | Portal backend on the API request | Business API, for protected-resource access |
| Refresh token, if issued | Authorization server | Portal backend on a renewal request | Authorization server, for token renewal |
| ID token in the alternative OIDC deployment | OpenID Provider | Returned to the portal backend in the selected code flow | Portal Relying Party, to validate the authentication result |
| Portal session cookie | Portal | Browser on eligible portal requests | Portal, to resolve its session |

The portal receives and stores some values that another server ultimately consumes. For example, it receives the refresh token but presents it back to the authorization server. "Who received it first?" is therefore less useful than "Who is supposed to act on it?"

## Appearance does not establish purpose

Two values can look similar while serving different consumers. **JSON Web Token**, or **JWT**, names a format for representing claims, not a universal permission to log in or call an API. An OIDC ID token uses JWT. An access token need not have that format. [RFC 7519, sections 1 and 3](https://www.rfc-editor.org/rfc/rfc7519.html) [OpenID Connect Core, section 2](https://openid.net/specs/openid-connect-core-1_0.html#IDToken)

You may also hear a value called **opaque**: the component holding it should treat its contents as uninterpreted data rather than derive meaning from its characters. The fictional portal session handle is an example from the browser's perspective.

Even when a value is readable, reading is not validation. Finding a name inside it does not establish its issuer, intended consumer, current validity, or suitability for the operation. The protocol lessons will introduce those checks where the receiver needs them. Use maintained protocol libraries for their implementation.

## Investigate the wrong value

In the alternative OIDC deployment, Maya can read the portal landing page, but its request for report data fails. Someone proposes retrying the API call with the ID token because "that one proves Maya signed in."

The following are fictional, sanitized observations, not live credentials:

| Observation | Evidence available |
|---|---|
| Portal session lookup | Active session for Maya's local account |
| Outgoing API request | Portal selected the saved ID-token field as its credential |
| API contract | Requires an access token intended for the business API |
| API validation log | Rejected credential under the API's acceptance policy |

What cause is supported, what should change, and how would you verify the correction?

### Worked reasoning

The active portal session establishes that the portal recognizes this interaction. It does not establish that the API request carries the right credential. The recorded field selection and API contract identify a concrete mistake: the portal selected its authentication result for an API access request.

Correct the portal's selection and confirm that its authorization arrangement actually supplies an access token for this API. If it does not, repair that arrangement rather than relabeling the ID token. Keep the API's intended-consumer and permission checks in place.

Repeat the request with the correctly obtained access token and verify that Maya's permitted report is returned. Then verify that the API still rejects the ID token and denies a report outside Maya's permissions. A generic failure response without the supplied observations would not, on its own, identify this cause. Expiry, a token for another API, and insufficient permission are different possibilities that later lessons will distinguish.

## Before the first full protocol exchange

In the SAML deployment, the authentication result and portal cookie now have separate owners and purposes. You can follow both through the browser without confusing their carrier with their issuer. That is enough background to open the first complete SAML login and ask what the portal must check before accepting it.

The OAuth and OIDC comparisons above introduce vocabulary, not extra prerequisites to study before SAML. Their complete exchanges follow in Parts 3 and 4.

## Verification note

The cited OASIS, IETF, and OpenID Foundation sources were checked on 2026-09-18. RFC 6749 supplies the framework terminology; RFC 9700 supplies the current OAuth security baseline. The fictional deployment choices illustrate roles and do not specify a complete protocol implementation. No cryptographically verifiable artifact is included.

[Previous: FND-002](FND-002-following-the-browser-and-its-sessions.md) | [Part 1 and readiness review](README.md) | [Table of contents](../TABLE-OF-CONTENTS.md)\
[Next: SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md)
