Purpose: Repo-specific source of truth for LLMs and developers.

After reading this file, ask the user clarifying questions to fill out the information below and specify what type of project this is. Update this file to be a long-term description of this repo, and guidance to future LLMs based on the user's answers.

Update this file regularly as the project's requirements, constraints, and structure change.

See ENGINEERING_PRINCIPLES.md for further rules to follow and guidance on how to write good code.

---

## Initialization Rule (CRITICAL)

- Do not begin implementation until Project Context is sufficiently filled out
- If key fields are missing, ask clarifying questions first

---

## Project Context

- Project type:
- Purpose:
- Primary users:
- Expected lifetime:
- Risk level:
- Failure impact:
- Data sensitivity:
- Deployment model:

---

## Repository Overview

### Goals
- 

### Non-goals
- 

### Architecture Summary
- 

### Key Components
- 

### Data Flow
- 

### External Dependencies
- 

---

## Requirements and Constraints

- Performance:
- Reliability:
- Security:
- Testing:
- Documentation:

---

## LLM Behavior Mode (REPLACE THIS SECTION)

### Instructions

- After answering the Project Context questions, SELECT and KEEP ONLY ONE mode below
- Delete the other modes
- This section must reflect the actual project type

### One-off script
- Optimize for speed and clarity
- Minimal abstraction
- Minimal testing

### Solo project
- Optimize for maintainability
- Moderate structure

### Team service
- Emphasize clarity, logging, testing

### Production system
- Emphasize safety, observability, rollback

### Enforcement Rule

- The selected mode modifies how ENGINEERING_PRINCIPLES.md is applied
- For lower-risk projects (e.g. one-off scripts), some principles may be relaxed
- For higher-risk projects (e.g. production systems), all principles must be strictly enforced

### Mode → Behavior Translation

- Convert the selected mode into concrete expectations in:
  - Requirements and Constraints
  - Testing expectations
  - Logging and safety level
- If the mode changes, update those sections accordingly

---

## Questions LLM Should Ask Early

- What kind of project is this?
- Who maintains it?
- What happens if it fails?
- Does it touch sensitive systems?
- Optimize for speed, simplicity, or safety?

### After Questions Are Answered (CRITICAL)

- Write the answers into the appropriate sections of this file (Project Context, Requirements, etc.)
- Summarize decisions, not just raw answers
- Remove or replace placeholders once information is known
- If answers imply constraints (e.g., high risk, sensitive data), reflect that in Requirements and Behavior Mode

---

## Working Agreements

- Preferred tools:
- Forbidden tools:
- Deployment workflow:
- CI/CD expectations:

---

## Feature Flags

- Must include purpose + removal condition
- Prefer percentage rollout

---

## Known Risks / Tradeoffs

- 

---

## Overrides to ENGINEERING_PRINCIPLES.md

- 

---

## Common LLM Failure Patterns

Be aware of these common mistakes and actively avoid them:

### Over-abstraction
- Creating abstractions before they are needed
- Generalizing from a single use case
- Introducing unnecessary layers or indirection

### Hidden defaults and silent fallbacks
- Using `.get()` or default values when missing data should be an error
- Masking bugs instead of surfacing them

### Unrequested behavior
- Adding “helpful” features or side effects not explicitly asked for
- Expanding scope beyond the stated task

### Implicit assumptions
- Assuming schema, data shape, or API behavior without confirmation
- Failing to state assumptions before implementation

### Boundary violations
- Mixing concerns across layers (e.g., DB logic in API handlers)
- Ignoring system boundaries (API, DB, filesystem, queues)

### Overuse of defensive coding
- Adding guards everywhere instead of understanding expected invariants
- Making code verbose while hiding real issues

### Logging mistakes
- Logging too little at important boundaries
- Logging too much in hot paths
- Logging sensitive or large payloads

### Async and concurrency misuse
- Introducing async unnecessarily
- Ignoring idempotency in retry logic
- Failing to handle duplicate processing

### Ignoring project context
- Treating a production system like a script
- Over-engineering simple tools
- Under-engineering critical systems

### Incomplete updates to AGENT.md
- Asking good questions but not recording the answers
- Leaving placeholders instead of updating context

---

## LLM Rules

- Do not take high-impact actions automatically
- Ask clarifying questions when ambiguity affects:
  - data structures or schemas
  - system boundaries (DB, API, filesystem, queues)
  - error handling behavior
  - deployment or runtime environment
  - security or data safety
- State assumptions when proceeding
- Prefer explicit failure over silent defaults
- Never run system utilities without explicit permission
- When making assumptions, explicitly state them before implementing
- If assumptions materially affect behavior, ask before proceeding
- Do not ask unnecessary clarification questions when reasonable assumptions can be safely made
- When proceeding with assumptions, state them clearly
- Do not introduce behavior that was not explicitly requested or clearly implied
- Avoid "helpful" side effects that are not part of the stated goal
- Avoid hidden state and implicit side effects
- Prefer explicit inputs/outputs over mutating shared or global state
- Clearly define and respect system boundaries (API, DB, filesystem, queues)
- Do not mix responsibilities across layers without explicit reason

---

## LLM Code Review Checklist

Before finalizing:

- Are state changes explicit?
- Are errors fail-fast?
- Are retries safe and idempotent?
- Any hidden defaults or silent fallbacks?
- Are system boundaries respected?
- Are inputs validated and sanitized?
- Are important boundaries logged?
- Are assumptions clearly stated?
- Is complexity justified (not under- or over-engineered)?
- Any unnecessary abstraction?
- Any unintended side effects?
- Any security risks?
- Does this match project type and risk level?

---

## Update Rules (CRITICAL)

- This file is the persistent memory of the repository
- Update this file as soon as new information is learned
- Do not leave placeholders once answers are known
- Do not silently guess missing context — ask or leave explicit TODOs
- Prefer updating this file over re-explaining context in chat
- Future LLM sessions should rely on this file as the source of truth

---

## Context Recovery Notes

- Key assumptions:
- Important decisions:
- Gotchas:
