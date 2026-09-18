# Login, access, and account lifecycle

**ID:** FND-001\
**Depth:** Core\
**Prerequisites:** Existing IT fundamentals; no earlier course lesson.\
**Outcome:** Distinguish establishing identity, granting access, and maintaining accounts, then identify which decision needs investigation when access fails.

> **Draft for review.** All people, account records, and diagnostic observations in this lesson are fictional.

## Maya wants to read her report

Maya works at Acme. She opens the employee portal to read her monthly report.

In the intended working setup, Acme has an active employee account for her. The portal has a corresponding local account, and that account may read Maya's reports. Those arrangements were established before she opened the page.

The portal sends her through Acme's central sign-in service. That service establishes which account she is using and returns an authentication result the portal can check. The portal accepts the result, finds Maya's local account, and remembers the signed-in interaction. It then checks her permission to read the requested report and displays it.

From Maya's perspective, she signed in and got her report. From the application's perspective, several different decisions succeeded. Understanding those decisions will make a failed login much easier to investigate.

## First, establish which account is being used

The central sign-in service needs evidence that the person interacting with it can authenticate as Maya's account. That might involve a password, another authenticator, or an existing usable sign-in session under the service's policy. The precise method is not important to this example yet.

This is **authentication**: establishing the account identity for the interaction using the required evidence. It does not by itself say which reports that account may read.

Acme's central service is an **identity provider**, often shortened to **IdP**. The portal is configured to accept authentication results from it after performing the required checks. The portal does not ask Maya to give it her Acme password in this arrangement.

