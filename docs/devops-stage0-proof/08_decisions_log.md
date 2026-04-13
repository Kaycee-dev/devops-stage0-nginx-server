# Decisions Log - DevOps Stage 0 Proof

Use this log for decisions affecting:

- proof interpretation of server-state evidence
- sign-off wording
- submission wording
- handling of missing checker-key evidence

No proof-specific decisions have been recorded yet.

## D-001 - Do not infer the exact HNG username from GitHub identity

- Date: 2026-04-11
- Phase / Checkpoint: Day 1 proof bootstrap
- Options considered:
  - infer `Kaycee-dev` from the GitHub remote or git noreply email and treat it as the final HNG username
  - keep the exact HNG username marked unconfirmed until the operator provides it explicitly
- Decision made: keep the exact HNG username marked unconfirmed until the operator provides it explicitly
- Rationale: the `/api` payload and the submission field are case-sensitive; GitHub identity is not proof of the registered HNG username
- Impact:
  - proof remains honest
  - the `/api` contract stays at a placeholder until the confirmed username is available
- Human approval: pending username confirmation

## D-002 - Keep proof files local-only while the public repo surface stays minimal

- Date: 2026-04-11
- Phase / Checkpoint: Day 1 proof bootstrap
- Options considered:
  - publish the raw journal, evidence logs, and control bundle in the public repo
  - keep the proof files local-only while the public repo tracks only the public-facing project surface
- Decision made: keep the proof files local-only while the public repo tracks only the public-facing project surface
- Rationale: the user explicitly approved keeping the sprint and proof bundle on the local machine only
- Impact:
  - local proof remains available for audit and handoff
  - commit `f7487a2` stays minimal and public-facing
- Human approval: yes, provided directly by the user
