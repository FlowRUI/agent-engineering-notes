# 05 · Agent Evaluation

Final-answer accuracy is necessary but insufficient. Agent evaluation should inspect both outcomes and trajectories.

## Evaluation layers

- Outcome: Was the user goal achieved?
- Process: Were tools chosen and used correctly?
- Grounding: Are claims supported by observable evidence?
- Efficiency: Were unnecessary steps and retries avoided?
- Safety: Were side effects authorized and scoped?
- Recoverability: Can failures be diagnosed and replayed?

Start with deterministic checks, add model-based judges only where rubric-based interpretation is required, and periodically calibrate judges against human review.
