# Course coverage and dependency map

This is an authoring record, not the learner's navigation. Use the [table of contents](../TABLE-OF-CONTENTS.md) to read the course and the [lesson register](lesson-register.md) for all reserved paths and direct prerequisites.

## Published-material review

On 2026-09-18, FND-001 was reviewed for narrative-first structure, authentication/account/authorization separation, source notes, fictional-example consistency, and an assessment answerable from its own teaching. No additional prerequisite or content blocker was found. Module A of Foundations is reviewed; FND-001 is Ready.

FND-002 was reviewed on 2026-09-18 for message delivery, separate sessions, evidence limits, and prerequisite discipline. Its sequence diagram was visually inspected on GitHub and agrees with the walkthrough. FND-002 is Ready.

FND-003 is drafted with issuer/carrier/consumer distinctions, separate SAML and OIDC deployments, an API extension, and a wrong-credential investigation. The Foundations readiness assessment now covers all three lessons. Module B review and FND-003 publication review remain pending; SAML-001 remains Draft.

## Structural baseline

The approved plan has 64 entries: 56 Core, 6 Advanced engineering, and 2 Specialist reference. There are 55 teaching lessons and nine cases. The initial register contains 245 prerequisite links. Its reading order has no missing/later prerequisite, duplicate ID, or Core dependency on optional material.

This is a structural result, not a claim that unwritten lesson content has been validated. Core material and assessments must introduce sufficient understanding before relying on it.

## Foundations and landscape

| Required coverage | Primary teaching home |
|---|---|
| Authentication, authorization, identity lifecycle, federation, SSO | FND-001 |
| SSO/API authorization/provisioning distinction; several protocols in one application | FND-001; CASE-008 |
| LDAP, Kerberos, SCIM, Workflows boundaries | FND-001; OPS-001 |
| Requests, methods, headers, status codes, redirects, form POSTs | FND-002 |
| Cookies, server sessions, browser/direct channels, internal processing | FND-002 |
| Roles and artifacts; OAuth is not application login; not every token is JWT | FND-003; OAUTH-001 |
| Origins, sites, CORS, SameSite | SAML-001 minimum; ARCH-001 introduction; ARCH-002 full treatment |
| TLS limits, keys, certificates, signatures, trust | SAML-001 minimum; SAML-002 and TOK-001 depth |
| Encoding, hashing, signing, encryption | SAML-001/002, OAUTH-002, TOK-001 |
| XML, JSON, URL/form encoding | SAML-001/002; OAUTH-002 introduces JSON before interpreting its token response |

## SAML

| Required coverage | Primary teaching home |
|---|---|
| Assertions, protocols, bindings, profiles, roles, complete SP-initiated exchange | SAML-001 |
| AuthnRequest, Response, Assertion; issuer, entity ID, ACS, destination, recipient, RelayState | SAML-001; configuration in SAML-003 |
| Minimum account matching and session creation | SAML-001 |
| IDs, InResponseTo, Subject, bearer SubjectConfirmationData | SAML-002 |
| Conditions, audience, validity, replay, clock tolerance | SAML-002 |
| AuthnStatement, AuthnContext, SessionIndex, status and nested codes | SAML-002 |
| AttributeStatement recognition | SAML-002; attribute contracts in SAML-003 |
| Response/assertion signatures, encryption distinction, exact consumed assertion | SAML-002 |
| Metadata, certificate trust, manual/metadata configuration, identifiers and URLs | SAML-002/003 |
| NameID, attributes, mapping, JIT, unsafe linking, MFA/context requirements | SAML-003 |
| Separate sessions, local logout, Single Logout | SAML-004 |
| Initiation models, request correlation, Redirect/POST | SAML-005 |
| Rollover, overlapping trust, environments, proxies, external URLs | SAML-006 |
| Migration, testing, cutover, rollback | SAML-006; OPS-003/004 |
| Multiple IdPs and partner federation | SAML-009; CASE-009 |
| Artifact binding and resolution | SAML-010 |

## OAuth and OIDC

