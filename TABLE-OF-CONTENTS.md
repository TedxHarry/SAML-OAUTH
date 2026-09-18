# Table of contents

Read Core lessons in the order shown. Optional lessons do not supply prerequisites needed by the Core path.

**Depth:** Core | Advanced engineering | Specialist reference\
**Status:** Planned | Draft | Ready

Only lessons with actual draft files are linked. A Draft is available for review; it has not yet passed every publication check. The other 62 titles reserve the approved curriculum without empty lesson files.

## Part 1: Foundations

### Understanding the login problem

- **[FND-001 - Login, access, and account lifecycle](part-foundations/FND-001-login-access-and-account-lifecycle.md)** · Core · Draft\
  Distinguish identity, permission, account maintenance, federation, and SSO.

### Following the exchange

- **FND-002 - Following the browser and its sessions** · Core · Planned\
  Follow redirects, form posts, cookies, and separate server sessions.

- **FND-003 - Who creates each artifact, and who consumes it?** · Core · Planned\
  Distinguish assertions, codes, tokens, and cookies by purpose and consumer.

## Part 2: SAML

### From a working login to an integration contract

- **[SAML-001 - The first complete SP-initiated login](part-saml/SAML-001-first-sp-initiated-login.md)** · Core · Draft\
  Follow Maya from the first portal request to an authenticated portal session.

- **SAML-002 - Reading the assertion and deciding whether to accept it** · Core · Planned\
  Connect message fields and trusted expectations to the acceptance decision.

- **SAML-003 - Turning the exchange into an integration contract** · Core · Planned\
  Agree on identifiers, endpoints, trust, attributes, and account mapping.

### Keeping an integration working

- **SAML-004 - Understanding sessions and logout after SAML login** · Core · Planned\
  Explain what persists after login and what each lifecycle action ends.

- **SAML-005 - Starting at the application or at the identity provider** · Core · Planned\
  Compare initiation models and their transaction expectations.

- **SAML-006 - Changing certificates and configuration without breaking login** · Core · Planned\
  Plan trust and endpoint changes with verification and recovery.

### Investigating failures from evidence

- **SAML-007 - Finding why the portal rejects a SAML response** · Core · Planned\
  Diagnose delivery, correlation, validity, and signature failures.

- **SAML-008 - Finding why accepted authentication does not produce usable access** · Core · Planned\
  Investigate account mapping, permission, cookie, and logout failures.

### Optional integration depth

- **SAML-009 - Keeping identities separate across multiple identity providers** · Advanced engineering · Planned\
  Preserve trust and identity boundaries across providers.

- **SAML-010 - Recognizing artifact binding and its extra exchange** · Specialist reference · Planned\
  Follow artifact resolution and its additional dependencies.

## Part 3: OAuth 2.0

### From an application requirement to authorized API access

- **OAUTH-001 - Why the portal needs permission to call an API** · Core · Planned\
  Separate application login from delegated API access.

- **OAUTH-002 - Following Authorization Code with PKCE from start to finish** · Core · Planned\
  Follow the complete exchange through a successful API response.

- **OAUTH-003 - Agreeing on the client, endpoints, and permissions** · Core · Planned\
  Establish registration, discovery, redirect, authentication, and permission contracts.

### Keeping access usable over time

- **OAUTH-004 - Continuing access when an access token expires** · Core · Planned\
  Explain refresh credentials and replacement access.

### Choosing an exchange for a different kind of client

- **OAUTH-005 - Giving a scheduled service its own API access** · Core · Planned\
  Follow Client Credentials without representing a signed-in human.

- **OAUTH-006 - Authorizing a device or command-line application** · Core · Planned\
  Follow browser approval and device polling as separate activities.

### Diagnosing failures and recognizing older integrations

- **OAUTH-007 - Finding where authorization or API access failed** · Core · Planned\
  Locate failures at the authorization, token, and API stages.

- **OAUTH-008 - Recognizing legacy flows and planning a migration** · Core · Planned\
  Identify older arrangements and assess a replacement direction.

## Part 4: OpenID Connect

### From API authorization to application login

- **OIDC-001 - Signing in to the portal with OpenID Connect** · Core · Planned\
  Follow an OIDC login and separate ID-token and access-token consumers.

- **OIDC-002 - Establishing trust and validating the ID token** · Core · Planned\
  Connect trusted discovery, keys, claims, and transaction expectations.

- **OIDC-003 - Connecting the authenticated identity to an application account** · Core · Planned\
  Resolve identities safely and interpret UserInfo consistently.

### Controlling authentication and understanding sessions

- **OIDC-004 - Requesting the authentication the application needs** · Core · Planned\
  Connect authentication requirements to requests and returned evidence.

- **OIDC-005 - Following sessions, reauthentication, and logout** · Core · Planned\
  Explain session boundaries and the effects of logout mechanisms.

### Investigating OIDC failures

- **OIDC-006 - Finding why OIDC login or the next API call fails** · Core · Planned\
  Investigate authentication, identity, session, and API boundaries.

### Optional compatibility depth

- **OIDC-007 - Evaluating a confidential-client nonce alternative to PKCE** · Advanced engineering · Planned\
  Assess a conditional compatibility arrangement and its safeguards.

## Part 5: Tokens, keys, and validation

### Choosing and applying a validation approach

- **TOK-001 - Understanding what a token's format does and does not tell you** · Core · Planned\
  Separate representation, meaning, and trust.

- **TOK-002 - Deciding whether an API should accept an access token** · Core · Planned\
  Compare local validation and introspection while preserving API responsibilities.

### Managing changing keys and credentials

- **TOK-003 - Keeping validation working through signing-key rotation** · Core · Planned\
  Investigate key publication, caches, rollover, and unknown-key failures.

