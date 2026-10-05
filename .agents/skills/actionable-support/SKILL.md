---
name: actionable-support
description: Turn a well-understood problem into one concrete, low-friction aid the user can use now, such as a script, decision aid, checklist, or next action.
---

# Actionable support

Use this skill after understanding the user's actual problem when the user asks what to do, is stuck, or the source supports a practical next move. In daily bundles, this skill owns `agentic/support.md`. `daily-note-analysis` routes substantive daily analyses through this skill to check for visible, usable help; it may conclude that no action is warranted.

## Standard

The output must give the user something usable outside the analysis: a short message draft, a bounded next step, a checklist, a decision table, a small implementation ticket, a pause-and-return script, or a prepared therapy agenda. Choose the smallest aid that addresses the demonstrated constraint. Do not produce an action list just to make an answer appear useful.

## Workflow

1. State the concrete problem as understood, using the user's facts and separating unknowns.
2. Check capacity. If the user reports acute overload, use [`nervous-system-overload-analysis`](../nervous-system-overload-analysis/SKILL.md) and restrict the artifact to one safe grounding/pause action until capacity improves.
3. Select one aid that matches the problem:
   - emotional overload: one orienting or grounding step and a simple return condition;
   - relationship communication: one short consent-respecting request, reflection prompt, or pause/return-time script;
   - escape behavior: a feasible alternative that can interrupt the same short-term function, plus any needed truth/repair action;
   - engineering/business: a bounded next implementation slice with owner, acceptance check, and stop condition;
   - therapy preparation: a concise, evidence-labeled summary and a few questions for the clinician.
4. Make the aid specific, ready to use, and proportionate. Include the first physical or verbal action and when to reassess. Preserve the user's agency; present a proposal, not a command.
5. If no safe, evidence-supported action is available, say what information is missing and ask one focused question or state that no action is warranted.

## Quality and safety

- No generic affirmations, moralizing, diagnoses, or overconfident predictions.
- Do not write messages that attribute motives to an absent person. Relationship drafts should state the user's observation, feeling/need, request, and openness to the other person's account.
- Do not advise irreversible decisions while the user reports severe overload. Do not make a partner responsible for co-regulating the user.
- For engineering, do not trigger external actions, deploy, contact people, or change live systems as part of an aid unless separately authorized.
- An empty note produces no invented problem or action.

## Daily bundle output

Write `agentic/support.md`:

```text
[Status]: actionable aid | no action warranted | source insufficient
[Problem understood]
[Usable aid]
[First step]
[Reassessment / stop condition]
```

Keep the aid concise enough to copy, send, perform, or bring to a conversation. Do not repeat all analysis from `personal.md`, `relationships.md`, or `engineering.md`.

## Evidence note

Structured problem-solving is a studied clinical approach, but evidence for therapy is not evidence that every ordinary difficulty needs a problem-solving intervention. An updated meta-analysis of problem-solving therapy for adult depression found small effects comparable to other psychological treatments in lower-bias studies; use its structured sequence as a modest design reference, not as a promise of benefit in this setting: [Cuijpers et al. (2018)](https://pubmed.ncbi.nlm.nih.gov/29331596/).
