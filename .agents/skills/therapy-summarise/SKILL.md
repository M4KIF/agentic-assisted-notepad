---
name: therapy-summarise
description: Prepare or update an optional, dated therapy-session briefing from the session date and relevant notes, with user-selected topics and no expectation of progress, disclosure, or homework. User-invoked; not a daily-note-analysis facade route.
---

# Therapy summarise

Use this skill only when the user asks to prepare, refresh, or review a therapy-session briefing. Invoke it with an unambiguous session date, preferably `YYYY-MM-DD`; a filename/path may supply the date if the user makes clear that it is the therapy-session date. Example: `$therapy-summarise 2026-10-14`. If the date is ambiguous, ask one focused clarification rather than guessing. Preparation is optional; the user may omit topics, choose not to share the brief, or decide that no document is useful.

This is a stand-alone, user-invoked therapy workflow. Do **not** add this skill to the `daily-note-analysis` facade or make ordinary daily-note processing invoke it. When this skill itself must analyze material in `notes/`, follow the repository's root note directives and the applicable `daily-note-analysis` / specialist skill instructions. The therapy briefing is the consolidated output for the session; do not rewrite daily-note analyses or raw source notes as a side effect.

## Required context and skill selection

1. Read the repository `AGENTS.md` and `therapy/AGENTS.md` before preparing a briefing. Follow any more-specific instructions for the source material. Read `notes/AGENTS.md` if it exists and the material being interpreted is under `notes/`.
2. Read the nearest earlier therapy briefing to establish the prior session date and relevant context. Read linked feedback only when it is relevant to this request. Treat earlier briefings as prior formulations, not new evidence that those formulations were true; do not turn prior topics into standing goals.
3. For source material under `notes/`, use the `daily-note-analysis` routing policy and read the current relevant specialist skill instructions. Use only relevant skills:
   - relationship pattern or attachment-cycle material: [`relationship-analysis`](../relationship-analysis/SKILL.md);
   - misunderstanding, intent/impact, blunt/direct communication, or conflict repair: [`relationship-communication`](../relationship-communication/SKILL.md);
   - the user's reported emotions, body sensations, needs, or protective responses: [`emotional-analysis`](../emotional-analysis/SKILL.md);
   - reported overload, “hot anvil,” stomach clenching, or reduced capacity: [`nervous-system-overload-analysis`](../nervous-system-overload-analysis/SKILL.md);
   - flirting, sexting, validation-seeking, secrecy, or phone escape, when present and relevant: [`safety-escape-mechanism-analysis`](../safety-escape-mechanism-analysis/SKILL.md);
   - a concrete aid or pause script the user asks for: [`actionable-support`](../actionable-support/SKILL.md); do not introduce between-session exercises unless requested.
4. Read `notes/historical/gemini/relationship-context.md` or `internal-struggle-context.md` only when relevant. Treat historical context as user-reported background, never as evidence that a pattern occurred in the current reporting interval. Consult the source chat only when needed to verify a specific historical detail.

## Date, destination, and prior-session window

Map the session date to this structure, preserving lowercase English month names and ordinal day suffixes:

```text
therapy/<month_name>_<year>/<ordinal-day>/briefing.md
```

For example, `2026-10-14` becomes `therapy/october_2026/14th/briefing.md`; use `11th`, `12th`, and `13th` (not `11st`, etc.). Create a missing month directory, day directory, or `briefing.md`. Do not create unrelated placeholders.

Scan existing `therapy/**/briefing.md` files and any clearly equivalent dated session summaries, then find the most recent earlier session by declared `session_date` metadata or an unambiguous date in the path/content. Record the document's `prepared_on` date when available, but use chronological **session dates**, not file modification time, to establish which session was last or where the review interval begins. If an explicit previous-session date is supplied, use it unless the repository contains a clear contradiction; surface the discrepancy rather than silently choosing.

By default, include a concise, factual retrospective of relevant material dated after the previous session and before the target session, since this is the core purpose of the briefing. The user may ask to omit or narrow it. Exclude target-day material unless the user indicates it occurred before therapy. Determine source dates from explicit metadata/content or a date-bearing path, not modification time. Search relevant therapy reflections and notes; use existing topic summaries to limit duplication. If there is no verifiable earlier briefing, state that the prior-session boundary is unknown and identify date coverage only if helpful. Do not claim to summarize “since last session” when the boundary cannot be established. This retrospective is context, not a test of progress or a prompt to discuss every event.

If a retrospective is included, state its interval and any material coverage gaps. Historical context can clarify the user's established preferences, but must not be presented as an event from the interval.

## Analysis and drafting method

