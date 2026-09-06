# Worked Example (Opposite Tier) — A Vibe Basic Build

The [primary worked example](worked-example.md) runs an idea to **Full Spec-Driven**. This one takes a deliberately simple idea to the *other* end of the spectrum, so the range of the framework is visible side by side.

---

## The raw idea

> "I want an agent that takes my rough daily notes and turns them into a clean bulleted standup update I can paste into chat each morning."

---

## Step 1 — Intake

| Question | Answer | Signal |
|----------|--------|--------|
| Multi-step workflow? | No — one transform: notes in, bullets out | Points to Vibe |
| Multiple SOPs / reference docs? | No — maybe one short format example | Points to Vibe Basic |
| Drift consequences? | None — a clumsy bullet is mildly annoying, nothing more | Confirms low stakes |

## Step 2 — Classify

```
Multi-step? NO
  → Multiple SOPs / reference docs? NO
    → Vibe Basic
```

**Tier: Vibe Basic.** Single transform, single user, zero compliance exposure, drift is cosmetic. Wrapping this in phase gates or an authority model would be pure overhead.

## Step 3 — Design (three phases)

**Phase 1 — Define role**
- Role: a standup-formatting assistant.
- Scope — *does*: reformat notes into Yesterday / Today / Blockers bullets. *Does not*: invent status, chase people, or track tickets.
- Boundaries: never fabricate progress that isn't in the notes; keep it under ~8 bullets.
- Output format: three headed sections, terse bullets, no preamble.

**Phase 2 — Attach knowledge**
- One optional reference file: a single example of a "good" standup update to anchor tone. Nothing more.

**Phase 3 — Ship and iterate**
- Use it every morning. When it drifts (e.g. it starts padding with filler), add one boundary line and move on.

## Step 4 — Deliver

Fill the [Vibe instruction template](../templates/vibe-instruction-template.md):

```
ROLE: You are a standup-formatting assistant.

SCOPE:
- Does: reformat rough notes into Yesterday / Today / Blockers bullets
- Does Not: invent status, track tickets, or contact people

BOUNDARIES:
- Never state progress not present in the notes
- Max ~8 bullets total

OUTPUT FORMAT:
- Three headed sections; terse bullets; no preamble

REFERENCE FILES:
- standup-example.md: one model update for tone
```

Deploy in minutes. No architecture conversation, no gates, no reference hierarchy.

---

## The contrast

| | Vibe Basic (this doc) | Full Spec-Driven ([other doc](worked-example.md)) |
|---|---|---|
| Trigger | One transform | Multi-step review pipeline |
| Failure cost | Cosmetic | A signed, incorrect attestation |
| Design time | Minutes | Hours to days |
| Reference docs | Zero to one | Four layered documents |
| Authority model | None needed | Explicit autonomous / escalate / deny |

Same builder, same afternoon — two completely different agents. Picking the right tier *first* is what keeps the simple one cheap and the risky one safe.
