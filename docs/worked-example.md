# Worked Example — A Raw Idea, End to End

This walkthrough runs a single agent idea through the full framework: intake → classify → design → deliver. It shows how the tree turns a vague concept into a concrete build plan.

---

## The raw idea

> "I want an agent that reviews incoming vendor security questionnaires, checks the answers against our control baseline, flags gaps, and drafts a response memo for the security team to sign off."

---

## Step 1 — Intake

Answer only the branch questions the tree needs:

| Question | Answer | Signal |
|----------|--------|--------|
| Multi-step workflow? | Yes — review, compare, flag, draft | Points to Spec |
| Does drift have material consequences? | Yes — a missed gap becomes a signed, incorrect attestation | Points to Spec |
| Compliance requirement or multiple stakeholders? | Yes — security team signs off; tied to a control baseline | Points to Full Spec |

## Step 2 — Classify

Walking the tree:

```
Multi-step? YES
  → Material drift consequences? YES
    → Compliance / multiple stakeholders? YES
      → Full Spec-Driven
```

**Tier: Full Spec-Driven.** The deciding factors: a wrong output gets *signed* (material consequence) and it is consumed by a review team against a formal baseline (compliance + stakeholders).

## Step 3 — Design (four phases)

**Phase 1 — Architecture conversation**
- Problem: reduce manual questionnaire review time while preventing missed control gaps.
- Stakeholders: security reviewer (signs), requesting vendor manager (consumes), auditor (may inspect trail).
- Adjacent systems: control-baseline document store, ticketing system.
- Success: every answer mapped to a control; every gap flagged with severity; memo matches the approved template.
- Failure modes: false "compliant" (worst case), missing citation, memo format drift.

**Phase 2 — Boundaries**
- Autonomous: mapping answers to controls, flagging gaps, drafting the memo.
- Escalate: final sign-off, any answer it cannot map with confidence.
- Deny: marking a questionnaire "approved" — that authority stays human.

**Phase 3 — Layer reference docs**

| Layer | Document |
|-------|----------|
| Methodology | Questionnaire review playbook (how to map answer → control) |
| Operational guide | Step sequence: parse → map → score gap severity → draft |
| Domain data | Control baseline, severity rubric |
| Output spec | Response memo template |

**Phase 4 — Architect instructions**
- Identity: vendor questionnaire review assistant, advisory authority only.
- Document hierarchy: methodology > operational guide > domain data > output spec.
- Workflow with gates:
  - Parse → *gate: every question extracted*
  - Map to controls → *gate: every answer mapped or escalated*
  - Score gaps → *gate: each gap has a severity*
  - Draft memo → *gate: matches output spec exactly*

## Step 4 — Deliver

Fill the [Spec-Driven instruction template](../templates/spec-instruction-template.md) with the above, outline the four reference docs, and recommend connectors (document store + ticketing).

---

## The counter-case

If the same person had asked for *"an agent that logs what vendors I contacted today in a running list"* — single step, no baseline, output consumed only by them, drift merely annoying — the tree lands on **Vibe Basic**, and the [Vibe template](../templates/vibe-instruction-template.md) is the right starting point. Same domain, completely different build. That is the entire point of tiering.
