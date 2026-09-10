# Contributing to ACL Community Content

Thank you for contributing. This is a **public** repository. Merged content is
Apache-2.0 licensed and must meet the same bar as
[acl-ready-to-use-content](https://github.com/redhat-services-platform-team/acl-ready-to-use-content).

Read [docs/specifications.md](docs/specifications.md) before opening a PR.

## Developer Certificate of Origin

Every commit must be signed off (`git commit -s`) to certify the
[Developer Certificate of Origin](https://developercertificate.org/):

```
Signed-off-by: Your Name <you@example.com>
```

Use the name and email associated with your GitHub account.

## What belongs here

Community playbooks and roles that follow GPA, pass ansible-lint `production`,
and have been tested on AAP 2.6+ (or include a Molecule scenario a maintainer
can run). Broader than sales starter-pack content; still not a dumping ground
for unlinted or untested YAML.

## Pull request checklist

- [ ] Playbook under `playbooks/` named `linux-<use-case>.yml` or `win-<use-case>.yml`
- [ ] Tasks live in `roles/<role>/` (thin playbook: hosts, become, facts, `roles:`)
- [ ] Catalog header before `---` (`Playbook:`, `Description:`, `Tags:` including
      `pillar:`, `lifecycle:`, `maturity:`, `Author:`, `Version:`, `Date:`, `License: Apache-2.0`)
- [ ] Role `README.md` with GPA sections and `**Tags:**` line
- [ ] Public vars `{rolename}_*`, internals `__{rolename}_*`
- [ ] `pre-commit run --all-files` (or CI) is green
- [ ] Tested on AAP 2.6+ **or** Molecule scenario documented in the PR
- [ ] No secrets, customer names, or internal-only URLs
- [ ] Commits include `Signed-off-by`

## Workflow

This is a **private** repository. All contributors must be members of the
`redhat-services-platform-team` GitHub org (read access is sufficient to fork
and open a pull request).

1. **Fork the repository** to your personal GitHub account via the GitHub UI
   (your fork will also be private).

2. **Clone your fork** and add the upstream remote:
   ```bash
   git clone https://github.com/<your-github-handle>/acl-community-content.git
   cd acl-community-content
   git remote add upstream https://github.com/redhat-services-platform-team/acl-community-content.git
   ```

3. **Create a branch on your fork** from the latest upstream `main`:
   ```bash
   git fetch upstream
   git checkout -b feat/linux-<your-use-case> upstream/main
   ```
   Branch naming convention:
   - `feat/linux-<use-case>` — new playbook or role
   - `feat/win-<use-case>` — Windows content
   - `fix/<playbook-name>` — bug fix or lint correction
   - `docs/<topic>` — documentation only

4. **Make your changes**, sign each commit:
   ```bash
   git commit -s -m "feat: add RHEL 8 DISA STIG audit playbook"
   ```

5. **Push to your fork** and **open a Pull Request** targeting `main` on the
   upstream repo. Direct pushes to `main` are blocked — all changes must go
   through a PR from a fork branch.

6. **One approval** from an SPT maintainer is required before merge.

## Review

SPT maintainers (`americas-spt`) review and merge. One approval is required on
`main`. Maintainers may ask for lint or test evidence before merge.

> **Branch protection note:** `main` is protected on this private repo —
> direct pushes are blocked and at least one approving review is required.
> This applies to all contributors including maintainers.

Questions: open a GitHub issue (not for security — see [SECURITY.md](SECURITY.md)).
