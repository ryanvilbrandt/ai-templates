# ENGINEERING_PRINCIPLES.md

Purpose: Stable, cross-project engineering rules for LLMs and developers.

These are defaults. Repo-specific overrides belong in AGENT.md.

---

## Core Principles

- Prefer clarity over cleverness
- Prefer explicitness over implicit behavior
- Prefer debuggability over convenience
- Prefer reversible systems over fragile ones

---

## Code Structure

### Prefer vertical, step-by-step code
Each line should represent one conceptual step.

### Avoid nested ternaries and complex comprehensions
Use them only for simple, obvious cases.

### Delay abstraction (Rule of Three)
Do not abstract until at least three real use cases exist.

### Prefer composition over inheritance
Avoid deep class hierarchies.

### Code should be understandable at a glance
If it requires prolonged analysis, refactor it.

---

## State Management

### Keep mutable state local
Pass state explicitly. Shared state belongs in DB/cache.

### Make state transitions obvious
Hidden mutations are bugs waiting to happen.

---

## Error Handling

### Fail fast and loudly
Do not silently recover from unexpected states.

### Preserve error context
Use proper chaining (`raise ... from e`).

### Prefer explicit failures over hidden fallbacks
Use `.get()` / `getattr()` only when absence is expected.

### Design for idempotency
Retries must be safe.

---

## Testing

### Unit tests
- Fast, isolated, deterministic
- No DB/network
- Mock external dependencies
- Freeze time in tests (mock current time)

### Integration tests
- Validate real boundaries:
  - Database queries
  - API interactions
  - Serialization/deserialization
  - External systems (queues, files, caches when relevant)
- Allowed to be slower
- Should not be unnecessarily brittle

### Philosophy
- Unit tests validate logic
- Integration tests validate wiring

---

## Database Principles

- Prefer additive schema changes
- Avoid destructive deletes
- Prefer soft deletes
- Use migrations only
- Make schemas explicit in code
- Enforce uniqueness and idempotency

---

## Concurrency

- Prefer synchronous by default
  - Use async when it materially improves performance, throughput, or user experience.
- Retries require idempotency
- Handle duplicates explicitly
- Use queues only when beneficial

---

## Logging

- Log inputs/outputs at system boundaries (unless large/sensitive)
- Use audit storage for large payloads
- Avoid verbose logging inside loops or frequently executed helper functions
- Never log secrets

---

## Security

### Principle of Least Privilege
Only grant required access.

### Never:
- Embed credentials in code
- Build SQL via string concatenation
- Execute shell commands with unsanitized input
- Trust frontend validation alone
- Log secrets or tokens
- Disable TLS checks casually

---

## Feature Flags

- Prefer percentage or allowlist rollout
- Every flag must have:
  - purpose
  - removal condition
  - (optional) ticket reference
- Remove flags after rollout

---

## Caching

- Use only when beneficial
- TTL: as short as possible, but no shorter
- Long-lived caches must have reset path

---

## Refactoring

### Use phased refactors
1. Prep (no behavior change)
2. Core change
3. Cleanup

Prefer many small deploys over large ones.

---

## Naming

- Prefer clear, specific names
- Avoid unnecessary abbreviations
- Generic names are a smell, not a blocker

---

## Documentation

- Comments explain *why*, not *what*
- Refactor unclear code instead of explaining it
- High-value docs:
  - API docs
  - README setup + usage
  - infra references
