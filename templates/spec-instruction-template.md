# Spec-Driven — Instruction Architecture Template

Use for Spec-Lite and Full Spec-Driven agents. Treat the instruction block as a system design document, not a prompt.

```
IDENTITY:
  [Agent name and role]
  [Authority level and accountability]

DOCUMENT HIERARCHY:
  1. [Primary methodology doc] -- governs approach
  2. [Operational guide] -- governs execution
  3. [Domain data] -- provides facts
  4. [Output spec] -- governs deliverables
  Precedence: In case of conflict, lower-numbered documents win.

AUTHORITY MODEL:
  Autonomous: [Decisions the agent can make]
  Escalate:   [Decisions requiring human input]
  Deny:       [Actions the agent must never take]

WORKFLOW:
  Phase 1: [Name]
    Input:   [What triggers this phase]
    Process: [What the agent does]
    Gate:    [Criteria to proceed]

  Phase 2: [Name]
    Input:   [Output from Phase 1]
    Process: [What the agent does]
    Gate:    [Criteria to proceed]

  Phase N: [Name]
    Input:   [Output from Phase N-1]
    Process: [What the agent does]
    Gate:    [Final verification against output spec]

QUALITY BAR:
  If generated output does not match the spec, the spec wins --
  regenerate to conform.
```

## Build checklist

**Architecture conversation**
- Problem statement documented (what problem, for whom, why now)
- Stakeholders identified (roles, expectations)
- Adjacent systems mapped (other agents, tools, data sources)
- Success criteria defined (measurable outcomes)
- Failure modes cataloged (what can go wrong, consequences)

**Boundary definition**
- Ownership model established (accountable party named)
- Authority scope documented (autonomous vs. escalation)
- Adjacent agent lanes defined (clear handoff points)
- Escalation paths specified (when and to whom)

**Knowledge layer**
- Methodology document written
- Operational guide created
- Domain data organized
- Output spec defined
- Document hierarchy / precedence rules established

**Execution layer**
- Workflow phases defined
- Gate criteria specified (pass/fail per transition)
- Verification criteria documented
- End-to-end test completed
