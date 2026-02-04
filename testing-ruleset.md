# Testing Ruleset

## Scope & Coverage

- Unit tests: The goal is 70–80% overall, ≥90% for critical modules.

- Integration tests: cover service boundaries, DB, queues, external APIs.

- E2E tests: 5–15 key user flows + 3–5 failure cases.


## Ownership

- Unit tests: written by the developer who writes the code.

- Integration tests: shared responsibility, live in tests/integration/, run with containers (not prod).

- E2E tests: shared responsibility between devs, stored in tests/e2e/.

## When to Run

Pre-commit (local): fast unit tests + lint/typecheck (<2 min).

PR/CI: all unit + integration tests.

Pre-release (staging): E2E (+ Unit + Integration if not already executed).
