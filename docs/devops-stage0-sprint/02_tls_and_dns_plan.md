# TLS and DNS Plan

## Required State

- domain resolves to the server
- Nginx answers on `80` and `443`
- valid Let's Encrypt certificate installed
- HTTP redirects to HTTPS with `301`

## Verification

- `curl -I http://<domain>/`
- `curl -i https://<domain>/api`
- certificate inspection via browser or `openssl s_client`

## Failure Policy

- do not substitute a self-signed certificate
- do not call TLS complete until the live cert chain validates
