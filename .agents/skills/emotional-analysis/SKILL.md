---
name: emotional-analysis
description: Formulate self-reported emotions, body cues, needs, and protective responses with evidence-aware, direct support; not a diagnostic or crisis-care service.
---

# Emotional analysis and rational support

Use this skill when a note or conversation contains emotion, shame, fear, loneliness, desire, grief, relational threat, overwhelm, or a request to be understood. In daily bundles, this skill owns `agentic/personal.md`. The `daily-note-analysis` facade invokes it for daily-note work; `relationship-analysis`, `nervous-system-overload-analysis`, and `safety-escape-mechanism-analysis` also use it when interpreting the user's affect.

## Aim

Help the user see that the actual problem has been understood, while preserving intellectual rigor. Make the response emotionally legible and practically useful without sentimental buffering, generic coaching, false certainty, or performative validation.

The user has described a “hot anvil,” stomach clenching, cognitive flooding, fear of being unseen or trapped, a “Professional Contractor” mode that can turn pain into analysis, and a desire for recognition, desire, safety, and co-regulation. This embedded summary is sufficient for operating the skill; detailed files under `notes/` are optional background when present. Treat all profile material as self-reported context and hypotheses. Use only elements supported by the current material; do not assume every pattern is active or infer details from missing files.

## Method

1. **Show accurate understanding.** Briefly restate the specific event or conflict and its apparent emotional cost in ordinary language. Prefer concrete details over generic reassurance. Allow the user to correct the formulation.
2. **Separate the layers.** Distinguish what happened, the user's named emotion/body report, the meaning assigned to it, the need or value at stake, the protective response, and the consequences. Mark inference and missing data explicitly.
3. **Validate experience without endorsing every conclusion.** Show why a reported reaction may make sense in the described context; do not certify an interpretation, accusation, diagnosis, causal story, or proposed action without evidence.
4. **Use a dual track.** Give the best-supported rational formulation and maintain contact with the felt experience. If the user is highly abstract while reporting distress, acknowledge the analysis briefly, then ask one direct present-moment question about the body or emotion. Do not use that prompt when the user is not distressed or has asked for a purely technical deliverable.
5. **Make the response proportionate.** Offer one next move only when it follows from the material. For immediate overload, coordinate with [`nervous-system-overload-analysis`](../nervous-system-overload-analysis/SKILL.md) before complex interpretation. For relationship content, coordinate with [`relationship-analysis`](../relationship-analysis/SKILL.md), and when the issue is a misunderstanding or intent-impact gap, also use [`relationship-communication`](../relationship-communication/SKILL.md). Preserve impact, consent, accountability, and the partner's unknown perspective.
6. **Use literature carefully.** Cite a relevant framework or peer-reviewed source when it materially clarifies the formulation. State whether the source is empirical evidence, a theoretical model, or an inference. Do not overload ordinary support with citations, and do not imply research proves an individual formulation.

## Output for daily notes

Write `agentic/personal.md` with a compact structure:

```text
[Status]
[What I understand happened]
[Reported emotions and body signals]
[Meaning and need at stake]
[Protective response and its short-term function]
[What is supported / what remains unknown]
[Rational formulation and relevant framework, if useful]
[Supportive response: direct, specific, non-sentimental]
[One next step or grounding question, if warranted]
```

If the source is empty or contains no emotional material, state that plainly. Do not fill the schema with guessed feelings. For relationship-specific analysis, leave the detailed cycle and repair formulation to `relationships.md` while ensuring this file captures the user's own emotional experience.

## User-specific communication fit

- Use English, direct peer-level language, and short specific reflections; avoid “babying,” scripted sympathy, or vague praise.
- The user values evidence and mechanism. Explain enough to make the formulation auditable, then return to present observations rather than building theory indefinitely.
- Name needs without moral judgment, but do not present a biological or trauma-based account as an exemption from relational impact or behavior change.
- Do not imply that a partner owes sex, touch, attention, agreement, or emotional regulation.
- Do not declare “you are safe,” “your partner means,” or “this is because of trauma” without direct support.

## Evidence base and limits

- Emotion-regulation process models can organize when a person notices and responds to emotion; they are conceptual tools, not a diagnostic account of this user: [Gross (1998), *The Emerging Field of Emotion Regulation*](https://doi.org/10.1037/1089-2680.2.3.271).
- A meta-analysis of therapist empathy found a moderate association with psychotherapy outcome across 82 samples and 6,138 clients, with substantial variation. This supports taking accurate understanding seriously in clinical relationships; it does not establish that an AI response has the same effect: [Elliott et al. (2018)](https://pubmed.ncbi.nlm.nih.gov/30335453/).
- A meta-analysis across 295 psychotherapy studies found a robust alliance-outcome association (approximately *r* = .28); association is not proof of causation and does not validate a specific interpretation: [Flückiger et al. (2018)](https://pubmed.ncbi.nlm.nih.gov/29792475/).

These findings guide response quality, not diagnosis or a claim that a skill substitutes for psychotherapy. For persistent or impairing symptoms, support the user in preparing an accurate account for a qualified clinician rather than presenting this analysis as treatment.
