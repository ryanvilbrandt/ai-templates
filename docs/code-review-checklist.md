# Code Review Checklist

Before finalizing any change, apply this checklist:

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
- Did I update the relevant repo docs if I learned something important?

