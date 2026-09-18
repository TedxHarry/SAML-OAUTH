# SAML, OIDC and OAuth 2.0: From Understanding to Engineering

An employee signs in successfully, but the application rejects the response. Another application accepts the login, but its API refuses the request. A signing-key change works for one integration and breaks another.

Understanding those situations requires following the exchange: who sent the message, who should receive it, what the receiver checks, and what happens after acceptance.

This course develops that understanding through SAML, OAuth 2.0, and OpenID Connect, using one fictional organization, Acme.

## Who this course is for

You should already be comfortable with applications, users, passwords, browsers, servers, basic HTTP, and simple networking.

You do not need prior knowledge of federation, tokens, certificates, browser security boundaries, or API authorization. Those concepts appear when the examples need them.

The entire course can be completed by reading. No identity tenant, software purchase, or deployment is required.

## What you should be able to do

By the end, you should be able to:

- Follow authentication and authorization exchanges across browsers and servers.
- Explain the integration settings covered in the course and investigate unfamiliar ones.
- Distinguish a valid signature from a fully acceptable message or token.
- Separate authentication, account matching, sessions, and application authorization.
- Diagnose failures using evidence rather than configuration guesses.
- Reason about service access, credential renewal, rotation, and operational change.
- Map the standards to an Okta-centered environment without confusing product behavior with protocol requirements.

A reading course cannot provide years of production experience. It can give you the foundations to investigate correctly and learn from real integration work more quickly.

This course does not cover every setting in every product. Provisioning, including SCIM, and Okta Workflows appear where they connect to these protocols. Their complete implementation belongs to separate material.

## How to read it

Follow the [table of contents](TABLE-OF-CONTENTS.md).

Every lesson has one of three depth tags:

- **Core:** the continuous path for ordinary integrations.
- **Advanced engineering:** deeper design and investigation, taken when useful.
- **Specialist reference:** material for particular requirements.

Core lessons depend only on earlier Core lessons. You can skip optional lessons without losing prerequisites needed later.

The progression is:

**Foundations → SAML → OAuth → OIDC → Tokens and keys → Architectures and APIs → Security → Operations and Okta → Case studies**

SAML comes first to establish a complete browser SSO story. OAuth then introduces API authorization, and OIDC adds an authentication result to the OAuth exchange. Later parts connect those mechanisms through architecture, lifecycle, and operational decisions.

## What the lessons look like

Each lesson begins with a situation and explains the reasoning before introducing message fields, configuration tables, or code excerpts.

Examples include annotated HTTP, XML, and token excerpts; diagrams separating browser traffic, direct server calls, and internal processing; configuration decisions tied to messages or checks; fictional troubleshooting evidence; and reasoning exercises with worked answers.

Optional observation boxes are supplementary. They use supplied fictional material and include a reading alternative. Never paste real assertions, tokens, secrets, or session cookies into a public decoder.

## Standards and Okta examples

The standard explanation comes first. Short Okta examples follow where they help connect the protocol to a real product.

Lessons distinguish protocol requirements, security recommendations, implementation choices, and vendor-specific behavior. Version-sensitive claims include a dated verification note.

The course uses maintained protocol libraries as the normal implementation approach. It explains validation so you can configure and investigate it, not so you can replace a reviewed library with a custom validator.

## References

- [Glossary](appendix/glossary.md)
- [Okta-first vendor mapping](appendix/vendor-mapping.md)
- [Error and symptom catalog](appendix/error-symptom-catalog.md)

These references grow alongside the lessons.

## Publication status

The approved structure contains 64 entries: 56 Core, 6 Advanced engineering, and 2 Specialist reference. It includes 55 teaching lessons and nine integrated cases.

Three lessons are available:

- [FND-001: Login, access, and account lifecycle](part-foundations/FND-001-login-access-and-account-lifecycle.md) · Ready
- [FND-002: Following the browser and its sessions](part-foundations/FND-002-following-the-browser-and-its-sessions.md) · Draft
- [SAML-001: The first complete SP-initiated login](part-saml/SAML-001-first-sp-initiated-login.md) · Draft, the reviewed pilot

The other 61 lessons are Planned, not yet written. The table of contents distinguishes **Planned**, **Draft**, and **Ready** material. No lesson is labeled Ready merely because its file exists.

For authoring conventions, see the [writing guide](WRITING-GUIDE.md). Structural coverage is tracked in the [coverage map](authoring/coverage-map.md), with paths and prerequisites in the [lesson register](authoring/lesson-register.md). Actual changes are recorded in the [changelog](CHANGELOG.md).
