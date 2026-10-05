---
name: daily-note-analysis
description: Orchestrate daily-note analysis across emotional, relationship, overload, escape, engineering, and other relevant skills; write a concise summary and topic-specific outputs.
---

# Daily note analysis

This is the facade and entry point for analysis of any source under `notes/`, not only daily-note bundles. Use it to select, coordinate, and connect the specialist skills. When the process needs to expand, add the specialist skill, link it, and define its trigger and output ownership in the routing map below; do not duplicate its full method here.

## Canonical daily bundle

```text
notes/<month_year>/<YYYY-MM-DD>/
├── personal/day-note.md
└── agentic/
    ├── summary.md
    ├── personal.md
    ├── relationships.md       # when relevant
    ├── engineering.md         # when relevant
    ├── support.md
    └── others/                # additional topic/source analyses
```

The primary pattern is a general summary plus individual analyses for topics that actually occur in the source. `personal/day-note.md` is user-authored input; `agentic/personal.md` is generated emotional analysis. The summary is an index and synthesis, not a replacement for topic files.

Read every note file recursively under the date bundle's `personal/`, with `personal/day-note.md` first, then deterministic path order. Never write into or overwrite source files. Keep documents outside `personal/` out of the evidence set unless the user or a relevant skill explicitly makes them context.

## Skill routing

For a non-empty bundle, always invoke:

- [`emotional-analysis`](../emotional-analysis/SKILL.md) for the user's emotional experience and rational, accurately understood response; write its result to `agentic/personal.md`.
- [`actionable-support`](../actionable-support/SKILL.md) to identify whether a concrete, user-usable aid is warranted; write it to `agentic/support.md`, including a concise no-action-needed status when appropriate.

Invoke additional skills only when source material warrants them, for both canonical bundles and standalone notes:

| Note signal | Specialist skill | Daily-bundle output |
|---|---|---|
| Romantic interaction, conflict, desire, boundary, repair | [`relationship-analysis`](../relationship-analysis/SKILL.md), with [`emotional-analysis`](../emotional-analysis/SKILL.md) | `agentic/relationships.md` |
| Misunderstanding, ambiguous intent, direct/blunt wording, or escalating communication | [`relationship-communication`](../relationship-communication/SKILL.md), with [`relationship-analysis`](../relationship-analysis/SKILL.md) and [`emotional-analysis`](../emotional-analysis/SKILL.md) | `agentic/relationships.md`; put a concise usable script in `agentic/support.md` when warranted |
| Body overload, “hot anvil,” stomach clenching, shutdown, reduced capacity | [`nervous-system-overload-analysis`](../nervous-system-overload-analysis/SKILL.md), with [`emotional-analysis`](../emotional-analysis/SKILL.md) | Contribute to `agentic/personal.md`; do not compete for ownership of the file |
| Flirting, sexting, validation-seeking, phone escape, secrecy or repair impact | [`safety-escape-mechanism-analysis`](../safety-escape-mechanism-analysis/SKILL.md), with [`emotional-analysis`](../emotional-analysis/SKILL.md); also [`relationship-analysis`](../relationship-analysis/SKILL.md) when relational | Contribute to `agentic/relationships.md` if relational, otherwise `agentic/personal.md` |
| Software, architecture, development, business, cost, automation | [`engineering-design-skill`](../engineering-design-skill/SKILL.md); add [`emotional-analysis`](../emotional-analysis/SKILL.md) only if personal affect or distress is also present | `agentic/engineering.md` |
| Another distinct subject | Relevant available skill; if none fits, use careful general analysis and label uncertainty | A named file under `agentic/others/` |

Always use [`daily-note-structure`](../daily-note-structure/SKILL.md) to initialize a requested date bundle. The routing and evidence rules in this skill are sufficient to operate without historical notes. Files such as `notes/historical/gemini/internal-struggle-context.md`, `relationship-context.md`, and `engineering-context.md` are optional historical, user-reported context: consult them only when present and relevant, and never treat them as evidence about today's events.

## Workflow and evidence discipline

1. Establish whether personal source files contain text. If all are empty, write a short `[Status]: no source content available` in `agentic/summary.md`; do not manufacture personal or topic analyses. Preserve empty source files.
   If the user supplies the note content directly and no source file is available, apply the same routing and evidence rules to that supplied content. If neither a source file nor source text is available, state that analysis cannot be grounded yet; do not infer content from profile or historical context. Do not create a missing input file or unrelated output artifact unless the user requests it.
2. Extract only what is present: reported events, sensations, emotions, interpretations, needs, actions, outcomes, and explicit requests. Distinguish report, observation, framework lens, inference, and unknown.
3. Select specialist skills using the routing table. Read their current `SKILL.md` instructions before using them. Preserve each skill's evidence and safety limits.
4. Produce topic documents first. `summary.md` then records the concise synthesis, key uncertainties, and links to only the topic files that have substance. Keep distinct topics separate rather than merging them into one long essay.
5. Make the work useful: include an actual next step or practical artifact when supported by the notes; otherwise say none is warranted.

Never infer a diagnosis, exact autonomic or neurotransmitter mechanism, the absent partner's mental state, or the user's intention from profile context alone. The user's self-reported AuDHD/ASD context, “hot anvil,” Contractor-style intellectualization, relationship aims, and escape-function formulation are hypotheses/context to test against current text, not templates to force onto every date.

For a standalone note, keep the source readable, run this same routing process, and combine the applicable specialists' findings in one sibling `<note-stem>-analysis.md`. Do not create a separate bundle or new legacy flat formats unless requested. For new daily dates, use the canonical bundle instead.
