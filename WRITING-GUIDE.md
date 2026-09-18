# Writing guide

## Teach the problem before naming the machinery

Write like an experienced practitioner explaining an integration to a newer engineer sitting beside them.

Begin with what someone is trying to do, what the application knows, and what it needs to establish. Introduce a technical term when it helps explain that situation.

The usual progression is:

1. A concrete problem.
2. The people and systems involved.
3. One complete successful example.
4. The reasoning behind its steps.
5. Relevant messages and configuration.
6. Acceptance checks and trust.
7. A meaningful failure or limitation.
8. Evidence, correction, and verification.

Adapt this sequence to the lesson. Do not force a short concept explanation and a multi-stage investigation into identical sections. The [SAML-001 pilot](part-saml/SAML-001-first-sp-initiated-login.md) is the voice reference, not a mandatory layout.

## Keep one learning purpose

Every lesson must answer one clear engineering question. Before adding material, ask whether the reader needs it for that question. Put deeper comparisons in their assigned teaching homes.

Do not split a lesson merely because it contains several fields. Do not keep it together merely because those fields belong to one specification. Split when the remaining material introduces a separate problem or prerequisite burden. Assign a new ID without renumbering existing lessons.

## Voice and wording

Use clear, direct prose. Explain reasoning before presenting XML, token claims, configuration tables, or code. Define unfamiliar terms at first use, then use their correct names consistently.

Avoid:

- Em dashes.
- Marketing language and exaggerated promises.
- Stock openings and concluding summaries.
- "Simply configure," "just validate," or "check the logs" without explanation.
- Forced analogies, unexplained acronyms, and repetitive recaps.
- Time estimates or an arbitrary target lesson count.
- Claims that completing the reading supplies production experience.

Tables summarize explanations or compare options. They should not be the reader's first encounter with every concept in a lesson.

## Lesson header

Use the lesson title as the main heading. Follow with immutable ID, depth tag, prerequisites by ID, and one observable learning outcome. Keep this metadata short.

Link prerequisites when their files exist. Identify unwritten prerequisites as Planned. A Draft file carries a brief draft notice. Publication status also belongs in the navigation and authoring register.

## IDs, paths, and navigation

IDs are permanent and independent of reading order. Prefixes are `FND`, `SAML`, `OAUTH`, `OIDC`, `TOK`, `ARCH`, `SEC`, `OPS`, and `CASE`. Never reuse or renumber an assigned ID.

Use one Markdown file per lesson. A part is a directory. Modules are named groups in its README. Use relative links with the lesson ID in the visible label. Update incoming links if a file moves.

The table of contents owns reading order. Each part README mirrors its module groups and gives each lesson a one-line description. Core navigation must remain usable when optional lessons are skipped. Optional lessons provide a clear return link to the Core path.

Do not link planned lessons to nonexistent files. Refer to their ID and mark them Planned until a file exists. The [lesson register](authoring/lesson-register.md) reserves all approved paths and prerequisites.

## The Acme environment

Use the [approved scenario reference](authoring/acme-scenario.md). Begin with Maya, the employee portal, and Acme's identity provider. Add the SaaS application, API, native client, scheduled service, and partner only when needed.

Use reserved example domains and fictional credentials. Clearly identify alternative deployments. The SAML and OIDC portal examples must not imply that both exchanges are required for one login. Keep identifiers, endpoints, account relationships, and evaluation times consistent.

## Explain every exchange precisely

For each significant message, identify:

- Sender and receiver.
- Endpoint and runtime.
- Browser-mediated or direct network delivery.
- Contents and any credentials or secrets.
- Receiver checks.
- State changed by success.
- What the next step depends on.

Represent internal validation, account lookup, and session creation as internal work, not network messages. Do not imply browser tools reveal backend processing or server-to-server token calls. A browser-only application's own network calls are a different case and should be labeled accordingly.

## Diagram convention

Default to inline Mermaid sequence diagrams. Use stable, descriptive participant names, such as Browser, Portal backend, Identity provider, and Business API.

- Draw browser-mediated delivery as its actual browser-to-server hops.
- Draw direct server calls between the actual runtimes.
- Use notes or self-actions for internal work.
- Label meaningful endpoints and message purposes.
- Keep the diagram consistent with the adjacent walkthrough.

