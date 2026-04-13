# Decisions Log - DevOps Stage 0 Delivery

Use this log for non-trivial delivery decisions such as:

- provider selection
- DNS path
- Certbot method
- redirect implementation shape
- checker-key timing and verification policy

No delivery-specific decisions have been recorded yet.

## D-001 - Do not treat the GitHub repo URL as the live submission domain

- Date: 2026-04-11
- Phase / Checkpoint: Day 1 delivery bootstrap
- Options considered:
  - reuse the GitHub repo URL or owner handle as a placeholder live domain
  - keep the live domain blank until the operator supplies a real domain and DNS control path
- Decision made: keep the live domain blank until a real domain and DNS control path are supplied
- Rationale: Stage 0 submission requires a reachable HTTPS domain backed by Let's Encrypt; a GitHub repo URL is not deployment proof
- Impact:
  - D0 remains in progress
  - Gate C and submission-readiness claims stay blocked until real domain evidence exists
- Human approval: pending blocker response

## D-002 - Keep delivery control files local-only

- Date: 2026-04-11
- Phase / Checkpoint: Day 1 repo bootstrap
- Options considered:
  - publish the delivery trackers, sprint prompts, and agent-control files in the public repo
  - keep the delivery control files local-only and track only the public repo surface
- Decision made: keep the delivery control files local-only and track only the public repo surface
- Rationale: the user explicitly directed that the repo exclude the agent materials, sprint prompts, `AGENTS.md`, and `docs/`
- Impact:
  - commit `f7487a2` contains only `.gitignore` and `README.md`
  - delivery evidence remains available locally without being pushed to GitHub
- Human approval: yes, provided directly by the user
