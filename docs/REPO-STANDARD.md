# The public-repository standard

One page. A repository is "public and done" when every line below is true. The file half is
in this template; the settings half is applied by `open-source-kit/lib/apply-settings.sh` and
verified by `open-source-kit/lib/check-standard.sh`.

## Files

- `LICENSE` (Apache-2.0, byte-identical to the template) and `NOTICE`.
- `README.md` with: what it is, quick start, usage, configuration, development, security,
  contributing, licence. Badges for CI and licence at the top.
- `CHANGELOG.md`, and a `vX.Y.Z` tag with a GitHub Release.
- `.github/dependabot.yml` for every package manager the repo uses.
- `.github/CODEOWNERS`.
- `.github/ISSUE_TEMPLATE/` (not inherited from the organisation repo).
- `SECURITY.md` when the repository has a supported-versions story or a scope worth naming;
  otherwise the organisation default applies.
- `CONTRIBUTING.md` when the repository has real setup/test commands; otherwise the
  organisation default applies.
- `scripts/ci/no-private-refs.sh` + `.betterleaks.toml` + `.betterleaksignore`.
- A CI workflow that runs on `ubuntu-latest` and uses no secrets.

## Settings

| Setting | Value |
|---|---|
| Description | one line, what + for whom, no trailing period |
| Topics | 5–8 lowercase hyphenated, matching the package keywords |
| Secret scanning + push protection | enabled |
| Dependabot alerts + security updates | enabled |
| Private vulnerability reporting | enabled |
| Code scanning (CodeQL default setup) | configured |
| Wiki / Projects | off |
| Delete branch on merge, auto-merge | on |
| Merge methods | squash + rebase, merge commit off |
| Web commit sign-off | required |
| Branch ruleset `main` | PR required, strict required checks, dismiss stale reviews on push, no force-push, 0 required approvals |

Required status checks are **discovered from the check-runs that actually ran**, never
hand-written: a context that never reports blocks every merge.

Not available on this Free org (measured 2026-11-13): organisation rulesets, code-security
configurations, secret-scanning non-provider patterns and validity checks. Do not spend time
re-trying them; the API accepts the request and leaves the setting disabled.

## Process

1. `git bundle create <name>-all-refs.bundle --all` before anything moves.
2. `open-source-kit/lib/prep.sh` to make the tree publishable; scrub by hand until
   `readiness.sh` exits 0.
3. Create the public repo, push one orphan commit of the scrubbed tree.
4. `apply-settings.sh --apply` for the repository.
5. Watch the first CI run — it cannot run while the repo is private (Actions billing).
6. `check-standard.sh <repo>` must exit 0.
7. Cut `v0.1.0` with `release.sh`.
8. Rename the private repo to `<name>-archive` and archive it.
