# Lesson register
This authoring record reserves filenames, IDs, purpose, and explicit prerequisites. Reading order is maintained in the [table of contents](../TABLE-OF-CONTENTS.md). IDs never change when a lesson moves.
64 entries: 56 Core, 6 Advanced engineering, 2 Specialist reference. FND-001 is Ready; FND-002 and SAML-001 are Draft; the remaining 61 entries are Planned.
| ID | Depth | Prerequisites | Status | Reserved path |
|---|---|---|---|---|
| FND-001 | Core | IT fundamentals | Ready | `part-foundations/FND-001-login-access-and-account-lifecycle.md` |
| FND-002 | Core | FND-001 | Draft | `part-foundations/FND-002-following-the-browser-and-its-sessions.md` |
| FND-003 | Core | FND-001, FND-002 | Planned | `part-foundations/FND-003-artifact-creators-and-consumers.md` |
| SAML-001 | Core | FND-001, FND-002, FND-003 | Draft | `part-saml/SAML-001-first-sp-initiated-login.md` |
| SAML-002 | Core | SAML-001 | Planned | `part-saml/SAML-002-reading-and-validating-the-assertion.md` |
| SAML-003 | Core | SAML-002 | Planned | `part-saml/SAML-003-integration-contract.md` |
| SAML-004 | Core | SAML-001, SAML-002, SAML-003 | Planned | `part-saml/SAML-004-sessions-and-logout.md` |
| SAML-005 | Core | SAML-002, SAML-003, SAML-004 | Planned | `part-saml/SAML-005-application-and-idp-initiated-login.md` |
| SAML-006 | Core | SAML-003 | Planned | `part-saml/SAML-006-certificate-and-configuration-changes.md` |
| SAML-007 | Core | SAML-002, SAML-003, SAML-005, SAML-006 | Planned | `part-saml/SAML-007-investigating-rejected-responses.md` |
| SAML-008 | Core | SAML-003, SAML-004, SAML-007 | Planned | `part-saml/SAML-008-investigating-access-and-session-failures.md` |
| SAML-009 | Advanced engineering | SAML-003, SAML-005, SAML-008 | Planned | `part-saml/SAML-009-multiple-identity-providers.md` |
| SAML-010 | Specialist reference | FND-002, SAML-002, SAML-005 | Planned | `part-saml/SAML-010-artifact-binding.md` |
| OAUTH-001 | Core | FND-001, FND-002, FND-003, SAML-001 | Planned | `part-oauth/OAUTH-001-permission-to-call-an-api.md` |
| OAUTH-002 | Core | OAUTH-001, FND-002 | Planned | `part-oauth/OAUTH-002-authorization-code-with-pkce.md` |
| OAUTH-003 | Core | OAUTH-001, OAUTH-002, SAML-003 | Planned | `part-oauth/OAUTH-003-client-endpoint-and-permission-contract.md` |
| OAUTH-004 | Core | OAUTH-002 | Planned | `part-oauth/OAUTH-004-renewing-access.md` |
| OAUTH-005 | Core | OAUTH-001, OAUTH-002, OAUTH-003 | Planned | `part-oauth/OAUTH-005-client-credentials.md` |
| OAUTH-006 | Core | OAUTH-001, OAUTH-002, OAUTH-003 | Planned | `part-oauth/OAUTH-006-device-authorization.md` |
| OAUTH-007 | Core | OAUTH-002, OAUTH-003, OAUTH-004, OAUTH-005 | Planned | `part-oauth/OAUTH-007-investigating-authorization-failures.md` |
| OAUTH-008 | Core | OAUTH-002, OAUTH-003, OAUTH-005, OAUTH-006, OAUTH-007 | Planned | `part-oauth/OAUTH-008-legacy-flows-and-migration.md` |
| OIDC-001 | Core | FND-003, OAUTH-001, OAUTH-002, OAUTH-003 | Planned | `part-oidc/OIDC-001-first-oidc-login.md` |
| OIDC-002 | Core | OIDC-001, OAUTH-003 | Planned | `part-oidc/OIDC-002-trust-discovery-and-id-token-validation.md` |
| OIDC-003 | Core | OIDC-001, OIDC-002, FND-001 | Planned | `part-oidc/OIDC-003-identity-and-account-mapping.md` |
| OIDC-004 | Core | OIDC-001, OIDC-002, OIDC-003 | Planned | `part-oidc/OIDC-004-authentication-requirements.md` |
| OIDC-005 | Core | OIDC-003, OIDC-004, SAML-004, OAUTH-004 | Planned | `part-oidc/OIDC-005-sessions-and-logout.md` |
| OIDC-006 | Core | OIDC-002, OIDC-003, OIDC-004, OIDC-005, OAUTH-007 | Planned | `part-oidc/OIDC-006-investigating-login-and-api-failures.md` |
| OIDC-007 | Advanced engineering | OAUTH-002, OAUTH-003, OIDC-002, OIDC-006 | Planned | `part-oidc/OIDC-007-confidential-client-nonce-alternative.md` |
| TOK-001 | Core | SAML-002, OAUTH-002, OIDC-002 | Planned | `part-tokens/TOK-001-token-formats-and-meaning.md` |
| TOK-002 | Core | TOK-001, OAUTH-003, OAUTH-007, OIDC-002 | Planned | `part-tokens/TOK-002-api-token-validation.md` |
| TOK-003 | Core | TOK-001, TOK-002, OIDC-002, SAML-006 | Planned | `part-tokens/TOK-003-signing-key-rotation.md` |
| TOK-004 | Core | TOK-002, OAUTH-004, OIDC-005 | Planned | `part-tokens/TOK-004-expiry-revocation-and-surviving-sessions.md` |
| TOK-005 | Core | OAUTH-004, TOK-004 | Planned | `part-tokens/TOK-005-refresh-token-lifecycle.md` |
| TOK-006 | Core | TOK-001, TOK-002, TOK-005, FND-002 | Planned | `part-tokens/TOK-006-token-exposure-and-safe-diagnostics.md` |
| TOK-007 | Advanced engineering | TOK-003, TOK-005, TOK-006 | Planned | `part-tokens/TOK-007-concurrent-refresh-investigation.md` |
| ARCH-001 | Core | OAUTH-002, OIDC-001, OIDC-005, TOK-002, TOK-006 | Planned | `part-architectures/ARCH-001-web-architecture-choices.md` |
| ARCH-002 | Core | ARCH-001, FND-002, TOK-006 | Planned | `part-architectures/ARCH-002-browser-boundaries-and-failures.md` |
| ARCH-003 | Core | OAUTH-002, OAUTH-006, TOK-005, TOK-006 | Planned | `part-architectures/ARCH-003-native-mobile-cli-and-device-clients.md` |
| ARCH-004 | Core | OAUTH-001, OAUTH-005, TOK-002, OIDC-003 | Planned | `part-architectures/ARCH-004-business-authorization.md` |
| ARCH-005 | Core | ARCH-004, TOK-002 | Planned | `part-architectures/ARCH-005-gateways-and-downstream-apis.md` |
| ARCH-006 | Core | OAUTH-003, OAUTH-005, TOK-003, TOK-006 | Planned | `part-architectures/ARCH-006-service-authentication-and-credentials.md` |
| ARCH-007 | Core | ARCH-004, ARCH-006, TOK-005, TOK-006 | Planned | `part-architectures/ARCH-007-dependable-automation.md` |
| ARCH-008 | Advanced engineering | ARCH-004, ARCH-005, ARCH-006, TOK-002 | Planned | `part-architectures/ARCH-008-downstream-delegation-and-token-exchange.md` |
| ARCH-009 | Advanced engineering | SAML-002, OAUTH-005, ARCH-006, TOK-002 | Planned | `part-architectures/ARCH-009-workload-federation-and-assertion-grants.md` |
| SEC-001 | Core | SAML-005, OAUTH-003, OIDC-002, ARCH-002 | Planned | `part-security/SEC-001-transaction-and-issuer-integrity.md` |
| SEC-002 | Core | TOK-004, TOK-006, ARCH-001, ARCH-002, ARCH-006 | Planned | `part-security/SEC-002-stolen-tokens-and-session-cookies.md` |
| SEC-003 | Core | SAML-002, SAML-003, OIDC-003, TOK-002, ARCH-004, ARCH-005 | Planned | `part-security/SEC-003-trusted-data-and-identity-mistakes.md` |
| SEC-004 | Core | SEC-001, SEC-002, SEC-003, ARCH-007 | Planned | `part-security/SEC-004-integration-security-review.md` |
| SEC-005 | Specialist reference | OAUTH-003, OIDC-002, SEC-001, SEC-002, SEC-004 | Planned | `part-security/SEC-005-hardened-profiles-and-extensions.md` |
| OPS-001 | Core | SAML-003, OAUTH-003, ARCH-001, ARCH-004, SEC-004 | Planned | `part-operations/OPS-001-owned-integration-contract.md` |
| OPS-002 | Core | OPS-001, OIDC-003, ARCH-006 | Planned | `part-operations/OPS-002-okta-configuration-mapping.md` |
| OPS-003 | Core | OPS-001, OPS-002, SAML-007, SAML-008, OIDC-006, SEC-004 | Planned | `part-operations/OPS-003-acceptance-and-rejection-testing.md` |
| OPS-004 | Core | OPS-003, SAML-006, OAUTH-008, TOK-003, ARCH-006 | Planned | `part-operations/OPS-004-rotation-migration-and-rollback.md` |
| OPS-005 | Core | OPS-003, TOK-003, TOK-004, TOK-006, ARCH-007 | Planned | `part-operations/OPS-005-monitoring-and-dependencies.md` |
| OPS-006 | Core | OPS-004, OPS-005, SAML-007, SAML-008, OAUTH-007, OIDC-006 | Planned | `part-operations/OPS-006-incident-investigation-and-handoff.md` |
| CASE-001 | Core | SAML-003, SAML-004, SAML-005, SAML-006, OPS-001, OPS-002, OPS-003 | Planned | `part-case-studies/CASE-001-enterprise-saml-saas-integration.md` |
| CASE-002 | Core | OIDC-002, OIDC-003, OIDC-005, TOK-002, ARCH-001, ARCH-004, OPS-003 | Planned | `part-case-studies/CASE-002-oidc-web-application-and-api.md` |
| CASE-003 | Core | ARCH-001, ARCH-002, TOK-006, SEC-002, SEC-004 | Planned | `part-case-studies/CASE-003-browser-architecture-decision.md` |
| CASE-004 | Core | OAUTH-005, ARCH-004, ARCH-006, ARCH-007, OPS-004, OPS-005 | Planned | `part-case-studies/CASE-004-scheduled-service-integration.md` |
| CASE-005 | Core | SAML-006, SAML-007, TOK-003, OPS-004, OPS-005, OPS-006 | Planned | `part-case-studies/CASE-005-signing-key-rollover-incident.md` |
| CASE-006 | Core | OAUTH-007, OIDC-006, TOK-002, ARCH-004, ARCH-005, OPS-006 | Planned | `part-case-studies/CASE-006-login-works-api-fails.md` |
| CASE-007 | Core | OAUTH-008, ARCH-001, ARCH-003, SEC-001, OPS-003, OPS-004 | Planned | `part-case-studies/CASE-007-legacy-oauth-migration.md` |
| CASE-008 | Core | SAML-004, OIDC-005, TOK-004, OPS-001, OPS-002, OPS-005, OPS-006 | Planned | `part-case-studies/CASE-008-mixed-saml-and-oidc-enterprise.md` |
| CASE-009 | Advanced engineering | SAML-009, OIDC-003, ARCH-004, SEC-003, OPS-001, OPS-006 | Planned | `part-case-studies/CASE-009-partner-federation.md` |

