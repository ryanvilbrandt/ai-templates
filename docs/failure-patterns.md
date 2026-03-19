# Common LLM Failure Patterns

Be aware of these common mistakes and actively avoid them:

## Over-abstraction
- Creating abstractions before they are needed
- Generalizing from a single use case
- Introducing unnecessary layers or indirection

## Hidden defaults and silent fallbacks
- Using `.get()` or default values when missing data should be an error
- Masking bugs instead of surfacing them

## Unrequested behavior
- Adding "helpful" features or side effects not explicitly asked for
- Expanding scope beyond the stated task

## Implicit assumptions
- Assuming schema, data shape, or API behavior without confirmation
- Failing to state assumptions before implementation

## Boundary violations
- Mixing concerns across layers (e.g. DB logic in API handlers)
- Ignoring system boundaries (API, DB, filesystem, queues)

## Overuse of defensive coding
- Adding guards everywhere instead of understanding expected invariants
- Making code verbose while hiding real issues

## Logging mistakes
- Logging too little at important boundaries
- Logging too much in hot paths
- Logging sensitive or large payloads

## Async and concurrency misuse
- Introducing async unnecessarily
- Ignoring idempotency in retry logic
- Failing to handle duplicate processing

## Ignoring project context
- Treating a production system like a script
- Over-engineering simple tools
- Under-engineering critical systems

## Incomplete documentation updates
- Asking good questions but not recording the answers
- Leaving placeholders instead of updating context
- Updating code without updating the relevant repo docs

