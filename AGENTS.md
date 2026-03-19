# AGENTS.md

Purpose: Front door for LLMs and developers working in this repository.

This file is the repo's quick-start operational guide. It tells you:
- what this project is
- how risky it is
- how rigorously to work
- which supporting docs to read
- which files to update when you learn new information

Do not treat this file as the only source of truth. Use it as the index and operating guide for the repo's persistent documentation.

---

## Role of This File

This file should stay concise. It should contain:
- the current high-level project context
- the selected LLM behavior mode
- important repo-specific working agreements
- pointers to deeper documents
- current known risks and assumptions

This file should not become the full architecture spec, roadmap, or requirements doc. Put detailed information in supporting docs and summarize it here.

---

## Canonical Supporting Docs

Use these as the long-form source of truth for repo details.

- Architecture: `docs/architecture.md`
- Engineering principles: `docs/engineering_principles.md`
- Requirements and constraints: `docs/requirements.md`
- Roadmap and deferred work: `docs/roadmap.md`
- Design decisions / ADRs: `docs/decisions/`

If a relevant file is missing, create it instead of stuffing too much detail into `AGENTS.md`.

---

## Initialization Rule (CRITICAL)

Before implementation:
- Read this file first
- Read the files in `docs/`
- Do not begin implementation until Project Context is sufficiently filled out
- If key fields are missing, ask clarifying questions first
- If an answer would materially affect architecture, data safety, testing, deployment, or security, do not guess

---

## Document Update Policy (CRITICAL)

Update the correct file when new information is learned:

- Update `AGENTS.md` when:
  - project context changes
  - working agreements change
  - repo-wide LLM instructions change
  - risk level, behavior mode, or major assumptions change
  - a summary or pointer to deeper documentation must be updated

- Update `docs/architecture.md` when:
  - component boundaries change
  - data flow changes
  - dependencies or integration points change
  - a new subsystem or service is introduced

- Update `docs/engineering_principles.md` when:
  - long-lived coding or review principles need to change
  - recurring LLM/developer failure patterns reveal missing guidance
  - existing principles are ambiguous, conflicting, or materially incomplete
  - repo-wide safety, reliability, or quality defaults are intentionally updated
  - for major or non-obvious principle changes, record rationale in `docs/decisions/`

- Update `docs/requirements.md` when:
  - performance, reliability, security, testing, or documentation expectations change
  - operational constraints become known
  - quality bars or acceptance expectations change

- Update `docs/roadmap.md` when:
  - future plans, follow-up work, cleanup work, or staged refactors are identified
  - work is intentionally deferred
  - technical debt is accepted with a future plan

- Update `docs/decisions/` when:
  - an important architectural or operational tradeoff is decided
  - a non-obvious choice needs lasting rationale
  - a future developer would need to know why a choice was made

Always prefer updating the relevant persistent doc over leaving important context only in chat.

---

## Project Context

- Project type: <fill in target repo>
- Purpose: <fill in target repo>
- Primary users: <fill in target repo>
- Expected lifetime: <fill in target repo>
- Risk level: <fill in target repo>
- Failure impact: <fill in target repo>
- Data sensitivity: <fill in target repo>
- Deployment model: <fill in target repo>

---

## LLM Behavior Mode (REPLACE THIS SECTION)

### Instructions

- After answering the Project Context questions, SELECT and KEEP ONLY ONE mode below
- Delete the other modes
- This section must reflect the actual project type and risk level
- The selected mode changes how strictly the repo should apply the guidance in `docs/engineering_principles.md`
- If the mode changes, update related expectations in `docs/requirements.md` and any other affected docs

### One-off script
- Optimize for speed and clarity
- Keep structure minimal
- Prefer direct solutions over reusable abstractions
- Minimal testing unless failure impact is higher than expected
- Lightweight docs are acceptable

### Solo project
- Optimize for maintainability and readability
- Use moderate structure
- Prefer simple helpers over elaborate abstractions
- Add tests for important logic and edge cases
- Keep docs practical and lightweight

### Team service
- Emphasize clarity, explicitness, logging, and tests
- Respect boundaries between layers
- Prefer maintainability over speed of initial implementation
- Record important design decisions
- Keep architecture and requirements docs current

### Production system
- Emphasize safety, observability, rollback, correctness, and controlled change
- Apply principles strictly
- Require strong validation, logging, and explicit operational behavior
- Prefer reversible and staged changes
- Keep all supporting docs current and specific

---

## Required Clarification Questions

Ask these before implementation if not already known:

- What kind of project is this (script, solo, team, production)?
- What happens if this fails?
- Does this touch sensitive data or systems?
- What level of testing is expected?
- Are there required or forbidden tools/patterns?

If answers affect architecture, safety, or data integrity, do not proceed without clarity.

### After Questions Are Answered (CRITICAL)

- Write the answers into the appropriate sections of this file
- Summarize decisions, not just raw answers
- Replace placeholders once information is known
- If answers imply deeper documentation needs, update or create the correct supporting file
- If answers imply constraints such as high risk or sensitive data, reflect that in the selected Behavior Mode and in `docs/requirements.md`

---

## Working Agreements (Active)

These are current expectations for working in this repo.

- Preferred tools: <fill in target repo>
- Forbidden tools: <fill in target repo>
- Deployment workflow: <fill in target repo>
- CI/CD expectations: <fill in target repo>
- Testing expectations: <fill in target repo>
- Review expectations: <fill in target repo>
- Documentation expectations: <fill in target repo>

If these become complex, move details into `docs/requirements.md`.

---

## Feature Flag Policy

- Every flag must have:
  - purpose
  - removal condition
- Prefer percentage rollout or allowlist rollout
- Long-lived flags should be tracked in `docs/roadmap.md` or a decision doc if they affect architecture or operations

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
- Read and update the appropriate supporting docs when repo knowledge changes

---

## Update Rules (CRITICAL)

- This file is the persistent entry point for repo context
- Do not guess missing context; ask or leave explicit TODOs
- Prefer updating repo docs over re-explaining context in chat
- Future LLM sessions should rely on this file first, then the supporting docs
- Keep this file concise by moving substantial detail into the appropriate docs

---

## Context Recovery Notes

- Key assumptions: <fill in target repo>
- Important decisions: <fill in target repo>
- Gotchas: <fill in target repo>
- Pointers to the most important supporting docs for current work: <fill in target repo>
