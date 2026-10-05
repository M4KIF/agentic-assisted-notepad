---
name: update-skills
description: Review the repository's analysis skills against the previous seven days of notes, learn recurring needs and drift, propose precise skill updates, and apply them only after explicit user approval.
---

# Update skills

Use this skill for the repository's weekly or explicitly requested skill review. It is a gated learning-and-proposal workflow. The skill must never silently modify another skill.

## 1. Purpose

Skills are working instruments, not static doctrine. Human needs, language, relationship patterns, engineering decisions, and safety boundaries evolve through notes. This workflow studies the recent record, checks what each skill actually claims and enforces, and proposes only updates supported by recurring or consequential evidence.

The required learning window is the seven calendar days ending on the current date. If the repository uses a different timezone or the current date is ambiguous, state the assumption. Include only files under `notes/` whose dates fall in that window; do not infer dates from file modification time alone when a note filename or content provides a clearer date. `notes/` may be empty or unavailable: record the resulting evidence gap, do not invent learning signals, and continue the skills-truth review. In that case, do not propose user-pattern changes on the basis of absent notes; request source material only if it is necessary to evaluate a specific proposed change.

## 2. Skills and context to inspect

Read every installed local skill under `.agents/skills/*/SKILL.md`, including:

- `daily-note-analysis`
- `daily-note-structure`
- `emotional-analysis`
- `actionable-support`
- `nervous-system-overload-analysis`
- `relationship-analysis`
- `relationship-communication`
- `safety-escape-mechanism-analysis`
- `engineering-design-skill`
- `therapy-summarise`
- this `update-skills` skill

Read applicable repository instructions and context when available:

- `AGENTS.md`
- `notes/AGENTS.md` if present
- `notes/historical/gemini/chat.md` and `chat-analysis.md`
- `notes/historical/gemini/internal-struggle-context.md`
- `notes/historical/gemini/relationship-context.md`
- `notes/historical/gemini/engineering-context.md`

The historical files are optional user-reported context, not prerequisites. If absent or unreadable, rely on the current skills, repository instructions, and available dated source material; never infer their contents. If `notes/` contains no files in the review window, say so explicitly and do not treat older history as evidence of a new development in that window.

For canonical daily bundles, `daily-note-analysis` reads every file under `personal/`, with `personal/day-note.md` first, routes to topic skills, and writes `summary.md` plus relevant topic files. Non-bundle note analysis produces a sibling `<note-stem>-analysis.md` artifact. Do not analyze ignored notes by modifying their source content unless explicitly asked.

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

The proposal must be understandable without requiring the user to reconstruct the seven-day notes. Keep quotations short and prefer precise paraphrase. Link each proposed update to the relevant skill and note artifact when one exists; otherwise state that no supporting note artifact was available and distinguish the proposal's basis (for example, a current user instruction or an internal inconsistency).

## 5. Apply pass — only after explicit agreement

Apply changes only after the user explicitly confirms that the proposal is fitting. “Continue,” “sounds good,” or an ambiguous response is not enough if multiple edits or material behavioral changes are proposed; ask which proposal is approved.

After approval:

1. Re-read the approved target skills and the proposal.
2. Apply the smallest patch that implements the approved wording.
3. Preserve unrelated directives, metadata, invocation policy, and user authorization boundaries.
4. Validate frontmatter, names, links, placeholders, and internal references.
5. Re-read the changed skills end-to-end and summarize the exact behavioral change.
6. Only when at least one approved change was applied, record the review window, approval, changed files, rationale, and deferred proposals in a dated changelog file. The changelog is not a prerequisite for review or proposal: if `.agents/skills-changelog/` is absent, create it during this apply step. Do not create the directory or a changelog file for a no-op review. Use one file per approved apply, dated in `Europe/Warsaw`: name the first file `YYYY-MM-DD-changelog.md`, then use `YYYY-MM-DD-changelog-1.md`, `YYYY-MM-DD-changelog-2.md`, and so on for additional files that day. Check for collisions and never overwrite an existing file. Keep changelogs in this gitignored directory, not under `notes/`.

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
