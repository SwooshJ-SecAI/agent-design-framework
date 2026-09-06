# Agent Tiering Framework — Reference

The full methodology behind the decision framework: tier definitions, the two design approaches, phase requirements, checklists, and migration heuristics.

---

## Framework overview

| Dimension | Vibe Coding | Spec-Driven |
|-----------|-------------|-------------|
| Complexity | Single-concern, repeatable tasks | Multi-phase workflows, compliance-bound |
| Tolerance for drift | Acceptable; corrected iteratively | Unacceptable; prevented by architecture |
| Knowledge structure | Flat reference files | Layered document hierarchy |
| Iteration model | Use, find drift, add constraint | Architecture conversation, then build |
| Stakeholders | Typically single user | Multiple users, reviewers, auditors |
| Time to first deploy | Minutes to hours | Hours to days |

---

## Tier reference

The canonical definition of all four tiers. Every other section refers back to this.

| Tier | Approach | Scope profile | Governance |
|------|----------|---------------|------------|
| Vibe Basic | Vibe | Single task, single SOP, single user | Iterative constraint addition |
| Structured Vibe | Vibe | Single task, multiple SOPs, single user | Organized reference files, iterative refinement |
| Spec-Lite | Spec-Driven | Multi-step workflow, low compliance risk | Documented architecture, light gating |
| Full Spec-Driven | Spec-Driven | Multi-step, compliance-bound, multi-stakeholder | Full architecture conversation, layered docs, phase gates |

---

## Vibe Coding framework

Start with the minimum viable instruction set, deploy immediately, and let real usage surface gaps. Each observed drift becomes a constraint added until output stabilizes.

**Three phases**

1. **Define role** — role, scope, boundaries, output format in one declarative block.
2. **Attach knowledge** — SOPs, policies, templates, domain data as reference files (the agent's "memory").
3. **Ship and iterate** — use it, identify drift, add a constraint, repeat until stable.

**Iteration principle:** *Use it. Find drift. Add constraint. Repeat until stable.* Each iteration produces one of: a new boundary statement, a new reference file/SOP section, or a narrowed capability.

**Use Vibe Coding when:** single concern, drift is annoying not dangerous, no compliance/audit exposure, single owner, speed matters more than rigor.

---

## Spec-Driven framework

The specification is the source of truth. Architecture precedes implementation; every design decision is documented before the agent is built.

**Four phases**

1. **Architecture conversation** — problem, stakeholders, adjacent systems, success criteria, failure modes, compliance constraints. Output: an architecture brief.
2. **Define boundaries** — ownership, authority scope (autonomous vs. escalate), adjacent agent lanes, failure-mode handling. Output: a boundary spec.
3. **Layer reference docs** — build the knowledge hierarchy:

   | Layer | Purpose | Example |
   |-------|---------|---------|
   | Methodology | How work is performed | Investigation playbook, audit methodology |
   | Operational guide | Procedures and sequences | Triage process, evidence collection workflow |
   | Domain data | Facts and reference material | Control frameworks, risk registers, inventories |
   | Output spec | What deliverables must look like | Report templates, evidence formats |

4. **Architect instructions** — identity, authority, document hierarchy/precedence, workflow phases with gates, verification criteria.

**Quality bar:** *If generated output does not match the spec, the spec wins — regenerate to conform.* Applied at every gate; the agent does not advance until output meets that phase's spec.

**Use Spec-Driven when:** multi-step workflows with dependencies, compliance/regulatory/audit requirements, material drift consequences, multiple stakeholders, interoperation with other systems, reproducibility mandatory.

---

## Decision logic

```
START: What does this agent need to do?
  |
  +-- Multi-step workflow?
  |     +-- NO --> Multiple SOPs / reference docs?
  |     |            +-- NO  --> Vibe Basic
  |     |            +-- YES --> Structured Vibe
  |     +-- YES --> Drift has material consequences?
  |                   +-- NO  --> Spec-Lite
  |                   +-- YES --> Compliance req. or multiple stakeholders?
  |                                 +-- NO  --> Spec-Lite
  |                                 +-- YES --> Full Spec-Driven
```

### Decision factors

| Factor | Points toward Vibe | Points toward Spec-Driven |
|--------|-------------------|--------------------------|
| Number of workflow phases | 1–2 | 3+ |
| Stakeholder count | 1 | 2+ |
| Regulatory exposure | None | Any |
| Output consumers | Self only | Team, auditors, clients |
| Failure cost | Time lost | Compliance gap, financial loss |
| Interoperability needs | Standalone | Interfaces with other systems |
| Reproducibility requirement | Nice to have | Mandatory |

---

## Migration indicators

**Move up a tier when:**
- A Vibe agent accumulates more than 10 iterative constraints (hidden complexity).
- A Vibe agent's output is consumed by other people or systems.
- A Spec-Lite agent gains compliance requirements or begins interfacing with other agents.
- Any agent's failure mode shifts from "inconvenient" to "consequential."

**Move down a tier when:**
- A Spec-Driven agent's compliance requirements are retired.
- A Spec-Lite agent's workflow simplifies to a single phase.
- Stakeholder count drops to one with no external consumers.

---

## Key principles

1. **One agent, one concern.** If scope spans multiple domains, split into multiple agents with defined lanes. Start with the simplest tier that covers your risk profile.
2. **Authority before action.** Define what an agent can and cannot decide before specifying what it does.
3. **Documents over instructions.** Instructions define identity, hierarchy, and workflow; reference documents hold domain knowledge. Keep instructions lean.
4. **Instructions are architecture, not prompts.** For Spec-Driven agents, treat the instruction block with system-design rigor.
5. **Gates prevent drift by design.** Phase gates enforce quality at each transition rather than catching errors at the end.
6. **The spec is the source of truth.** When output diverges from spec, the spec wins. Always.
7. **Iterate deliberately.** Vibe agents improve through use (track constraints); Spec-Driven agents improve through document revision (version the docs).
8. **Lane boundaries prevent collision.** When multiple agents share a domain, define what each one does NOT do.
9. **Design for the failure mode, not the happy path.**

---

## Example tier mapping (illustrative)

Generic examples showing how common agent types map to tiers — not a specific organization's inventory.

| Agent type | Tier | Rationale |
|------------|------|-----------|
| Daily task logger | Vibe / Structured Vibe | Single concern, iterative refinement, no compliance exposure |
| Periodic review assistant | Vibe / Structured Vibe | Reference-heavy but single-phase, low drift consequence |
| Third-party risk questionnaire helper | Vibe / Structured Vibe | Multiple SOPs, contained scope, single-user operation |
| Structured learning / study agent | Spec-Lite | Multi-step, phase-based workflow, no compliance gate |
| Multi-phase research assistant | Spec-Lite | Multi-phase operation, moderate complexity, single stakeholder |
| Investigation copilot | Full Spec-Driven | Multi-phase, evidence-bound, multi-stakeholder |
| Audit / evidence assistant | Full Spec-Driven | Regulatory framework, audit trail required, reproducibility mandatory |

---

*Framework reference — design philosophy, offered as reusable structure rather than measured benchmarks.*