## Purpose by lesson

### FND-001: Login, access, and account lifecycle

Distinguish identity, permission, account maintenance, federation, and SSO.

### FND-002: Following the browser and its sessions

Follow redirects, form posts, cookies, and separate server sessions.

### FND-003: Who creates each artifact, and who consumes it?

Distinguish assertions, codes, tokens, and cookies by purpose and consumer.

### SAML-001: The first complete SP-initiated login

Follow Maya from the first portal request to an authenticated portal session.

### SAML-002: Reading the assertion and deciding whether to accept it

Connect message fields and trusted expectations to the acceptance decision.

### SAML-003: Turning the exchange into an integration contract

Agree on identifiers, endpoints, trust, attributes, and account mapping.

### SAML-004: Understanding sessions and logout after SAML login

Explain what persists after login and what each lifecycle action ends.

### SAML-005: Starting at the application or at the identity provider

Compare initiation models and their transaction expectations.

### SAML-006: Changing certificates and configuration without breaking login

Plan trust and endpoint changes with verification and recovery.

### SAML-007: Finding why the portal rejects a SAML response

Diagnose delivery, correlation, validity, and signature failures.

### SAML-008: Finding why accepted authentication does not produce usable access

Investigate account mapping, permission, cookie, and logout failures.

### SAML-009: Keeping identities separate across multiple identity providers

