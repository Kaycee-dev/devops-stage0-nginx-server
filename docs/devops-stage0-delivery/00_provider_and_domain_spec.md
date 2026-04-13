# Provider and Domain Spec

## Current Status — Updated 2026-04-13

- Cloud provider: GCP (Google Cloud Platform)
- Project ID: devops-stage0-nginx-server
- Region / Zone: europe-west1-b
- Machine type: f1-micro
- Server public IP: 34.76.24.38 (static, reserved as hng-stage0-ip)
- Linux distro and version: Ubuntu 22.04.5 LTS
- Domain name: kelechiuba.duckdns.org
- DNS control path: DuckDNS
- Exact HNG username: Kelechi Uba
- Checker public SSH key: not received yet
- GitHub repo URL: `https://github.com/Kaycee-dev/devops-stage0-nginx-server.git`

## Required Facts

- cloud provider
- region
- server public IP
- Linux distro and version
- domain name
- DNS control path
- exact HNG username

## Remaining Blockers

- checker public SSH key has not been received yet (check #track-devops)

## Deployment Requirements

- live domain reachable on `https://`
- ports `80` and `443` open publicly
- Nginx active on the server
- Let's Encrypt certificate valid

## Proof Discipline

- do not infer the live domain from the GitHub repo URL
- do not infer the exact HNG username from the GitHub owner handle or git identity