| Required coverage | Primary teaching home |
|---|---|
| OAuth roles, delegated access, scope/resource/audience restrictions, consent | OAUTH-001 |
| Bearer possession and consequences | OAUTH-001/002; SEC-002 |
| Complete code flow with PKCE S256, state, redirect, verifier/challenge, code exchange, API call | OAUTH-002 |
| Public/confidential clients, client/user authentication, endpoints, artifacts | OAUTH-002 |
| Registration, redirect contracts, authentication, scopes and policy | OAUTH-003 |
| OAuth server metadata, approved trust, PKCE enforcement/downgrade protection | OAUTH-003 |
| Original specifications versus current security guidance | OAUTH-002/003 |
| Refresh grant; Client Credentials; Device Authorization | OAUTH-004; OAUTH-005; OAUTH-006 |
| Machine identity differs from a human login | OAUTH-005 |
| Implicit/password recognition and migration; OAuth 1.0; current OAuth 2.1 status | OAUTH-008 |
| openid, OP/RP, complete login, ID token versus API token | OIDC-001 |
| sub, iss, aud, exp, iat, nonce, conditional azp; validation | OIDC-002 |
| OIDC Discovery/JWKS, distinct from OAuth metadata | OIDC-002 |
| UserInfo/subject consistency, issuer-plus-subject, email limitations | OIDC-003 |
| prompt, max_age, hints, auth_time, acr, amr, authentication versus consent | OIDC-004 |
| OIDC sessions and logout | OIDC-005 |
| Conditional confidential-client nonce alternative | OIDC-007 |
| Token exchange/delegated calls; JWT/SAML assertion grants | ARCH-008; ARCH-009 |

## Tokens, architectures, and API authorization

| Required coverage | Primary teaching home |
|---|---|
| Opaque/JWT; JWT/JWS/JWE/JWK/JWKS; decoding versus verification | TOK-001 |
| Algorithms, issuer/audience/expiry/purpose, resource-server duties, introspection/local validation | TOK-002 |
| Key IDs, JWKS cache, rotation, rollover failures | TOK-003 |
| Revocation limits, account/session effects | TOK-004 |
| Refresh rotation, reuse, sufficient Core concurrency | TOK-005 |
| Logs, URLs, storage, diagnostics and leakage | TOK-006 |
| Deep multi-instance refresh incident | TOK-007 |
| Server-rendered, browser-only, BFF | ARCH-001 |
| Browser behavior and failures | ARCH-002 |
| Native/mobile, CLI/device | ARCH-003 |
| Delegated/application access; scopes, roles, claims, resource, tenant/object policy | ARCH-004 |
| Gateways, downstream services, multiple API audiences | ARCH-005 |
| Secrets, private_key_jwt, mutual-TLS client authentication, credential rotation | ARCH-006 |
| Background services, caching, expiry, coordination, retries/backoff/rate limits/duplicate operations | ARCH-007 |
| Delegation/impersonation, token exchange, on-behalf-of patterns | ARCH-008 |
| Workload federation, assertion grants versus client authentication | ARCH-009 |

Every architecture comparison covers credential handling, redirects where applicable, sessions, token exposure, renewal, and operational tradeoffs. None is universally preferred.

## Security, operations, and cases

| Required coverage | Primary teaching home |
|---|---|
| CSRF/login CSRF, code interception/injection, redirect abuse | Introduced with flows; SEC-001 consolidation |
| Mix-up, issuer confusion, transaction binding | OAUTH-003/OIDC-002; SEC-001 |
| Theft/replay, XSS, logging | TOK-006/ARCH-002; SEC-002 |
| Audience/purpose confusion, unverified claims | TOK-002; SEC-003 |
| XML wrapping/parser risks, unsafe account linking, excessive scopes/consent | SAML-002/003, OIDC-003, OAUTH-003; SEC-003 |
| Review method, assumptions, protection limits, negative tests | SEC-004 |
| DPoP and mutual-TLS-bound awareness | SEC-002 |
| PAR, JAR/JARM, RAR, Resource Indicators, registration, resource metadata, FAPI, CIBA | One compact SEC-005 map |
| Requirements, protocol/flow selection, trust, ownership, configuration contract | OPS-001 |
| Okta mapping, org/custom server, API targets, assignments/claims/permissions, entitlements | OPS-002 |
| Environments and positive/negative evidence | OPS-001/003 |
| Rotation, migration, interoperability, change, rollback | OPS-004 |
| Monitoring, correlation IDs, safe logs, clocks, availability/dependencies | OPS-005 |
| Incident handoff, escalation, verified recovery | OPS-006 |
| Enterprise SAML SaaS; OIDC web/API; browser architecture; scheduled service | CASE-001/002/003/004 respectively |
| Rollover incident; login works/API fails; legacy migration; mixed enterprise | CASE-005/006/007/008 respectively |
| Partner or multi-tenant federation | CASE-009 |

## Worked troubleshooting ownership

