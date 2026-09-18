# Vendor mapping: Okta

This reference maps standard concepts to Okta terminology and behavior. The standard explanation remains in the linked lesson. Entries currently support SAML-001 only.

## SAML

| Standard concept | Okta field | Role and direction | Important distinction |
|---|---|---|---|
| Portal ACS endpoint | Single sign-on URL | Okta as IdP, portal as SP | This is the SP response endpoint, not the Okta request endpoint |
| SP entity ID used as audience | Audience URI (SP Entity ID) | Intended application | An identifier is not automatically an endpoint |
| Subject identifier representation | Name ID format | IdP supplies subject to SP | Format and account-mapping policy are separate decisions |
| Application user identifier value | Application username | Value supplied for the application identity | The value must agree with the application's mapping contract |

**Teaching home:** [SAML-001](../part-saml/SAML-001-first-sp-initiated-login.md).\
**Official source:** [Okta SAML field reference](https://help.okta.com/en-us/content/topics/apps/aiw-saml-reference.htm).\
**Source checked:** 2026-09-17 during pilot review.

## OAuth and OpenID Connect

Entries will be added with the relevant lessons.

| Standard concept | Okta term or configuration area | Authorization server or API context | Important distinction | Lesson | Official source | Verified on |
|---|---|---|---|---|---|---|

## Capabilities and availability

| Capability | Applicable configuration | Availability or entitlement condition | Official source | Verified on |
|---|---|---|---|---|

## Maintenance

Keep org and custom authorization servers distinct. Keep Okta API access and application API access distinct. Do not infer authorization from assignment or claim presence alone. Check current official documentation before adding product labels, support, or entitlement claims.

Add another vendor only when a specific lesson needs the comparison.

[Table of contents](../TABLE-OF-CONTENTS.md)
