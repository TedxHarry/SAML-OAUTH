# Error and symptom catalog

This reference supports worked troubleshooting lessons. A message or error code is evidence, not a diagnosis. Entries distinguish standardized errors, validation failures, provider-specific text, and observed symptoms. The quoted application messages below are fictional.

## SAML

### Assertion audience does not match the portal

- **Classification:** Validation failure, not a universal wire error string.
- **Protocol and stage:** SAML, SP assertion acceptance.
- **Standard error code:** None asserted by this example. A Response with a successful SAML status can still fail the SP's audience validation.
- **Observed symptom:** The portal refuses to establish a session after receiving the response.
- **Possible causes:** Wrong IdP application selected, incorrect audience configuration, or incorrect expected SP entity ID.
- **Distinguishing evidence:** Received assertion audience, configured SP entity ID, and the portal's audience-validation result.
- **Next check:** Compare both sides of the integration contract before changing either.
- **Not established:** A generic browser failure does not establish audience mismatch. A valid signature alone does not establish intended audience.
- **Worked lesson:** [SAML-001 exercise](../part-saml/SAML-001-first-sp-initiated-login.md#predict-the-result).
- **Source:** [OASIS SAML Profiles, section 4.1.4](https://docs.oasis-open.org/security/saml/v2.0/saml-profiles-2.0-os.pdf), checked during pilot review on 2026-09-17.

## Application identity and permission

### No matching local account

- **Classification:** Fictional application symptom, not a standardized protocol error.
- **Stage:** Local account resolution after the portal reports accepting the authentication result.
- **Standard error code:** Not applicable to this example.
- **Possible causes:** Account absent, incorrect mapping contract, or mismatched stored mapping value.
- **Distinguishing evidence:** Portal acceptance event, received identity, expected mapping, and local records.
- **Next check:** Compare those records before creating an account or resetting a password.
- **Not established:** IdP sign-in success alone does not prove portal validation succeeded.
- **Worked lesson:** [FND-001 exercise](../part-foundations/FND-001-login-access-and-account-lifecycle.md#predict-the-next-useful-check).
- **Source basis:** The lesson's explicitly fictional application policy and supplied observations.

### Report denied after successful account lookup

- **Classification:** Fictional application authorization outcome.
- **Stage:** The portal evaluates the requested report against its own-report policy.
- **Standard error code:** No universal code asserted.
- **Possible causes:** Correct denial for another employee's report; incorrect ownership or permission data if access was intended.
- **Distinguishing evidence:** Requested operation, resolved account, report owner, and policy result.
- **Next check:** Establish whether access should be allowed before modifying policy.
- **Not established:** A denial does not by itself prove a broken SSO integration.
- **Worked lesson:** [FND-001 variations](../part-foundations/FND-001-login-access-and-account-lifecycle.md#when-the-same-journey-stops-at-a-different-point).
- **Source basis:** The lesson's explicitly fictional application policy.

## OAuth and OpenID Connect

Entries will be added from their worked investigations. Keep standardized codes separate from provider messages and visible symptoms.

## Token lifecycle and browser behavior

### Browser returns to sign-in after posting the authentication result

- **Classification:** Observed redirect-loop symptom, not a standard protocol error.
- **Stage:** Browser return and subsequent portal-session use.
- **Standard error code:** None established by the trace.
- **Possible causes:** Rejected authentication result, absent or ineligible cookie, missing session creation, or failed server-side session lookup.
- **Distinguishing evidence:** Whether the response set a cookie, whether the next eligible request sent it, and the portal's validation/session events.
- **Next check:** Follow the cookie across response and request, then correlate the relevant portal decisions.
- **Not established:** The redirect alone does not prove a signature failure; a cookie header alone does not prove a live server session.
- **Worked lesson:** [FND-002 exercise](../part-foundations/FND-002-following-the-browser-and-its-sessions.md#predict-the-next-check). Later SAML-008 and ARCH-002 add deeper investigations.
- **Sources:** [RFC 6265](https://www.rfc-editor.org/rfc/rfc6265.html), [OWASP session management](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html); checked 2026-09-18. The diagnostic scenario is fictional.

Further entries will be added from the token and architecture investigations.

## Entry structure

Every new entry records classification, protocol and stage, standard code if applicable, symptom, possible causes, distinguishing evidence, next check, what the evidence does not establish, worked lesson, source, and verification date where relevant.

Use fictional or safely redacted evidence. Never include reusable credentials, assertions, tokens, or session cookies.

[Table of contents](../TABLE-OF-CONTENTS.md)
