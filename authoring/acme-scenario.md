# Acme scenario reference

This authoring record preserves the fictional environment. Add participants only when their lesson needs them. All credentials and traces are fictional; sample messages are not production captures.

## Established participants

| Participant | Role in the current drafts |
|---|---|
| Maya | Acme employee who reads her own reports; not a payroll administrator |
| Employee portal | Application with its own account mapping, session, and report permissions |
| Acme identity provider | Central authentication service trusted by the portal |
| Identity administrator | Maintains identities and the approved account lifecycle process |
| Portal owner | Owns local account mapping, sessions, and report authorization |

## Established identifiers

| Value | Meaning |
|---|---|
| `https://portal.example.com/reports` | Maya's requested portal page |
| `https://portal.example.com/saml` | SAML SP entity ID, not an endpoint used by the browser in this example |
| `https://portal.example.com/saml/acs` | Portal assertion consumer service |
| `https://idp.example.net/saml` | Trusted SAML IdP entity ID |
| `https://idp.example.net/sso` | IdP SSO endpoint |
| `acme-user-1042` | Fictional persistent NameID under the approved IdP relationship |
| `https://expenses.example.com/saml` | Different audience used by the pilot's negative exercise |

## SAML pilot evaluation context

Request `_req_701` starts at `2026-09-17T18:00:00Z`. Assertion `_assert_901` is evaluated at `18:00:20Z` on that date. Conditions run from `18:00:00Z` up to, but excluding, `18:05:00Z`. Bearer confirmation expires at `18:05:00Z`.

These fixed times are teaching assumptions, not current credentials. The pilot has no complete signature or test key and is not a cryptographic verification artifact.

The selected deployment uses Redirect for the request and POST for the response, accepts unsigned AuthnRequests under its configured contract, and requires the IdP to validate the requested ACS against registration. The assertion is signed. Maya has an existing usable IdP session and no portal session at the start.

The temporary browser correlation cookie and authenticated portal cookie serve different purposes. The chosen attributes are implementation choices described in the pilot, not universal SAML requirements.

## Foundation variations

FND-001 first presents Maya's intended, working account and report access. It then deliberately varies the example by removing her local mapping or report permission. Those are hypothetical failure cases, not changes to the pilot's baseline.

## Browser-foundation illustration

FND-002 uses the same successful SAML deployment while omitting the authentication message fields and cookie attributes to explain delivery first. `FICTIONAL_IDP_HANDLE` and `FICTIONAL_PORTAL_HANDLE` are non-working labels for distinct host-only session cookies. The report and receiving endpoints remain unchanged.

`https://idp.example.net/status` is a separate fictional public-status endpoint used only to contrast a backend network request with browser traffic. It is not a SAML step or an asserted Okta capability.

## Future participants and deployments

The SaaS application, business API, native client, scheduled service, and partner are approved future roles. Allocate their URLs and relationships when their first lesson is written, then record them here.

The OIDC portal will be a clearly labeled alternative deployment. Do not imply SAML and OIDC are both required for one login. A later mixed-enterprise case may place them in different applications explicitly.

Okta examples remain inside the Acme setting. A reserved example hostname represents a fictional service, not a real Okta tenant endpoint.
