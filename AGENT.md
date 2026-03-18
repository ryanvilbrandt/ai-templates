# AGENT.md

Purpose: Repo-specific source of truth for LLMs and developers.

After reading this file, ask the user clarifying questions to fill out the information below and specify what type of project this is. Update this file to be a long-term description of this repo, and guidance to future LLMs based on the user's answers.

This file should be updated regularly as the project's requirements, constraints, and structure change.

See ENGINEERING_PRINCIPLES.md for further rules to follow and guidance on how to write good code.

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

Choose ONE after clarification:

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

---

## Questions LLM Should Ask Early

- What kind of project is this?
- Who maintains it?
- What happens if it fails?
- Does it touch sensitive systems?
- Optimize for speed, simplicity, or safety?

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

## Update Rules

- Update this file as decisions evolve
- Do not guess missing context
- Prefer updating this over re-explaining context

---

## Context Recovery Notes

- Key assumptions:
- Important decisions:
- Gotchas:

---

## LLM Rules

- Do not take high-impact actions automatically
- Ask questions when ambiguity affects safety or architecture
- State assumptions when proceeding
- Prefer explicit failure over silent defaults
- Never run system utilities without explicit permission

---

## LLM Code Review Checklist

Before finalizing:

- Are state changes explicit?
- Are errors fail-fast?
- Are retries safe?
- Any hidden defaults?
- Are boundaries logged?
- Are assumptions stated?
- Is complexity justified?
- Any unnecessary abstraction?
- Any security risks?
- Does this match project type?
