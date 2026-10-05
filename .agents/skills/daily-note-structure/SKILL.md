---
name: daily-note-structure
description: Idempotently initialize the repository's dated daily-note bundle with a summary, topic outputs, and raw personal input.
---

# Daily note structure

Use this skill when the user asks to create or check the note bundle for a date. The primary generated pattern is one short general summary plus separate, visible files for each applicable topic.

## Canonical structure

For a valid date `YYYY-MM-DD`, place the bundle under `notes/<lowercase-month>_<year>/<YYYY-MM-DD>/`:

```text
notes/october_2026/2026-10-05/
├── personal/
│   └── day-note.md             # human-authored source
└── agentic/
    ├── summary.md              # always: overview and links to topic outputs
    ├── personal.md             # emotional analysis and rational support
    ├── relationships.md        # when relationship content is present
    ├── engineering.md          # when engineering/business content is present
    ├── support.md              # concrete, usable aid
    └── others/                 # additional topic/source analyses when needed
```

`personal/day-note.md` is raw user input. `agentic/personal.md` is generated emotional analysis; the names are intentionally distinct.

## Initialization behavior

1. Require a valid ISO date and resolve every target relative to the repository root.
2. The required starter set is `personal/day-note.md`, `agentic/summary.md`, `agentic/personal.md`, and `agentic/support.md`. Create ready-to-use `relationships.md` and `engineering.md` topic files as well, matching the current bundle convention. Create `agentic/others/` for additional topic analyses.
3. If the complete structure already exists, return `NO_OP` without changing file contents or timestamps.
4. If it is partial, create only missing directories and files. Never overwrite or reformat any existing file.
5. Newly created outputs contain only a title with the requested date and `[Status]: pending source note`; do not invent note content or analysis.
6. Report the status (`CREATED`, `COMPLETED_PARTIAL_STRUCTURE`, or `NO_OP`) and paths created.

The general generated overview is `agentic/summary.md`. Do not create `agentic/analysis.md` for new bundles; it is a legacy-compatible name only. Do not delete or rename legacy files such as `personal-notes.md`, `agentic-analysis.md`, `analysis.md`, or `YYYY-MM-DD-notes.md`.

## Analysis ownership

- [`daily-note-analysis`](../daily-note-analysis/SKILL.md) is the facade that coordinates the applicable analysis skills and maintains the summary/index.
- [`emotional-analysis`](../emotional-analysis/SKILL.md) owns `agentic/personal.md`.
- [`relationship-analysis`](../relationship-analysis/SKILL.md) owns `agentic/relationships.md` when relevant.
- [`engineering-design-skill`](../engineering-design-skill/SKILL.md) owns `agentic/engineering.md` when relevant.
- [`actionable-support`](../actionable-support/SKILL.md) owns `agentic/support.md`.
- Other applicable skills may add clearly named files under `agentic/others/`.

Structure creation itself performs no analysis. An empty source note means only that no source text is available; it says nothing about the user's emotional state.
