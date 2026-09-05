# 01 · Agent Architecture

## Working model

An agent system is easier to reason about when planning, execution, state, and review have explicit boundaries.

```mermaid
sequenceDiagram
    participant U as User
    participant P as Planner
    participant X as Executor
    participant T as Tool
    participant R as Reviewer
    U->>P: Goal
    P->>X: Typed plan
    X->>T: Validated call
    T-->>X: Structured result
    X->>R: Trace + candidate answer
    R-->>U: Accepted output or revision request
```

## Failure modes

- Planner emits actions that no tool can execute.
- Executor retries without reading changed state.
- Reviewer sees only the final answer and misses a dangerous trajectory.
- Shared mutable state makes failures hard to reproduce.

## Design checklist

- Are component inputs and outputs typed?
- Is every side effect recorded with an event ID?
- Can the reviewer cite the evidence behind a decision?
- Is there a deterministic stopping condition?
