# Glossary

This reference grows as lessons introduce terms. Use the linked teaching home for the explanation and worked example. Entries support the currently available lessons; they do not replace them.

| Term | Plain-language meaning | Context | Teaching home |
|---|---|---|---|
| Assertion | A structured statement about a subject, with conditions and other information the receiver evaluates | SAML | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Assertion Consumer Service (ACS) | The SP endpoint that receives a SAML response in the pilot | SAML | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Audience | The intended relying party identified in the assertion's restrictions | SAML pilot | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Authentication | Establishing the account identity for an interaction using required evidence | Identity | [FND-001](../part-foundations/FND-001-login-access-and-account-lifecycle.md) |
| Authorization | Deciding whether a caller may perform an action on a resource | Application/API policy | [FND-001](../part-foundations/FND-001-login-access-and-account-lifecycle.md) |
| Back channel | A direct exchange between server runtimes rather than delivery through the user's browser | Message delivery | [FND-002](../part-foundations/FND-002-following-the-browser-and-its-sessions.md) |
| Bearer assertion | An assertion presented without proving possession of a separate cryptographic key; all applicable acceptance checks still apply | SAML | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Binding | Rules for transporting protocol messages | SAML | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Cookie | Browser-held name/value data returned on eligible requests; this course's session cookies identify separate server-side sessions | HTTP | [FND-002](../part-foundations/FND-002-following-the-browser-and-its-sessions.md) |
| Endpoint | An address at which a service receives a particular kind of request | HTTP services | [FND-002](../part-foundations/FND-002-following-the-browser-and-its-sessions.md) |
| Entity ID | An identifier for a SAML participant, not necessarily a browser endpoint | SAML | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Federation | An arrangement in which an application relies on an identity provider's verified authentication result | Identity | [FND-001](../part-foundations/FND-001-login-access-and-account-lifecycle.md) |
| Front channel | Message delivery through the user's browser | Message delivery | [FND-002](../part-foundations/FND-002-following-the-browser-and-its-sessions.md) |
| Header | A named field carrying information about an HTTP request or response | HTTP | [FND-002](../part-foundations/FND-002-following-the-browser-and-its-sessions.md) |
| Identity provider (IdP) | The participant that establishes identity and supplies the authentication result in the course's login example | Federation | [FND-001](../part-foundations/FND-001-login-access-and-account-lifecycle.md) |
| Internal processing | Work within a component, such as validating a message or looking up a session, distinguished from a network message to another participant | Diagram convention | [FND-002](../part-foundations/FND-002-following-the-browser-and-its-sessions.md) |
| NameID | A SAML subject identifier; the pilot uses an agreed persistent value within the trusted IdP relationship | SAML | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Profile | Rules combining protocol mechanisms for a particular use, such as browser SSO | SAML | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Provisioning | Creating and maintaining the account and access-related data an application needs | Account lifecycle | [FND-001](../part-foundations/FND-001-login-access-and-account-lifecycle.md) |
| Redirect | A response directing the client to another location; following it creates a new request | HTTP | [FND-002](../part-foundations/FND-002-following-the-browser-and-its-sessions.md) |
| RelayState | A value carried through a SAML round trip; Acme uses an opaque handle to stored login context | SAML pilot | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Service provider (SP) | The application requesting and consuming an authentication result in the SAML example | SAML | [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md) |
| Session | State through which an application recognizes an ongoing interaction across requests | Applications | [FND-001](../part-foundations/FND-001-login-access-and-account-lifecycle.md) |
| Single sign-on (SSO) | An experience in which an existing authentication can satisfy another application interaction without repeated interactive authentication, subject to policy | Federation | [FND-001](../part-foundations/FND-001-login-access-and-account-lifecycle.md) |
| Access token | Credential presented for protected-resource access; acceptance and permission checks still apply | OAuth | [FND-003](../part-foundations/FND-003-artifact-creators-and-consumers.md) |
| Authorization code | Short-lived, single-use value the client redeems at the authorization server token endpoint | OAuth code flow | [FND-003](../part-foundations/FND-003-artifact-creators-and-consumers.md) |
| Authorization server | Service issuing tokens under the access arrangement | OAuth | [FND-003](../part-foundations/FND-003-artifact-creators-and-consumers.md) |
| Client | Application seeking access to a protected resource | OAuth | [FND-003](../part-foundations/FND-003-artifact-creators-and-consumers.md) |
| Consumer | Component interpreting or validating an artifact for its intended use | Exchange roles | [FND-003](../part-foundations/FND-003-artifact-creators-and-consumers.md) |
| ID token | Authentication result issued to an OIDC client; not the business API access credential | OIDC | [FND-003](../part-foundations/FND-003-artifact-creators-and-consumers.md) |
| JSON Web Token (JWT) | A format for representing claims; its format alone does not establish trust or purpose | Token formats | [FND-003](../part-foundations/FND-003-artifact-creators-and-consumers.md) |
| Opaque value | Value whose contents the holding component treats as uninterpreted data | Artifact handling | [FND-003](../part-foundations/FND-003-artifact-creators-and-consumers.md) |
| OpenID Connect (OIDC) | Authentication layer on OAuth 2.0 | Login | [FND-003](../part-foundations/FND-003-artifact-creators-and-consumers.md) |
| OpenID Provider / Relying Party | Issuer of the OIDC authentication result / client relying on that result | OIDC roles | [FND-003](../part-foundations/FND-003-artifact-creators-and-consumers.md) |
| Refresh token | Optional credential used with the authorization server to request new access tokens | OAuth | [FND-003](../part-foundations/FND-003-artifact-creators-and-consumers.md) |
| Resource server | Service exposing the protected resource, such as Acme business API | OAuth | [FND-003](../part-foundations/FND-003-artifact-creators-and-consumers.md) |

## Entry conventions

Define a meaning once and link to its main teaching home. Distinguish related terms rather than treating them as synonyms. Explain acronyms. Leave detailed examples in lessons.

[Table of contents](../TABLE-OF-CONTENTS.md)