- **TOK-004 - Understanding expiry, revocation, and the sessions that survive** · Core · Planned\
  Predict the effects and limits of lifecycle actions.

- **TOK-005 - Renewing access without mishandling refresh tokens** · Core · Planned\
  Explain rotation, replacement storage, reuse, and simple concurrency.

### Handling artifacts and investigating lifecycle failures

- **TOK-006 - Keeping tokens out of places they do not belong** · Core · Planned\
  Trace exposure and preserve useful, credential-safe evidence.

- **TOK-007 - Investigating concurrent refresh and uncertain outcomes** · Advanced engineering · Planned\
  Reconstruct a multi-instance refresh incident from incomplete observations.

## Part 6: Application architectures and API authorization

### Choosing where the application handles credentials

- **ARCH-001 - Choosing between a server-rendered application, browser-only application, and backend-for-frontend** · Core · Planned\
  Compare the placement of credentials, sessions, and operational responsibilities.

- **ARCH-002 - Explaining browser-specific failures and exposure** · Core · Planned\
  Distinguish cookie delivery, cross-origin access, and script execution.

- **ARCH-003 - Choosing an interaction for native, mobile, CLI, and device applications** · Core · Planned\
  Match authorization interactions to runtime constraints.

### Turning accepted tokens into business authorization

- **ARCH-004 - Deciding what an authenticated caller may do** · Core · Planned\
  Apply scope, tenant, object, and business-policy decisions.

- **ARCH-005 - Preserving authorization boundaries across gateways and multiple APIs** · Core · Planned\
  Assign validation and authorization responsibilities across services.

### Building dependable service integrations

- **ARCH-006 - Choosing and managing a service's authentication credentials** · Core · Planned\
  Compare supported authentication methods and plan credential change.

- **ARCH-007 - Running automation through expiry, failures, and retries** · Core · Planned\
  Separate credential recovery from potentially repeated business operations.

### Optional service-identity and delegation patterns

- **ARCH-008 - Carrying delegated authority into a downstream service** · Advanced engineering · Planned\
  Evaluate exchange, actor context, audiences, and issuance policy.

- **ARCH-009 - Using an external assertion to establish service identity** · Advanced engineering · Planned\
  Explain workload federation and assertion-based access arrangements.

## Part 7: Security reasoning

### Protecting the transaction and its credentials

- **SEC-001 - Keeping the login tied to the right browser, request, and issuer** · Core · Planned\
  Connect transaction attacks to protections and their assumptions.

- **SEC-002 - Understanding what a stolen token or session cookie enables** · Core · Planned\
  Trace exposure into consequences and evaluate containment limits.

### Preserving meaning after cryptographic validation

- **SEC-003 - Avoiding trusted-data mistakes and unsafe identity decisions** · Core · Planned\
  Separate authentic data from appropriate identity and authorization decisions.

### Reviewing a design and recognizing additional protections

- **SEC-004 - Reviewing an integration by tracing trust decisions** · Core · Planned\
  Produce a bounded review supported by evidence and negative tests.

- **SEC-005 - Recognizing hardened profiles and protocol extensions** · Specialist reference · Planned\
  Locate additional mechanisms by the requirements they address.

## Part 8: Production, operations, and Okta in practice

### Agreeing on the integration before configuring it

- **OPS-001 - Turning requirements into an owned integration contract** · Core · Planned\
  Make decisions, boundaries, assumptions, and ownership explicit.

- **OPS-002 - Mapping the contract onto Okta** · Core · Planned\
  Connect the standard design to product capabilities and configuration.

### Verifying and changing the integration

- **OPS-003 - Testing the contract, including rejection behavior** · Core · Planned\
  Evaluate acceptance evidence for intended and invalid interactions.

- **OPS-004 - Planning rotation, migration, cutover, and rollback** · Core · Planned\
  Coordinate changes through evidence-based gates.

### Operating and supporting the service

- **OPS-005 - Monitoring the integration and its dependencies** · Core · Planned\
  Explain observations, availability, caches, clocks, and failure effects.

- **OPS-006 - Investigating, handing off, and closing an incident** · Core · Planned\
  Move from symptoms to supported diagnosis and verified recovery.

## Part 9: Final case studies

### Designing an integration

- **CASE-001 - Bringing an enterprise SaaS application into Acme SSO** · Core · Planned\
  Produce a SAML agreement and acceptance plan.

- **CASE-002 - Signing in to a web application and calling its API** · Core · Planned\
  Keep authentication and API authorization correct in one design.

- **CASE-003 - Choosing the architecture for a browser application** · Core · Planned\
  Defend a choice against a reasonable alternative.

- **CASE-004 - Operating a scheduled service without a human login** · Core · Planned\
  Combine service identity, bounded access, and reliable operations.

### Investigating and changing a running integration

- **CASE-005 - Recovering from a signing-key rollover incident** · Core · Planned\
  Diagnose trust propagation and verify recovery.

- **CASE-006 - Investigating login works, but the API fails** · Core · Planned\
  Locate the failed decision across application and API boundaries.

- **CASE-007 - Migrating an older OAuth integration** · Core · Planned\
  Plan application and protocol changes together.

### Coordinating multiple trust relationships

- **CASE-008 - Operating a mixed SAML and OIDC enterprise** · Core · Planned\
  Coordinate distinct sessions, credentials, lifecycle actions, and owners.

- **CASE-009 - Adding a partner without merging identity boundaries** · Advanced engineering · Planned\
  Preserve provider, account, and tenant boundaries.

## Supporting references

[Glossary](appendix/glossary.md) | [Okta-first vendor mapping](appendix/vendor-mapping.md) | [Error and symptom catalog](appendix/error-symptom-catalog.md)

[Course introduction](README.md)
