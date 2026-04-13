# Decisions Log - DevOps Stage 0 Sprint

Use `D-001`, `D-002`, and so on. Every entry should record:

- date
- phase or checkpoint
- options considered
- decision made
- rationale
- impact
- whether human approval was required

Seed decision already encoded by this kit:

## D-000 - Treat missing checker SSH key as a blocker, not an assumed completed step

- Date: 2026-04-11
- Phase / Checkpoint: contract setup
- Options considered:
  - assume the key will arrive later and still mark checker access complete
  - record the key as a live dependency and block completion until it is installed or explicitly waived
- Decision made: record the key as a blocker until installed or explicitly waived
- Rationale: the task explicitly says a public SSH key will be provided for checking. Pretending that step is complete without the key would fabricate readiness.
- Impact:
  - checker-access proof stays honest
  - the delivery state must carry the key as an open dependency until resolved
- Human approval: not yet required unless the operator chooses to submit without it

## D-001 - Treat this working directory as the authoritative target repo

- Date: 2026-04-11
- Phase / Checkpoint: Day 1 governance bootstrap
- Options considered:
  - leave the repo described as a copy-only kit and track live execution elsewhere
  - treat this working directory as the authoritative target project repo and update the Day 1 logs here
- Decision made: treat this working directory as the authoritative target project repo
- Rationale: the user explicitly stated that this repo is the target project repo, not only a portable overlay
- Impact:
  - Day 1 tracker updates, hardening plans, and git history belong in this repo
  - repo-facing docs should describe the live project state honestly
- Human approval: yes, provided directly by the user

## D-002 - Stop Gate A before server mutation when live prerequisites are missing

- Date: 2026-04-11
- Phase / Checkpoint: Day 1 governance bootstrap
- Options considered:
  - begin server-side user, SSH, or firewall work immediately against an unspecified target
  - stop after planning and session-start logging until provider access, domain control, exact HNG username, and checker-key status are confirmed
- Decision made: stop after planning and session-start logging until the live prerequisites are confirmed
- Rationale: the sprint prompts and `AGENTS.md` require stop-and-ask behavior for missing provider access, missing domain control, and a missing checker key; the exact HNG username is also required for the case-sensitive `/api` contract
- Impact:
  - no fabricated server evidence enters the logs
  - retained-access planning is documented before any risky SSH or sudoers change
- Human approval: pending blocker response

## D-003 - Keep the control-plane bundle local-only and out of the public repo

- Date: 2026-04-11
- Phase / Checkpoint: Day 1 repo bootstrap
- Options considered:
  - commit `.agents/`, `AGENTS.md`, the sprint prompts, and `docs/` into the public repo
  - keep the control-plane bundle local-only and exclude it from version control with `.gitignore`
- Decision made: keep the control-plane bundle local-only and exclude it from version control with `.gitignore`
- Rationale: the user explicitly requested that the repo include only the files needed for the public project surface, while the agent and sprint materials stay local
- Impact:
  - local planning, proof, and gate-control records remain on the workstation
  - the public repo currently contains only `.gitignore` and `README.md`
- Human approval: yes, provided directly by the user
