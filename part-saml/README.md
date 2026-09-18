# Part 2: SAML

**Entry prerequisites:** FND-001, FND-002, FND-003.

**Core completion outcome:** Plan, explain, investigate, and maintain an ordinary SAML integration.

Follow the Core entries in order. Optional entries can be skipped. Lesson files are created as they are drafted; Planned titles are intentionally unlinked.

## From a working login to an integration contract

- **[SAML-001 - The first complete SP-initiated login](SAML-001-first-sp-initiated-login.md)** · Core · Draft\
  Follow Maya from the first portal request to an authenticated portal session.

- **SAML-002 - Reading the assertion and deciding whether to accept it** · Core · Planned\
  Connect message fields and trusted expectations to the acceptance decision.

- **SAML-003 - Turning the exchange into an integration contract** · Core · Planned\
  Agree on identifiers, endpoints, trust, attributes, and account mapping.

## Keeping an integration working

- **SAML-004 - Understanding sessions and logout after SAML login** · Core · Planned\
  Explain what persists after login and what each lifecycle action ends.

- **SAML-005 - Starting at the application or at the identity provider** · Core · Planned\
  Compare initiation models and their transaction expectations.

- **SAML-006 - Changing certificates and configuration without breaking login** · Core · Planned\
  Plan trust and endpoint changes with verification and recovery.

## Investigating failures from evidence

- **SAML-007 - Finding why the portal rejects a SAML response** · Core · Planned\
  Diagnose delivery, correlation, validity, and signature failures.

- **SAML-008 - Finding why accepted authentication does not produce usable access** · Core · Planned\
  Investigate account mapping, permission, cookie, and logout failures.

## Optional integration depth

- **SAML-009 - Keeping identities separate across multiple identity providers** · Advanced engineering · Planned\
  Preserve trust and identity boundaries across providers.

- **SAML-010 - Recognizing artifact binding and its extra exchange** · Specialist reference · Planned\
  Follow artifact resolution and its additional dependencies.

## Readiness review

The cumulative assessment and worked answers will be written after this part's Core lessons. They may depend only on the concepts taught in those lessons. See the [coverage map](../authoring/coverage-map.md) for the approved assessment requirements.

[Table of contents](../TABLE-OF-CONTENTS.md) | [Course introduction](../README.md)