1. **Establish what the user wants from this document.** Use an aim only if the user provides or requests one; do not infer a standing goal from prior notes.
2. **Select only useful context.** For each included event, retain source/date, observable event, the user's stated meaning/feeling/body cue, and response when relevant. Distinguish report, interpretation, clinical lens, inference, and unknown. Do not create a comprehensive record or pressure the user to recount events.
3. **Preserve both perspectives accurately.** The user’s reported intention to understand and avoid harm is a good-faith statement of intent, not proof of impact. Include a partner's perspective only when directly provided; otherwise label it `not available in these sources`. Do not infer the partner's motives, neurotype, emotions, attachment response, or capacity.
4. **Use formulations as questions.** Where useful, offer one or two evidence-aware possible lenses (for example, an interaction cycle, capacity/overload, emotion regulation, or neurodivergent communication mismatch) and ask whether they fit. Do not present a diagnosis, a precise neurochemical/autonomic chain, or a trauma cause as established by notes. Keep language understandable and avoid making the briefing sound like a clinical report written to overrule the therapist.
5. **Do not assess progress by default.** Do not compare performance across sessions, assign a score, or frame change as expected. Reflect change only if the user asks or it is needed to accurately summarize a specific event; keep the wording neutral and do not imply success/failure.
6. **Keep topics and actions optional.** If the user wants an agenda, help select topics and questions. Do not impose a topic count, require a takeaway, or propose homework/experiments unless the user asks; frame suggestions as choices to discuss, not assignments.
7. **Write the briefing in English**, consistent with repository-wide language directives, even if source notes are in another language. Use the user's direct, adult style: specific, calm, respectful, non-sentimental. Reflect what is hard without generic comfort or pressure to resolve it.

## Output file and template

If requested, write or update `briefing.md` with a concise, readable session brief. There is no length, completeness, or preparation target. Include only details the user wants or that materially serve the stated request. Omit sections that are not useful.

```markdown
# Therapy briefing — YYYY-MM-DD

> Session date: YYYY-MM-DD — Prepared on: YYYY-MM-DD (optional metadata)
> Previous briefing: YYYY-MM-DD | not found
> Source window: YYYY-MM-DD to YYYY-MM-DD (only when a retrospective was requested)

## What I may want from this session (optional)
Include only if the user has named an aim or wants help shaping one.

## Context since the last session (optional or omit on request)
Selected dated events only; separate reports from interpretations. This is background, not a performance review or an expectation that the user discuss every item.

## What I noticed (optional)
Include only what the user reported and wants to bring; do not assign mechanisms.

## A question I may want to explore (optional)
One tentative formulation only if useful. Partner perspective: directly reported / not available in these sources.

## Topics I may want to bring (optional)
No required number or priority order.

## Questions I may want to ask (optional)

## Anything about therapy I want to note (optional)
Include feedback or follow-up only when volunteered or requested. Do not add homework by default.

## Evidence and limits
Name a relevant clinical framework or cite a directly relevant source only when it clarifies a question. State whether it is research, a model lens, or an inference; it does not establish the user's diagnosis or determine what happened.
```

The template is entirely optional, not a checklist or standard to meet. Do not create empty headings or clinical terminology for appearance. A very short note—or no note—is valid.

## Existing content and optional files

- If the target briefing is missing, create it. If it exists, inspect it first and preserve meaningful user-authored content. Update a clearly generated draft in place; if authorship or intended meaning is ambiguous, append a clearly dated addendum or ask before replacing material.
- Additional files such as `user-feedback.md` or a topic note are not expected. Create one only if the user requests it or it materially improves the specific task. Do not create a progress log or tracker unless explicitly requested. Keep source/feedback attribution and dates, and link any additional file from `briefing.md`.
- Never modify raw notes or historical source files. For a canonical daily bundle, read its existing `agentic/summary.md` and relevant topic outputs alongside only the source material needed; if substantive analysis of raw daily notes is needed and those outputs are missing, follow the facade's daily-bundle workflow. For a non-bundle note that this workflow substantively analyzes, create or update the required sibling `<note-stem>-analysis.md` (preserving user-authored content); if an adequate sibling analysis already exists, use it rather than duplicating it. This does not register `therapy-summarise` as a facade route.
- Do not write an additional “analysis” file automatically. The `briefing.md` is the default output; avoid duplicating a short synthesis in multiple places.

## User-specific guardrails

- The user reports wanting a meaningful future, direct two-way communication, explicit needs and intentions, and repair instead of unnecessary conflict. Present these as his stated aims; do not assert that the partner has confirmed them.
- Historical context also reports needs around a stable safe home, recognition of effort, warmth/touch/desire, feeling welcomed and cared for after hard work, sensory/processing space, and mutual co-regulation. Bring these forward only when relevant to the dated material; translate them into specific, negotiable behaviors and preserve consent and each partner's autonomy.
- He describes dry/blunt delivery, possible neurodivergent social processing, stomach clenching, “hot anvil,” defensiveness, a somewhat raised voice, and stronger gestures under escalation. Use only cues supported by the dated material. These are not sufficient for a diagnosis or an autonomic-state determination.
- The historical “Professional Contractor”/intellectualization formulation may help name a shift from felt experience to abstraction. It must remain a working metaphor/model, not an identity imposed on the user. If current distress is explicit, one respectful prompt about immediate bodily experience may be useful; do not mechanically “stop” him or force somatic focus.
- Where escape behavior appears, describe its possible short-term regulatory function and its impact on trust, boundaries, consent, and the partner. Neither biological hypotheses nor moral condemnation alone are adequate.
- The user values accurate understanding and visible help. Reflect the specific issue clearly; provide a next step only if asked for or plainly useful, and present it without expectation that the user act on it.
- Do not script the therapist as incompetent or prescribe EFT, IFS, Somatic Experiencing, or any other modality. Phrase modality questions as options to discuss and leave assessment to the clinician.

If the material indicates immediate danger, coercion, violence, self-harm, suicidality, or risk to another person, do not bury it in a routine briefing. Surface the concern accurately and recommend timely qualified or emergency support as appropriate.
