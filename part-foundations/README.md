# Part 1: Foundations

**Entry prerequisites:** Existing IT fundamentals.

**Core completion outcome:** Explain why the portal needs an authentication result, how the browser carries it, and why the application session is separate.

Follow the Core entries in order. Optional entries can be skipped. Lesson files are created as they are drafted; Planned titles are intentionally unlinked.

## Understanding the login problem

- **[FND-001 - Login, access, and account lifecycle](FND-001-login-access-and-account-lifecycle.md)** · Core · Ready\
  Distinguish identity, permission, account maintenance, federation, and SSO.

The first module was reviewed on 2026-09-18: its account-mapping and report-permission examples satisfy the single-purpose and prerequisite requirements. FND-001 is Ready.

## Following the exchange

- **[FND-002 - Following the browser and its sessions](FND-002-following-the-browser-and-its-sessions.md)** · Core · Ready\
  Follow redirects, form posts, cookies, and separate server sessions.

- **[FND-003 - Who creates each artifact, and who consumes it?](FND-003-artifact-creators-and-consumers.md)** · Core · Draft\
  Distinguish assertions, codes, tokens, and cookies by purpose and consumer.

## Readiness review

This assessment uses FND-001 through FND-003. It is a reading exercise with fictional evidence; no tenant or live credentials are needed. FND-003 and the completed module remain under review.

### Follow Maya's request

In the selected SAML deployment, Maya opens the portal without a portal session. She already has a usable IdP session. The browser follows a redirect to the IdP, carries a return form to the portal, and then requests her report with a new portal cookie.

1. Identify the authentication, account-matching, and report-permission decisions. Could the first succeed while a later decision fails?
2. Who creates the authentication result, who carries it, and who consumes it? Does the returning form mean the IdP directly called the portal?
3. Explain why the IdP cookie and portal cookie are different. If the portal session is removed, does that necessarily remove the IdP session?
4. The browser receives a redirect to the reports page, then another redirect to the IdP. What two kinds of evidence would distinguish cookie delivery from server-side session handling? Does the redirect prove a signature failure?

### Add an API, then compare a different login deployment

The portal backend now requests data from a separate business API. In a separate, alternative deployment, Acme uses OIDC for the portal login instead of SAML.

5. Match the authorization code, access token, refresh token, and ID token to their intended consumer and purpose. Explain why possessing an active portal session does not, by itself, establish the API request's permission.
6. The OIDC portal sends its ID token to the business API. The API requires an access token intended for it. Explain the correction and give one positive and one negative verification. Would making either token readable establish that it is acceptable?

### Worked reasoning

1. The IdP establishes authentication; the portal accepts the authentication result and resolves the local account; the portal checks permission for the report. An accepted authentication result can still lead to an account-mapping failure or a denied report. Provisioning and permission decisions are not guaranteed by successful login.
2. The IdP creates the result, the browser carries it in a form POST, and the portal consumes it. The browser makes that receiving-endpoint request. Validation inside the portal is internal work, not a network call from the IdP.
3. Each cookie identifies the corresponding server's session in this design. The portal cookie goes to eligible portal requests and the IdP cookie to eligible IdP requests. Removing the portal session alone does not remove the independently held IdP session.
4. Inspect whether the portal offered a cookie and whether the browser returned it on the next eligible request. Separately obtain the portal's validation, session-creation, and session-lookup observations. A redirect is a symptom; it does not name the failed check.
5. The authorization server consumes the code for redemption and the refresh token for renewal. The API consumes the access token for protected-resource access. The OIDC portal consumes its ID token as an authentication result. The portal's own session is a separate relationship and does not bypass the API's credential or permission checks.
6. Obtain and select the access token appropriate for that API while preserving its validation and authorization policy. Verify that Maya's allowed report succeeds and that the ID token is still rejected. Also verify that a disallowed report remains denied. Readable contents alone prove neither trust nor suitability.

If a distinction is unclear, revisit [FND-001](FND-001-login-access-and-account-lifecycle.md) for application decisions, [FND-002](FND-002-following-the-browser-and-its-sessions.md) for delivery and evidence, or [FND-003](FND-003-artifact-creators-and-consumers.md) for artifact purpose. The next protocol lesson will explain the SAML message fields; these questions do not require them.

[Table of contents](../TABLE-OF-CONTENTS.md) | [Course introduction](../README.md)