Do not draw an IdP-to-SP network arrow merely because the IdP created a response delivered by the browser. Use a table when it communicates a mapping or comparison more clearly.

Keep diagrams in lesson files. Add shared assets only when genuinely reused. Record rendering checks accurately; source inspection is not proof that GitHub rendered the diagram.

## Standards and implementation guidance

Prefer OASIS, IETF RFCs and Datatracker, OpenID Foundation specifications, and official vendor documentation. Use OWASP as supplementary security guidance. Use RFC 9700 as the OAuth security baseline.

Provide section- or lesson-level source notes sufficient to trace important claims. Verify document numbers and current status when writing. Distinguish protocol requirements, security recommendations, chosen implementation behavior, and vendor behavior. State optional and conditional requirements accurately.

Date verification notes for evolving specifications or product capabilities. Do not copy an old verification date into a newly checked lesson.

Teach maintained protocol libraries as the normal implementation approach. Explain what the library does and what configuration, trust, policy, and lifecycle responsibilities remain with the application.

## Okta examples

Explain the standard first, then give a short labeled Okta example. Distinguish org and custom authorization servers; Okta APIs and Acme APIs; assignment, claims, and API permission; and capability, configuration, and production entitlement.

Keep the full terminology mapping in the appendix. Avoid repeated console walkthroughs.

## Troubleshooting

Begin with expected working behavior. For each investigation provide the symptom, available evidence, plausible explanations, a distinguishing check, a supported cause, correction, and positive and relevant negative verification.

Do not treat a generic error code as a diagnosis. Separate standardized errors from provider messages and visible symptoms. Preserve uncertainty: "consistent with" and "confirmed by" mean different things.

## Examples and observation boxes

Label every fictional trace and simplified excerpt. Do not describe incomplete XML or placeholder signatures as executable, verifiable messages.

For a verifiable artifact, record its test key, expected issuer and audience, evaluation time, and expected result. Check it before publication.

Use few optional observation boxes. Each must work without a tenant or account, use supplied fictional material, have a complete reading alternative, avoid real credentials and public-decoder exposure, and demonstrate any intended failure deterministically. Do not introduce a hidden lab requirement.

## Assessments

Ask the reader to predict, explain, investigate, or justify. Provide worked reasoning, not only an answer key.

Core assessments may use only earlier Core material and concepts taught within the current lesson. Optional references and observation boxes cannot supply necessary answers. Each teaching part ends with cumulative readiness questions. Final cases integrate prior knowledge without introducing new Core mechanisms.

## A short voice example

Maya's browser returns to the portal carrying a SAML response. The portal remembers that it started a login request called `_req_701`.

Before using the response, it needs to establish that this is the answer to that pending request. The response includes an `InResponseTo` value for that purpose. In this example, the value is `_req_701`, so the identifiers match.

That match answers one question: which request the response refers to. The portal still needs to check the trusted signature, intended recipient, validity, replay state, and browser interaction. Passing one check does not remove the others.

## Definition of done

A lesson is Ready when:

- Its single learning purpose is clear.
- Prerequisites are satisfied; Core depends only on earlier Core material.
- The successful example appears before its variants or failures.
- Acme identifiers, relationships, and timeline are consistent.
- Important technical claims have authoritative source notes.
- Requirements, recommendations, choices, and vendor behavior are distinguishable.
- Diagrams agree with the walkthrough and render in the intended environment.
- Relevant failures or limitations are explained.
- Verifiable artifacts have been tested and expected outcomes recorded.
- Assessments are answerable from material already taught.
- Relative links resolve.
- Navigation, references, coverage records, and changelog are updated.

## Writing and review loop

1. Read the approved plan, prerequisites, and Acme reference.
2. Select one concrete example and identify its required sources.
3. Draft the narrative and successful exchange.
4. Add technical artifacts, decisions, and relevant failure reasoning.
5. Add an assessment and worked answer.
6. Check accuracy, prerequisites, voice, examples, links, and diagrams.
7. Review the lesson and resolve concrete issues.
8. Mark it Ready and update supporting records.
9. Review the completed module before starting the next module.

References grow with the lessons. Do not pre-fill the glossary or error catalog with material the course has not yet taught.
