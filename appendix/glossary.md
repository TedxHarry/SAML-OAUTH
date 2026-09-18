# Glossary

This reference grows as lessons introduce terms. Use the linked teaching home for the explanation and worked example. Entries below support the two current drafts; they do not replace them.

| Term | Plain-language meaning | Context | Teaching home |
|---|---|---|---|
| Assertion | A structured statement about a subject, with conditions and other information the receiver evaluates | SAML | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Assertion Consumer Service (ACS) | The SP endpoint that receives a SAML response in the pilot | SAML | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Audience | The intended relying party identified in the assertion's restrictions | SAML pilot | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Authentication | Establishing the account identity for an interaction using required evidence | Identity | [FND-001](../part-foundations/FND-001-login-access-and-account-lifecycle.md) |
| Authorization | Deciding whether a caller may perform an action on a resource | Application/API policy | [FND-001](../part-foundations/FND-001-login-access-and-account-lifecycle.md) |
| Bearer assertion | An assertion presented without proving possession of a separate cryptographic key; all applicable acceptance checks still apply | SAML | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Binding | Rules for transporting protocol messages | SAML | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Entity ID | An identifier for a SAML participant, not necessarily a browser endpoint | SAML | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Federation | An arrangement in which an application relies on an identity provider's verified authentication result | Identity | [FND-001](../part-foundations/FND-001-login-access-and-account-lifecycle.md) |
| Identity provider (IdP) | The participant that establishes identity and supplies the authentication result in the course's login example | Federation | [FND-001](../part-foundations/FND-001-login-access-and-account-lifecycle.md) |
| NameID | A SAML subject identifier; the pilot uses an agreed persistent value within the trusted IdP relationship | SAML | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Profile | Rules combining protocol mechanisms for a particular use, such as browser SSO | SAML | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Provisioning | Creating and maintaining the account and access-related data an application needs | Account lifecycle | [FND-001](../part-foundations/FND-001-login-access-and-account-lifecycle.md) |
| RelayState | A value carried through a SAML round trip; Acme uses an opaque handle to stored login context | SAML pilot | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Service provider (SP) | The application requesting and consuming an authentication result in the SAML example | SAML | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Session | State through which an application recognizes an ongoing interaction across requests | Applications | [FND-001](../part-foundations/FND-001-login-access-and-account-lifecycle.md) |
| Single sign-on (SSO) | An experience in which an existing authentication can satisfy another application interaction without repeated interactive authentication, subject to policy | Federation | [FND-001](../part-foundations/FND-001-login-access-and-account-lifecycle.md) |

## Entry conventions

Define a meaning once and link to its main teaching home. Distinguish related terms rather than treating them as synonyms. Explain acronyms. Leave detailed examples in lessons.

[Table of contents](../TABLE-OF-CONTENTS.md)
