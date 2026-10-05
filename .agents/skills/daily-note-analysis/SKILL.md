---
name: daily-note-analysis
description: Analyze personal daily notes, reflections, and updates for body signals, unmet needs, and defensive intellectualization. Use for self-reflection; not for diagnosis or crisis care.
---

# Daily note analysis

## Canonical daily-note bundle

New daily notes use a dated bundle under `notes/<month_year>/<YYYY-MM-DD>/`:

```text
notes/october_2026/2026-10-05/
├── personal/
│   └── day-note.md
└── agentic/
    └── analysis.md
```

When analyzing a bundle:

1. Read `personal/day-note.md` first; it is the primary daily source.
2. Read every note file found anywhere under that bundle's `personal/` directory in deterministic path order. Treat additional personal files as supplementary evidence, never as a replacement for `day-note.md`.
3. Write or update the generated result in the matching `agentic/analysis.md` file. Never overwrite files under `personal/`.
4. If all personal files are empty, state `[Status]: no source content available` and do not infer a psychological, relational, medical, or engineering state.
5. Keep project or contextual documents outside `personal/` separate unless an applicable skill explicitly requires them.

Legacy files (`YYYY-MM-DD-notes.md`, `YYYY-MM-DD/notes.md`, `personal-notes.md`, and top-level `agentic-analysis.md`) remain read-compatible for migration but must not be created for new dates. For non-bundle note files, preserve the repository's sibling `<note-stem>-analysis.md` artifact rule.

### Description & Goal
Process daily notes, phone logs, reflections, and user updates. Goal: extract raw body signals, identify hidden underlying needs, and spot moments where the defensive mask took control.

### Execution Workflow:
1. **Extract Somatic Markers:**
   * Scan for symptoms: "anvil", stomach clenching, paralysis, fatigue, dopamine crash.
   * Identify Autonomic State: *Sympathetic (fight/flight)* vs *Dorsal Vagal (freeze/shutdown)* vs *Ventral Vagal (safe/social)*.
2. **Identify Defensive Masks & Intellectualization:**
   * Does the note contain excessive psychological jargon used defensively?
   * Is the relationship described from an external "observer/contractor" stance?
3. **Analyze Unmet Needs:**
   * Directly state what was missing (e.g., desire, appreciation after work, safe touch, clear communication without leaks).
4. **Output Schema:**
   * **[Somatic Signal]:** Physical state of the body.
   * **[Nervous System State]:** Window of tolerance status (Exceeded / In Range).
   * **[Defensive Shield]:** Was intellectualization triggered?
   * **[Primary Need]:** Explicitly named without sugarcoating.
   * **[Grounding Action]:** 1 immediate physical step.

## Extended machine-use output

Add these fields when the note contains relational, romantic, or consequential material:

* **[Evidence Status]:** `report`, `observation`, `framework lens`, `inference`, or `unknown`.
* **[Trigger and Interpretation]:** What happened and what meaning the body assigned to it.
* **[Protective Move]:** Pursuit, withdrawal, intellectualization, phone escape, shutdown, or another observable response.
* **[Partner Data]:** Direct words/actions only; otherwise write `UNKNOWN`.
* **[Short-Term Payoff / Relational Cost]:** What the move solved immediately and what it damaged or complicated later.
* **[Next Experiment]:** One bounded, observable action for the next interaction.

Do not turn a note into a prosecution brief against either partner. Keep reported experience, inference, and missing data separate.
