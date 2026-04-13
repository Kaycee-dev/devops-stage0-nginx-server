# Server Hardening Plan

## Day 1 Status

- Working directory role: target project repo
- Cloud provider: pending human input
- Linux distro and version: pending provider console or SSH access
- Domain: pending human input and DNS control confirmation
- Exact HNG username: pending human input
- Checker public SSH key: not received as of `2026-04-11 08:32:26 +01:00`
- Gate A state: in progress locally; live server changes blocked until safe access exists

## Required State

- Linux server provisioned
- non-root user `hngdevops` exists
- `hngdevops` has the required passwordless sudo entries for `/usr/sbin/sshd` and `/usr/sbin/ufw`
- root SSH login disabled
- password-based SSH authentication disabled
- UFW active with only `22`, `80`, and `443`

## Minimum Safe SSH-Hardening Sequence

1. keep the existing root or bootstrap SSH session open and confirm a provider console or serial access path before editing `sshd` or `sudoers`
2. capture baseline host facts and SSH state with `hostnamectl`, `cat /etc/os-release`, and `sshd -T | grep -E 'permitrootlogin|passwordauthentication|pubkeyauthentication'`
3. create `hngdevops`
4. create `/home/hngdevops/.ssh` with correct ownership and permissions
5. install the operator public key for `hngdevops`
6. open a second session and prove `ssh hngdevops@<server>` works before changing root-login or password-auth settings
7. install the exact sudoers drop-in with `hngdevops ALL=(root) NOPASSWD:/usr/sbin/sshd,/usr/sbin/ufw`
8. validate the sudoers file with `visudo -cf /etc/sudoers.d/hngdevops-stage0`
9. from the second session, verify `sudo /usr/sbin/sshd -T` and `sudo /usr/sbin/ufw status` run without a password prompt
10. set `PermitRootLogin no` and `PasswordAuthentication no` while keeping public-key authentication enabled
11. run `sshd -t`, reload `sshd`, and prove a brand-new `hngdevops` login still works before closing the original session
12. only after retained access is proven, enable UFW and allow only `22`, `80`, and `443`

## Exact Sudoers Plan

- target file: `/etc/sudoers.d/hngdevops-stage0`
- exact content: `hngdevops ALL=(root) NOPASSWD:/usr/sbin/sshd,/usr/sbin/ufw`
- validation command: `visudo -cf /etc/sudoers.d/hngdevops-stage0`

## Retained-Access Verification Plan

- keep one known-good session open until the end of Gate A
- prove a fresh `hngdevops` login from a second session before and after the `sshd` reload
- verify the required passwordless sudo commands from `hngdevops`
- do not activate UFW until the second-session login survives the SSH hardening change

## Checker Key Note

Record whether the public SSH key from `#track-devops` has been received and installed. If it has not been received, treat checker access as blocked rather than complete.

## Day 1 Blockers

- provider access or console path has not been supplied yet
- domain ownership or DNS control path has not been supplied yet
- exact HNG username has not been confirmed yet
- checker public SSH key has not been supplied yet
