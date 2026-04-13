# Stage 0 Rollout

## Initial Lane Board

| Lane | Window | Preconditions | Success signal |
|---|---|---|---|
| control | all days | none | delivery state and packets stay current |
| provisioning | Days 1-2 | none | server, domain, and `hngdevops` path are clear |
| hardening | Days 1-3 | provisioning stable | SSH and firewall state are correct |
| nginx | Days 2-3 | hardening path stable | `/` and `/api` are correct over HTTP |
| ssl | Days 3-5 | nginx route baseline stable | valid HTTPS and 301 redirect are live |
| proof | all days | none | same-day logs are current |

## Serialization Rules

- `provisioning` blocks `hardening`
- `hardening` blocks `nginx`
- `nginx` blocks `ssl`
- `proof` runs alongside every active lane

## Immediate Groundwork Tasks

1. instantiate the lane board from `templates/lane-board.md`
2. issue a standing `proof` packet
3. issue the first `hardening` packet once provider and domain facts are known
