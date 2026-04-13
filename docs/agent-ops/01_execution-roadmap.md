# Execution Roadmap

## Combined Order

1. Governance bootstrap
   - record provider, distro, domain, and username
   - create sprint artifacts
   - confirm the checker public SSH key status
2. Server access and hardening
   - user creation
   - sudoers
   - SSH config
3. Firewall and web server
   - UFW
   - Nginx
   - `/` and `/api`
4. DNS and TLS
   - domain resolution
   - Let's Encrypt
   - 301 redirect
5. Submission
   - live verification
   - sign-off
   - submit domain and username

## Dependency Rules

- safe access retention precedes SSH hardening
- SSH hardening precedes firewall lock-in
- HTTP correctness precedes TLS
- live HTTPS verification precedes submission
- proof updates happen in the same session as config or live verification work