Preserve trust and identity boundaries across providers.

### SAML-010: Recognizing artifact binding and its extra exchange

Follow artifact resolution and its additional dependencies.

### OAUTH-001: Why the portal needs permission to call an API

Separate application login from delegated API access.

### OAUTH-002: Following Authorization Code with PKCE from start to finish

Follow the complete exchange through a successful API response.

### OAUTH-003: Agreeing on the client, endpoints, and permissions

Establish registration, discovery, redirect, authentication, and permission contracts.

### OAUTH-004: Continuing access when an access token expires

Explain refresh credentials and replacement access.

### OAUTH-005: Giving a scheduled service its own API access

Follow Client Credentials without representing a signed-in human.

### OAUTH-006: Authorizing a device or command-line application

Follow browser approval and device polling as separate activities.

### OAUTH-007: Finding where authorization or API access failed

Locate failures at the authorization, token, and API stages.

### OAUTH-008: Recognizing legacy flows and planning a migration

Identify older arrangements and assess a replacement direction.

### OIDC-001: Signing in to the portal with OpenID Connect

Follow an OIDC login and separate ID-token and access-token consumers.

### OIDC-002: Establishing trust and validating the ID token

Connect trusted discovery, keys, claims, and transaction expectations.

### OIDC-003: Connecting the authenticated identity to an application account

