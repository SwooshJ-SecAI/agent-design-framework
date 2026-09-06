# Vibe Coding — Minimum Viable Instruction Template

Use for Vibe Basic and Structured Vibe agents. Fill the brackets, deploy, then iterate:
**Use it → find drift → add one constraint → repeat until stable.**

```
ROLE: [Single sentence defining what the agent is]

SCOPE:
- Does: [Task 1], [Task 2], [Task 3]
- Does Not: [Exclusion 1], [Exclusion 2]

BOUNDARIES:
- [Constraint 1]
- [Constraint 2]

OUTPUT FORMAT:
- [Structure definition]
- [Length guidance]
- [Tone/style notes]

REFERENCE FILES:
- [File 1]: [Purpose]
- [File 2]: [Purpose]
```

## Build checklist

| Item | Notes |
|------|-------|
| Role identity defined | Clear, single-sentence role statement |
| Scope boundaries established | Explicit "does" and "does not" lists |
| Output format specified | Structure, length, and style defined |
| Reference files attached | SOPs, policies, templates linked |
| Test scenarios executed | 5+ representative prompts tested |
| Drift log started | Track observed drift over time |
| First iteration complete | At least one constraint added from testing |

## Migration signal

Move up to a Spec tier when: the agent accumulates 10+ iterative constraints, its output starts being consumed by other people or systems, or its failure mode shifts from "inconvenient" to "consequential."
