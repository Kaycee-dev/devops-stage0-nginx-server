# Evidence Log - DevOps Stage 0 Sprint

Use `E-001`, `E-002`, and so on. Every entry should record:

- date
- scope
- files changed
- commands run
- result
- behavioral outcome
- risks or follow-up

No target-server evidence has been recorded yet. The first real entry should start after the kit is copied into the working project and the provider/domain facts are known.

## E-001 - Day 1 governance bootstrap and Gate A planning

- date: `2026-04-11 08:32:26 +01:00`
- scope: verified authority files, required artifact presence, git repo state, and the minimum safe Gate A SSH-hardening sequence
- files changed: `README.md`; `docs/devops-stage0-sprint/00_server_hardening_plan.md`; `docs/devops-stage0-sprint/07_progress_tracker.md`; `docs/devops-stage0-sprint/08_evidence_log.md`; `docs/devops-stage0-sprint/09_decisions_log.md`; `docs/devops-stage0-delivery/00_provider_and_domain_spec.md`; `docs/devops-stage0-delivery/06_progress_tracker.md`; `docs/devops-stage0-delivery/07_evidence_log.md`; `docs/devops-stage0-delivery/08_decisions_log.md`; `docs/devops-stage0-proof/01_raw_journal/2026-04-11_day_1.md`; `docs/devops-stage0-proof/06_progress_tracker.md`; `docs/devops-stage0-proof/07_evidence_log.md`; `docs/devops-stage0-proof/08_decisions_log.md`; `docs/agent-ops/06_delivery-state.md`
- commands run: `Get-Content -Raw AGENTS.md`; `Get-Content -Raw devops-stage0-sprint_v1_0.md`; `Get-Content -Raw devops-stage0-hardening-sprint_v1_0.md`; `Get-Content -Raw devops-stage0-proof-sprint_v1_0.md`; `Get-ChildItem docs -Recurse -File`; `git status --short --branch`; `git remote -v`; `git init -b main`; `git remote add origin https://github.com/Kaycee-dev/devops-stage0-nginx-server.git`; `git add .`; `git rm --cached -r .agents`; `git rm --cached -r AGENTS.md devops-stage0-sprint_v1_0.md devops-stage0-hardening-sprint_v1_0.md devops-stage0-proof-sprint_v1_0.md docs`; `git add .gitignore README.md`; `git commit -m "Initialize project repo surface"`; `git log --oneline -1`; `git status --short --branch --ignored`; `Get-Date -Format 'yyyy-MM-dd HH:mm:ss zzz'`; `git config --get user.name`; `git config --get user.email`
- result: required sprint artifacts are present locally; this working directory is now a git repo on `main`; `origin` points to the requested GitHub URL; commit `f7487a2` tracks only the public repo surface; local control files are intentionally ignored; no provider, distro, domain, exact HNG username, or checker public SSH key has been recorded yet
- behavioral outcome: Day 1 session start and Gate A planning are documented locally without fabricating server work, while the public repo stays minimal; live execution remains blocked until provider access and the missing inputs are supplied
- risks or follow-up: do not touch `sshd`, `sudoers`, or `ufw` until a safe current session or provider console path exists
