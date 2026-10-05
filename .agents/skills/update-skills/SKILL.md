---
name: update-skills
description: Review the repository's analysis skills against the previous seven days of notes, learn recurring needs and drift, propose precise skill updates, and apply them only after explicit user approval.
---

# Update skills

Use this skill for the repository's weekly or explicitly requested skill review. It is a gated learning-and-proposal workflow. The skill must never silently modify another skill.

## 1. Purpose

Skills are working instruments, not static doctrine. Human needs, language, relationship patterns, engineering decisions, and safety boundaries evolve through notes. This workflow studies the recent record, checks what each skill actually claims and enforces, and proposes only updates supported by recurring or consequential evidence.

The required learning window is the seven calendar days ending on the current date. If the repository uses a different timezone or the current date is ambiguous, state the assumption. Include only files under `notes/` whose dates fall in that window; do not infer dates from file modification time alone when a note filename or content provides a clearer date.

## 2. Skills and context to inspect

Read every installed local skill under `.agents/skills/*/SKILL.md`, including:

- `daily-note-analysis`
- `daily-note-structure`
- `nervous-system-overload-analysis`
- `relationship-analysis`
- `safety-escape-mechanism-analysis`
- `engineering-design-skill`
- this `update-skills` skill

Also read applicable repository context files, especially:

- `AGENTS.md`
- `notes/AGENTS.md` if present
- `notes/historical-context-chat-gemini.md`
- `notes/historical-context-internal-struggle.md`
- `notes/historical-context-relationship.md`
- `notes/historical-context-engineering.md`

Follow the repository rule that any non-bundle note analysis produces a sibling `<note-stem>-analysis.md` artifact. For canonical daily bundles, `daily-note-analysis` writes `agentic/analysis.md` and reads every file under `personal/`, with `personal/day-note.md` first. Do not analyze ignored notes by modifying their source content unless explicitly asked.

## 3. Learning pass

Before proposing edits:

1. Build the seven-day note inventory and record which canonical bundles, legacy files, personal files, generated analyses, missing files, empty files, ignored files, or unavailable files are present.
2. Extract recurring signals: body states, overload markers, defenses, relationship loops, romantic/sexual needs, escape functions, engineering decisions, business assumptions, safety risks, and communication corrections.
3. For each candidate insight, classify it as `recurring`, `consequential single event`, `uncertain`, or `unsupported`. Do not universalize a single unusual note.
4. Compare each candidate with the current skill. Record whether it is already covered, conflicts with a directive, fills a real gap, or belongs in a context file rather than a skill.
5. Check for overreach: diagnosis, moral judgment, false scientific certainty, partner-mind-reading, unstable prices/laws/API claims, or instructions that expand authority beyond the user's request.

## 4. Proposal output — mandatory stop point

Produce a proposal and stop. Do not modify any skill, `AGENTS.md`, context file, or source note during this pass. The proposal must contain:

```text
[Review window]: dates, timezone assumption, and files read
[Current skill truth]: what each relevant skill currently claims/enforces
[Observed changes]: recurring or consequential evidence from the window
[Proposed update]: exact wording or a minimal diff per skill
[Rationale]: which observations justify each change
[Evidence status]: report | observation | framework lens | inference | unknown
[Risk check]: overreach, contradiction, safety, privacy, or stale-fact risks
[No-change decisions]: skills reviewed but not changed, with reason
[Approval request]: ask the user to approve, reject, or amend the proposal
```

The proposal must be understandable without requiring the user to reconstruct the seven-day notes. Keep quotations short and prefer precise paraphrase. Link each proposed update to the relevant skill and note artifact.

## 5. Apply pass — only after explicit agreement

Apply changes only after the user explicitly confirms that the proposal is fitting. “Continue,” “sounds good,” or an ambiguous response is not enough if multiple edits or material behavioral changes are proposed; ask which proposal is approved.

After approval:

1. Re-read the approved target skills and the proposal.
2. Apply the smallest patch that implements the approved wording.
3. Preserve unrelated directives, metadata, invocation policy, and user authorization boundaries.
4. Validate frontmatter, names, links, placeholders, and internal references.
5. Re-read the changed skills end-to-end and summarize the exact behavioral change.
6. Record the review window, approval, changed files, and deferred proposals in a sibling update-analysis artifact or a clearly named changelog note. Do not rewrite source notes as part of skill maintenance.

## 6. Weekly reminder behavior

When operating under this repository's `AGENTS.md`, remind the user once per seven-day period to run:

`.agents/skills/update-skills/SKILL.md`

The reminder should be direct and brief. If no reliable record of the last reminder exists, say that the reminder date is unknown and offer the review. Do not claim to send a reminder outside an active interaction or create a scheduled job without explicit authorization.

## 7. Quality bar

- Update a skill only when the recent evidence changes a decision, workflow, safety boundary, or output quality.
- Prefer a narrow correction over accumulating universal rules.
- Keep context-specific facts in context files and reusable behavior in skills.
- For psychological material, distinguish reported experience from clinical evidence and model-specific language; never diagnose.
- For relationship material, preserve the absent partner's unknown perspective and keep impact, consent, boundaries, and repair visible.
- For engineering material, preserve explicit ownership, event contracts, human control, auditability, reversible actions, and current-fact verification.
- If the review finds no justified changes, say so and do not manufacture updates.
