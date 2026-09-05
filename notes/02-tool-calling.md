# 02 · Tool Calling

Reliable tool use starts with contracts, not prompt cleverness.

## Contract

Each tool should define its purpose, typed inputs, side effects, error model, idempotency behavior, and observable success signal.

## Execution loop

1. Select the narrowest capable tool.
2. Validate arguments before execution.
3. Record the request and result.
4. Inspect the returned state.
5. Retry only when the error is classified as retryable.

## Common anti-pattern

Blindly repeating the same call after an unchanged precondition is not recovery; it is duplicated failure.
