# Tooling Setup

## Principle

Use the server's native Linux tools only. This is a bare-server exercise.

## Expected Runtime Tools

- `ssh`
- `sudo`
- `visudo`
- `ufw`
- `systemctl`
- `nginx`
- `certbot`

## Recommended Verification Commands

- `sudo /usr/sbin/sshd -T`
- `sudo /usr/sbin/ufw status`
- `systemctl status nginx`
- `curl -i http://<domain>/`
- `curl -i https://<domain>/api`
- `curl -I http://<domain>/api`
- `openssl s_client -connect <domain>:443 -servername <domain>`

## Safety Guidance

- keep an existing root or provider console session open while hardening SSH
- test new SSH access before closing the current working session
- validate Nginx config before reload or restart
