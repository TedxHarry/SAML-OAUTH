# Part 5: Tokens, keys, and validation

**Entry prerequisites:** SAML, OAuth, and OIDC Core progression.

**Core completion outcome:** Choose validation strategies and reason through changing keys, renewal, revocation, and exposure.

Follow the Core entries in order. Optional entries can be skipped. Lesson files are created as they are drafted; Planned titles are intentionally unlinked.

## Choosing and applying a validation approach

- **TOK-001 - Understanding what a token's format does and does not tell you** · Core · Planned\
  Separate representation, meaning, and trust.

- **TOK-002 - Deciding whether an API should accept an access token** · Core · Planned\
  Compare local validation and introspection while preserving API responsibilities.

## Managing changing keys and credentials

- **TOK-003 - Keeping validation working through signing-key rotation** · Core · Planned\
  Investigate key publication, caches, rollover, and unknown-key failures.

- **TOK-004 - Understanding expiry, revocation, and the sessions that survive** · Core · Planned\
  Predict the effects and limits of lifecycle actions.

- **TOK-005 - Renewing access without mishandling refresh tokens** · Core · Planned\
  Explain rotation, replacement storage, reuse, and simple concurrency.

## Handling artifacts and investigating lifecycle failures

- **TOK-006 - Keeping tokens out of places they do not belong** · Core · Planned\
  Trace exposure and preserve useful, credential-safe evidence.

- **TOK-007 - Investigating concurrent refresh and uncertain outcomes** · Advanced engineering · Planned\
  Reconstruct a multi-instance refresh incident from incomplete observations.

## Readiness review

The cumulative assessment and worked answers will be written after this part's Core lessons. They may depend only on the concepts taught in those lessons. See the [coverage map](../authoring/coverage-map.md) for the approved assessment requirements.

[Table of contents](../TABLE-OF-CONTENTS.md) | [Course introduction](../README.md)
