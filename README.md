# DevOps Stage 0 — Kelechi Uba

HNG DevOps Track Stage 0: hardened Linux server with Nginx, UFW, and Let's Encrypt.

## Live Deployment

| Field | Value |
|---|---|
| Domain | https://kelechiuba.duckdns.org |
| Server IP | 34.76.24.38 |
| Provider | GCP (europe-west1-b) |
| OS | Ubuntu 22.04.5 LTS |
| HNG username | Kelechi Uba |

## Endpoints

- `GET /` — HTML page with username visible as page text
- `GET /api` — JSON: `{"message":"HNGI14 Stage 0","track":"DevOps","username":"Kelechi Uba"}`

## Server Hardening

- Non-root operator user: `hngdevops`
- Passwordless sudo scoped to `/usr/sbin/sshd` and `/usr/sbin/ufw` only
- Root SSH login disabled
- Password-based SSH authentication disabled
- UFW active: ports 22, 80, 443 only
- Let's Encrypt TLS certificate (valid until 2026-07-12)
- HTTP → HTTPS 301 redirect
