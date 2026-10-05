---
name: daily-note-structure
description: Idempotently initialize the canonical dated personal-note bundle with personal/day-note.md and agentic/analysis.md.
---

# Daily note structure

Use this skill when a dated daily-note bundle must be created or checked. It creates the canonical structure without overwriting existing user content.

## Canonical structure

For a requested date `YYYY-MM-DD`, use the repository's month directory convention, for example:

```text
notes/october_2026/2026-10-05/
├── personal/
│   └── day-note.md
└── agentic/
    └── analysis.md
```

The month directory is lowercase `<month>_<year>` and the date directory is ISO `YYYY-MM-DD`.

## Invocation contract

1. Require one valid date argument in `YYYY-MM-DD` format.
2. Resolve the target below `notes/`, relative to the repository root.
3. If both directories and both files already exist, return `NO_OP` and do not modify timestamps or contents.
4. If the structure is partial, create only missing directories and files; preserve every existing file byte-for-byte.
5. Do not delete, rename, migrate, or overwrite legacy files such as `personal-notes.md`, `agentic-analysis.md`, `notes.md`, or `YYYY-MM-DD-notes.md`.
6. Report the exact paths created and whether the result was `CREATED`, `COMPLETED_PARTIAL_STRUCTURE`, or `NO_OP`.

## Initial file templates

Only newly created files receive these minimal headings:

`personal/day-note.md`

```markdown
# Daily Note — YYYY-MM-DD

<!-- Write raw observations, events, body signals, needs, and decisions here. -->
```

`agentic/analysis.md`

```markdown
# Agentic Analysis — YYYY-MM-DD

[Status]: pending source note
```

The skill must not generate psychological, relational, medical, or engineering conclusions. Analysis is performed later by `daily-note-analysis` or another applicable skill.

## Safety and idempotency

- Reject invalid or ambiguous dates before creating anything.
- Keep human input and generated analysis in separate files.
- Never treat an empty `day-note.md` as evidence of an empty emotional state; report only that no source text is available.
- This skill creates local note structure only; it does not contact external systems, publish notes, or change repository policy.
