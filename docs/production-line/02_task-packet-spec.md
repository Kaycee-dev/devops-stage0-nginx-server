# Task Packet Specification

Use this spec to dispatch non-trivial DevOps Stage 0 work.

## Packet Shape

```yaml
packet_id: d0-<lane>-<yyyymmdd>-<nn>
day: <overlay day>
lane_type: control | provisioning | hardening | nginx | ssl | proof
objective: >
  One sentence describing the finished state.
scope_in:
  - owned files, configs, or behaviors
scope_out:
  - areas the lane must not change without escalation
repo_root: <absolute repo path>
worktree:
  path: <absolute path>
  branch: <branch name>
primary_surface: shell | mixed | editor
required_reads:
  - AGENTS.md
  - relevant sprint prompt
inputs:
  - prior packet ids or gate dependencies
deliverables:
  - concrete outputs
verification:
  commands:
    - exact commands
  manual_proofs:
    - live URL or server-state checks
green_level: targeted_green | lane_green | gate_green | release_green
evidence_updates:
  - progress tracker
  - evidence log
  - decisions log
  - raw journal
escalate_when:
  - exact blocker conditions
closeout_contract:
  must_report:
    - summary
    - files changed
    - checks run
    - blocker status
    - next exact starting point
    - next handoff point
```

## Example - Hardening Lane

```yaml
packet_id: d0-hardening-20260411-01
day: Day 1
lane_type: hardening
objective: >
  Leave the server accessible by key while disabling root login and password-based SSH authentication.
scope_in:
  - sshd_config
  - sudoers for hngdevops
scope_out:
  - Nginx route behavior
  - TLS
green_level: gate_green
```