| Investigation | Worked home |
|---|---|
| Wrong ACS; issuer/audience; destination/recipient mismatch | SAML-007 |
| InResponseTo, initiation model, expired/not-yet-valid assertion | SAML-007 after SAML-005 |
| Signature/certificate rollover failure | SAML-007; CASE-005 |
| Missing attributes, unsuitable NameID, accepted assertion/access denial | SAML-008 |
| Redirect loops, session cookies, logout leaves a session alive | SAML-008 |
| invalid_client; code expiry/reuse/PKCE/invalid_grant; state | OAUTH-007 |
| Consent and tenant restrictions | OAUTH-007 |
| Nonce where applicable; token issuer/audience/purpose | OIDC-006; OAUTH-007 for API context |
| Unknown key and stale JWKS | TOK-003 |
| Refresh reuse/simple concurrency; deeper incident | TOK-005; optional TOK-007 |
| Login succeeds/API rejects; accepted token/business denial | OIDC-006 and CASE-006; ARCH-004 |
| Browser cookie/session/CORS | OIDC-006 and ARCH-002 |

Each investigation supplies symptoms, evidence, competing explanations, a distinguishing check, correction, and verification. The catalog is a lookup derived from these lessons, not a replacement for them.

## Accepted review corrections

- SAML-001: unpack bearer; move cookie attributes after the returning POST.
- SAML-002: recognize AttributeStatement and point to SAML-003. Keep essential signature, timing, and replay understanding with acceptance if deeper mechanics are split.
- SAML-005: state unsolicited-response implications; assess initiation model explicitly.
- OAUTH-003: prerequisite SAML-003 added for the shared worksheet.
- OIDC-005: length safeguard for provider logout details; preserve sufficient Core session-survival reasoning.
- OIDC-006: prerequisite OAUTH-007 added for reused investigations.
- ARCH-004 owns full business authorization after token acceptance.
- ARCH-008: exchange does not inherently guarantee reduced authority. Inspect policy and resulting authorization context.
- SEC-002 connects to ARCH-005; any ARCH-008 connection remains optional.

## First-exposure safeguards

FND-002 precedes session mechanics. SAML-001 introduces keys, certificates, trust and signature limits before validation. OAUTH-002 explains hashing and JSON as needed and includes minimum API checks. OIDC-001 introduces enough token/key concepts before its first validation. OAUTH-003 and OIDC-002 begin discovery from approved configuration. TOK-005 supplies Core concurrency without TOK-007. SEC-001 supplies its two-provider context locally. OPS-002 supplies inbound role-reversal context without optional SAML-009.

## Repetition and size controls

- SAML-004 establishes lifecycle comparison; OIDC-005 and TOK-004 extend it; CASE-008 applies it.
- SAML-006/TOK-003 teach rotation mechanics; OPS-004 coordinates change; CASE-005 investigates an incident.
- TOK-006 owns exposure paths; ARCH-001/003 select runtimes; SEC-002 evaluates consequences.
- One integration worksheet grows through SAML-003, OAUTH-003, OPS-001.
- Protocol lessons introduce protections; Part 7 connects threats, assumptions, and remaining risks.
- Cases require combined decisions or evidence; they must not repeat prior walkthroughs with renamed participants.

Watch SAML-002/007/008, OAUTH-002, OIDC-002/005, ARCH-001, and OPS-002 for length. Remove repetition first. Split only for a separate purpose or an otherwise unreadable explanation; never renumber existing IDs.

## Readiness assessment requirements

| Part | Required cumulative reasoning |
|---|---|
| Foundations | Separate authentication/account/permission; follow browser and sessions; distinguish artifacts and evidence |
| SAML | Trace login, identify initiation model/correlation, validate intended parties, map account, diagnose validation/session failures, plan rollover |
| OAuth | Separate login/API access, follow runtime calls, explain code/verifier/tokens, choose grants, diagnose token/API failures, recognize legacy migration |
| OIDC | Identify OIDC addition, trusted expectations, identity mapping, authentication evidence, surviving sessions, login/API failure |
| Tokens | Format versus trust, validation choice, business policy boundary, unknown keys, lifecycle actions, simple refresh overlap, safe evidence |
| Architectures | Defend runtime choice, locate credentials, distinguish CORS/authorization, enforce tenant/object checks, gateway boundaries, service rotation, safe retries |
| Security | Identify broken trust, explain misuse, choose protection and limits, distinguish authentic/appropriate data, negative tests, uncertainty |
| Operations | Identify missing ownership, product assumptions, release evidence, unsafe cutover, dependencies, safe observations, cause/hypothesis, handoff |
| Cases | Design/trust/messages/validation/failure/operations with worked reasoning, assumptions, and reasonable alternatives |

All Core assessments use prior Core understanding. Optional observation boxes and specialist lessons supply no required answers.

## Supporting artifacts

The glossary, vendor mapping, and error catalog grow lesson by lesson. The Acme reference prevents contradictions. The writing guide carries the narrative-first standard, diagram convention, authoritative sourcing, and definition of done. Keep standards, recommendations, implementation choices, and vendor behavior distinguishable. Use maintained libraries instead of production hand-rolled validators.
