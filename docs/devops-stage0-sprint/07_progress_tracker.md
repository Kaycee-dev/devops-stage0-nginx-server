# DevOps Stage 0 Sprint - Progress Tracker

## Baseline

- Date started: 2026-04-11
- Required sprint artifacts present: Yes
- Provider chosen: GCP (Google Cloud Platform)
- Region: europe-west1-b
- Server public IPv4: 34.76.24.38 (static)
- Linux distro chosen: Ubuntu 22.04 LTS
- Domain: kelechiuba.duckdns.org
- DNS control: DuckDNS
- HNG username confirmed: Kelechi Uba
- Checker public SSH key received: No (pending)

## Milestones

- M0 Governance bootstrap: Complete — 2026-04-11
- M1 Server user and SSH hardening: Complete — 2026-04-13
- M2 UFW and Nginx HTTP baseline: Complete — 2026-04-13
- M3 TLS and redirect behavior: Complete — 2026-04-13
- M4 Submission closeout: In Progress

## Current Focus

- Task: Obtain checker public SSH key from #track-devops and complete submission
- Checkpoint: All server config complete and verified. HTTPS live with valid Let's Encrypt cert. Both endpoints responding correctly.
- Next actions:
  - install checker public SSH key to /home/hngdevops/.ssh/authorized_keys
  - run final Gate D/E audit commands
  - submit
- Open questions requiring human input:
  - checker public SSH key (from #track-devops channel)

## SESSION START: 2026-04-11 08:32:26 +01:00

- current day/date: Day 1 / 2026-04-11
- target gate: Gate A
- checkpoint: artifacts are present locally, commit `f7487a2` exists for the public repo surface, and the safe SSH-hardening sequence is documented locally
- blockers: cloud provider access missing; domain control missing; exact HNG username unconfirmed; checker public SSH key missing
- next three actions:
  - record provider, distro, public IP, and domain facts once supplied
  - create `hngdevops` and prove a second-session login before changing SSH policy
  - install the exact sudoers rule and verify retained access before enabling UFW
- logs to update this session:
  - sprint progress tracker
  - sprint evidence log
  - sprint decisions log
  - Day 1 raw journal