Resolve identities safely and interpret UserInfo consistently.

### OIDC-004: Requesting the authentication the application needs

Connect authentication requirements to requests and returned evidence.

### OIDC-005: Following sessions, reauthentication, and logout

Explain session boundaries and the effects of logout mechanisms.

### OIDC-006: Finding why OIDC login or the next API call fails

Investigate authentication, identity, session, and API boundaries.

### OIDC-007: Evaluating a confidential-client nonce alternative to PKCE

Assess a conditional compatibility arrangement and its safeguards.

### TOK-001: Understanding what a token's format does and does not tell you

Separate representation, meaning, and trust.

### TOK-002: Deciding whether an API should accept an access token

Compare local validation and introspection while preserving API responsibilities.

### TOK-003: Keeping validation working through signing-key rotation

Investigate key publication, caches, rollover, and unknown-key failures.

### TOK-004: Understanding expiry, revocation, and the sessions that survive

Predict the effects and limits of lifecycle actions.

### TOK-005: Renewing access without mishandling refresh tokens

Explain rotation, replacement storage, reuse, and simple concurrency.

### TOK-006: Keeping tokens out of places they do not belong

Trace exposure and preserve useful, credential-safe evidence.

### TOK-007: Investigating concurrent refresh and uncertain outcomes

Reconstruct a multi-instance refresh incident from incomplete observations.

### ARCH-001: Choosing between a server-rendered application, browser-only application, and backend-for-frontend

Compare the placement of credentials, sessions, and operational responsibilities.

### ARCH-002: Explaining browser-specific failures and exposure

Distinguish cookie delivery, cross-origin access, and script execution.

### ARCH-003: Choosing an interaction for native, mobile, CLI, and device applications

Match authorization interactions to runtime constraints.

### ARCH-004: Deciding what an authenticated caller may do

Apply scope, tenant, object, and business-policy decisions.

### ARCH-005: Preserving authorization boundaries across gateways and multiple APIs

Assign validation and authorization responsibilities across services.

### ARCH-006: Choosing and managing a service's authentication credentials

Compare supported authentication methods and plan credential change.

### ARCH-007: Running automation through expiry, failures, and retries

Separate credential recovery from potentially repeated business operations.

### ARCH-008: Carrying delegated authority into a downstream service

Evaluate exchange, actor context, audiences, and issuance policy.

### ARCH-009: Using an external assertion to establish service identity

Explain workload federation and assertion-based access arrangements.

### SEC-001: Keeping the login tied to the right browser, request, and issuer

Connect transaction attacks to protections and their assumptions.

### SEC-002: Understanding what a stolen token or session cookie enables

Trace exposure into consequences and evaluate containment limits.

### SEC-003: Avoiding trusted-data mistakes and unsafe identity decisions

Separate authentic data from appropriate identity and authorization decisions.

### SEC-004: Reviewing an integration by tracing trust decisions

Produce a bounded review supported by evidence and negative tests.

### SEC-005: Recognizing hardened profiles and protocol extensions

Locate additional mechanisms by the requirements they address.

### OPS-001: Turning requirements into an owned integration contract

Make decisions, boundaries, assumptions, and ownership explicit.

### OPS-002: Mapping the contract onto Okta

Connect the standard design to product capabilities and configuration.

### OPS-003: Testing the contract, including rejection behavior

Evaluate acceptance evidence for intended and invalid interactions.

### OPS-004: Planning rotation, migration, cutover, and rollback

Coordinate changes through evidence-based gates.

### OPS-005: Monitoring the integration and its dependencies

Explain observations, availability, caches, clocks, and failure effects.

### OPS-006: Investigating, handing off, and closing an incident

Move from symptoms to supported diagnosis and verified recovery.

### CASE-001: Bringing an enterprise SaaS application into Acme SSO

Produce a SAML agreement and acceptance plan.

### CASE-002: Signing in to a web application and calling its API

Keep authentication and API authorization correct in one design.

### CASE-003: Choosing the architecture for a browser application

Defend a choice against a reasonable alternative.

### CASE-004: Operating a scheduled service without a human login

Combine service identity, bounded access, and reliable operations.

### CASE-005: Recovering from a signing-key rollover incident

Diagnose trust propagation and verify recovery.

### CASE-006: Investigating login works, but the API fails

Locate the failed decision across application and API boundaries.

### CASE-007: Migrating an older OAuth integration

Plan application and protocol changes together.

### CASE-008: Operating a mixed SAML and OIDC enterprise

Coordinate distinct sessions, credentials, lifecycle actions, and owners.

### CASE-009: Adding a partner without merging identity boundaries

Preserve provider, account, and tenant boundaries.