That trust arrangement is **federation**. An application can rely on an identity provider's verified authentication result rather than directly checking the user's authenticator itself. The detailed messages and checks arrive in the SAML and OIDC parts of the course. [NIST SP 800-63C-4, Introduction](https://pages.nist.gov/800-63-4/sp800-63c.html#introduction)

For now, keep the distinction clear: the identity provider establishes the identity, and the portal must correctly process the result. Seeing a successful sign-in screen at the identity provider does not prove the portal completed its own work.

## Next, find the portal account

Acme's identity provider and employee portal are separate systems. In this example, the portal has its own account record for Maya. The authentication result must be associated with that record using the agreed identity mapping.

Think about what the portal needs to know locally. Is this account active? Which employee does it represent? Which application permissions does it have? Those facts need an owner and an update process.

**Provisioning** is the creation and maintenance of the account and access-related data an application needs. It can include creating an account, updating its attributes, changing membership, or disabling it when access should end. A deployment may automate those operations or manage some of them administratively.

In Acme's example, the approved onboarding process has already created Maya's account and mapping. We are not assuming that every SSO login creates an account. Some applications can create a local account during a first successful login, but that is an additional configured behavior, not a substitute for planning the entire account lifecycle.

**SCIM**, the System for Cross-domain Identity Management protocol, is one way systems exchange identity-management operations. Its user-management purpose is separate from a browser login exchange. [RFC 7644, section 1](https://www.rfc-editor.org/rfc/rfc7644.html#section-1)

## Then, decide whether this report is allowed

The portal has identified Maya and found her active account. Now it examines the requested report.

Acme's policy says employees may read their own monthly reports. Maya owns the requested report, so the portal permits the operation. This decision is **authorization**: deciding whether a caller may perform a particular action on a particular resource.

Here is the relevant fictional application record after the successful setup:

| Fact | Maya's working example | Why the portal needs it |
|---|---|---|
| External identity mapping | Approved Acme identity maps to Maya's local account | Connect the authentication result to the correct account |
| Local account status | Active | Determine whether the account may use the portal |
| Requested action | Read a monthly report | Identify the operation being evaluated |
| Report owner | Maya | Apply the own-report access rule |
| Result | Allow | Return this report |

If Maya requests another employee's restricted report, the same authentication can still be valid while authorization denies that operation. Repeating sign-in does not change the report's owner or the access rule.

The policy in this example is Acme's application policy. It is not a universal permission model imposed by a federation protocol.

## Why Maya does not sign in for every page

After the portal establishes the authenticated interaction, it maintains a **session**. That lets it recognize subsequent requests without repeating the full sign-in process on every page. FND-002 will explain the browser cookie and server-side record involved.

The portal's session is separate from any session at the identity provider.

If Maya already has a usable identity-provider session, the provider may satisfy another application's authentication request without asking her to authenticate interactively again. That experience is **single sign-on**, or **SSO**. Whether another prompt is needed depends on the request and applicable policy. [NIST SP 800-63C-4, Introduction](https://pages.nist.gov/800-63-4/sp800-63c.html#introduction)

Neither federation nor SSO means that every application shares one session record or one permission policy.

## When the same journey stops at a different point

Now vary the working example. These observations are deliberately simplified evidence, not real provider log messages.

**Variation one: no local account can be found.** The portal's internal record says it accepted the authentication result, but its lookup found no matching local account. Maya cannot reach the reports page.

Authentication has succeeded according to the supplied portal evidence. Account mapping has not. Possible explanations include an account that was never created or a mismatch between the expected external identity and the stored mapping. The next useful check compares the approved mapping contract, the identity received, and the actual local account record.

Do not create a duplicate account before checking whether the correct one already exists under a different mapping.

**Variation two: the account exists, but the report is denied.** The portal confirms a successful account lookup and identifies the requested report as belonging to someone else. Its own-report rule denies access.

The supplied evidence supports an authorization explanation. Changing Maya's password would not correct that decision. First determine whether the requested operation should be permitted at all. A correct denial is not an integration defect.

Notice how the next check changes with the failed decision. "Maya cannot access reports" is a symptom. It is not yet a diagnosis.

## When Maya changes roles or leaves Acme

The same distinctions matter after onboarding. A role change may require updated permissions. Leaving the company may require account disablement and action on existing sessions or credentials.

Do not assume that changing one account record immediately updates every relying application or ends every existing session. Record which system performs each action and how downstream enforcement is confirmed. The later lifecycle lessons examine those boundaries in detail. [NIST SP 800-63C-4, general federation requirements](https://pages.nist.gov/800-63-4/sp800-63c.html)

## Where the protocol names fit

The course follows these responsibilities rather than treating all identity technology as a single login mechanism:

| Technology | Place in the picture |
|---|---|
| SAML | Carries structured security statements; the course first uses it for federated browser login |
| OpenID Connect | Adds an authentication layer to OAuth 2.0 so an application can obtain an authentication result |
| OAuth 2.0 | Lets a client obtain limited access to a protected resource; it does not alone define application login |
| SCIM | Supports identity-resource management, such as creating or updating user records |
| LDAP | A protocol for accessing directory services; its presence behind a system does not make it the browser federation exchange |
| Kerberos | A ticket-based network authentication protocol, distinct from the SAML and OIDC browser exchanges taught here |

This is orientation, not a requirement to memorize every protocol. A portal can use one mechanism for login and another to access an API. A provisioning process can maintain the account independently of either.

Sources: [SAML technical overview](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0.html), [OIDC Core, Introduction](https://openid.net/specs/openid-connect-core-1_0.html#Introduction), [RFC 6749, Introduction](https://www.rfc-editor.org/rfc/rfc6749.html#section-1), [RFC 7644](https://www.rfc-editor.org/rfc/rfc7644.html), [RFC 4511](https://www.rfc-editor.org/rfc/rfc4511.html), and [RFC 4120](https://www.rfc-editor.org/rfc/rfc4120.html).

## Applying the distinction in an Okta environment

In an Okta-centered deployment, start with the same three questions: what establishes the identity, what maintains the application's account, and what grants the requested access?

Do not infer the answer to all three from a successful Okta sign-in. Account linking and account creation are configuration concerns of their own. [Okta: External Identity Providers](https://developer.okta.com/docs/concepts/identity-providers/)

Okta Workflows belongs alongside this picture as an automation tool that may orchestrate identity-related actions and API calls. [Okta Workflows use cases](https://help.okta.com/wf/en-us/content/topics/workflows/use-cases-workflows-learn-about.htm)

This course will explain the protocol boundaries those operations depend on. It does not teach complete Workflows implementations or SCIM integrations.

## Predict the next useful check

Maya reports that she cannot open the portal. You receive these fictional observations:

1. The identity provider reports successful authentication.
2. The portal reports that it accepted the authentication result.
3. The portal reports "no matching local account."

A colleague proposes resetting Maya's password. Explain why that is not yet a supported fix. What should you investigate next, and how would you verify a correction?

### Worked answer

The supplied evidence puts the failure after authentication-result acceptance. A password reset does not address the observed local lookup failure.

Compare the identity that the portal received with its configured mapping rule and local account records. Check whether the account exists, whether it was created through the intended process, and whether the mapping values agree. Missing provisioning and an incorrect mapping are competing explanations until that comparison distinguishes them.

After making the supported correction, start a fresh interaction. Confirm that the portal accepts the authentication result, resolves the intended account, and permits Maya's own report. Also confirm that a restricted report remains denied. Successful account mapping should not accidentally broaden her access.

If only the first observation were available, you could not yet claim that the portal accepted the authentication result. You would need evidence from the portal before narrowing the investigation.

## Verification note

Source documents for the introductory distinctions were checked on 2026-09-18. The Acme records, policy, and diagnostic observations are fictional teaching choices. This lesson has no executable protocol artifact and does not claim that one product setting controls every account, session, or permission.

[Part 1](README.md) | [Table of contents](../TABLE-OF-CONTENTS.md)\
**Next:** FND-002, Following the browser and its sessions (Planned).
