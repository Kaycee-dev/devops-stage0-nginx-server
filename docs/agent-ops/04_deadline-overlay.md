# Deadline Overlay

Use this file as the dated execution overlay for the April 11-16, 2026 delivery window.

## Overlay Defaults

- Window: `2026-04-11` through `2026-04-16`
- Final cutoff: Thursday, `2026-04-16`
- Mode: fast-turn, single-server delivery
- Gate approvals: same-day

## Daily Operating Rhythm

1. Session start
   - read `06_delivery-state.md`
   - confirm day/date, checkpoint, target gate, blockers, next three actions
2. Build block
   - work only on the current critical path
3. Proof block
   - update progress, evidence, decisions, and journal artifacts
4. Session close
   - update `06_delivery-state.md`
   - record the next exact starting point and next handoff point

## Gate Calendar

| Gate | Planned day | Date | Required by close of |
|---|---|---|---|
| Gate A | Day 2 | 2026-04-12 | server access, `hngdevops`, SSH hardening |
| Gate B | Day 3 | 2026-04-13 | UFW active and Nginx routes correct over HTTP |
| Gate C | Day 4 | 2026-04-14 | DNS, Let's Encrypt, and 301 redirect live |
| Gate D | Day 5 | 2026-04-15 | checker-key and sudo-command verification |
| Gate E | Day 6 | 2026-04-16 | final live smoke and submission readiness |

## Daily Plan

| Day | Critical path | Required proof |
|---|---|---|
| Day 1 - Sat Apr 11 | provider/domain setup, artifact bootstrap, SSH sequencing plan | progress tracker, first evidence entry, first decisions entry, Day 1 journal |
| Day 2 - Sun Apr 12 | `hngdevops`, sudoers, SSH hardening, test retained access | updated logs, `sshd -T` evidence, Gate A pack |
| Day 3 - Mon Apr 13 | UFW activation, Nginx install, `/` and `/api` over HTTP | UFW proof, Nginx proof, Gate B pack |
| Day 4 - Tue Apr 14 | DNS verification, Certbot, HTTPS, 301 redirect | live cert proof, redirect proof, Gate C pack |
| Day 5 - Wed Apr 15 | checker key install, passwordless sudo verification, sign-off draft | command proof, sign-off draft, Gate D pack |
| Day 6 - Thu Apr 16 | final live smoke and submission | final sign-off, submission checklist, delivery-state closeout |

## Slippage Policy

- If safe SSH access is at risk, recover access first.
- TLS work never outranks broken HTTP baseline behavior.
- Same-day proof updates are part of the deliverable, not optional admin work.
