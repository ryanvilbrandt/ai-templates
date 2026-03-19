Purpose: Stable, cross-project engineering rules for LLMs and developers.

These are defaults. Repo-specific overrides belong in AGENTS.md.

---

## Core Principles

- Prefer clarity over cleverness
- Prefer explicitness over implicit behavior
- Prefer debuggability over convenience
- Prefer reversible systems over fragile ones

### Surface necessary complexity explicitly

If the problem is inherently complex, do not oversimplify it. Make complexity visible and well-structured instead of hiding it.

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
Use `.get()` or `getattr(..., default)` only when missing data is an expected case.

If missing data indicates a bug, use direct access so the failure is explicit.

### Design for idempotency
Retries must be safe.

---

## Testing

### Unit tests

- Fast, isolated, deterministic
- No DB/network
- Mock external dependencies
- Freeze time (mock current time instead of using real time)

### Integration tests

- Validate real boundaries:
  - Database queries and schema assumptions
  - API interactions
  - Serialization/deserialization
  - External systems (queues, files, caches when relevant)
- Allowed to be slower
- Should not be unnecessarily brittle
- Do not run integration tests on every iteration by default unless required by the project

### Philosophy

- Unit tests validate logic
- Integration tests validate wiring

---

## Database Principles

- Prefer additive schema changes
- Avoid destructive deletes
- Prefer soft deletes
- Use migrations only
- Do not rely on implicit schema assumptions; represent expected structures explicitly in code
- Enforce uniqueness and idempotency
- Define schema to enforce data shape (types, required fields, constraints)

---

## Concurrency

- Prefer synchronous by default
- Use async only when it materially improves performance, throughput, or user experience
- Do not add retries unless the operation is idempotent or otherwise safe to repeat
- Handle duplicates explicitly
- Use queues only when beneficial

---

## Caching

- Use caching only when it provides a clear benefit
- TTL should be as short as possible, but no shorter
- Long-lived caches must have a clear reset/invalidation path
- Consider how stale data affects correctness, not just performance

---

## Logging

- Log inputs and outputs at important system boundaries (unless large or sensitive)
- Avoid verbose logging inside loops or frequently executed helper functions
- Use audit storage for large payloads instead of standard logs
- Never log secrets or sensitive data
- Avoid logging entire objects or payloads when they may contain sensitive or high-volume data

---

## Security

### Principle of Least Privilege
Only grant required access.

### Never...

- Embed credentials in code
- Build SQL via string concatenation
- Execute shell commands with unsanitized input
- Trust frontend validation alone
- Log secrets or tokens
- Disable TLS checks casually

### Input validation

- Constrain input at the UI when possible
- Always validate and sanitize input at backend boundaries
- Return explicit 4xx errors for invalid input

---

## Feature Flags

- Prefer percentage or allowlist rollout
- Every flag must have:
  - purpose
  - removal condition
  - (optional) ticket reference
- Remove flags after rollout
- Flags should have an owner or clear context explaining who is responsible for removal

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
- Avoid overly generic names (e.g. data, handler, manager) when a more specific name is practical
- Avoid unnecessary abbreviations
- Generic names are a smell, not a blocker

---

## Documentation

- Comments explain *why*, not *what*
- Refactor unclear code instead of explaining it
- High-value docs:
  - API docs
  - README setup + usage
  - Infrastructure references

