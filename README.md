# repo-template

The starting point for a new **public** repository in `nonagenticai`. Use it as a GitHub
template (`gh repo create nonagenticai/<name> --template nonagenticai/repo-template
--public`) or copy the files you need.

The organisation-level defaults — `SECURITY.md`, `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`,
`SUPPORT.md` and the pull request template — live in
[`nonagenticai/.github`](https://github.com/nonagenticai/.github) and are applied by GitHub
to any repository that does not define its own. This template therefore carries only what is
**per repository**.

## What is here

| Path | Use |
|---|---|
| `LICENSE`, `NOTICE` | Apache-2.0. Fill in `<Project>`/`<year>` in `NOTICE`; keep `LICENSE` verbatim. |
| `CHANGELOG.md` | Keep a Changelog. The first public release is `0.1.0`. |
| `templates/dependabot.yml` | Copy to `.github/dependabot.yml` in the new repo. Uncomment the ecosystem(s) it uses; delete the rest. It is not live in *this* repository — a template has no manifest, and Dependabot rejects a config with zero ecosystems. |
| `.github/CODEOWNERS` | Default owner. |
| `.github/ISSUE_TEMPLATE/`, `.github/PULL_REQUEST_TEMPLATE.md` | Issue templates are **not** inherited from the organisation repo, so copy these in. The PR template here is the same one the organisation supplies. |
| `.betterleaks.toml`, `.betterleaksignore` | Secret-scan configuration. |
| `scripts/ci/no-private-refs.sh`, `.ci/private-refs.allow` | The private-infrastructure guard. Run it before every push. |
| `.editorconfig`, `.gitattributes`, `.gitignore` | Baseline hygiene. Extend the ignore list for the ecosystem. |
| `templates/README.project.md` | The README skeleton — copy it to `README.md` in the new repo and fill it in. |
| `templates/ci/{python,rust,ts}.yml` | The public CI workflow for each archetype. Copy one to `.github/workflows/ci.yml`. |
| `docs/REPO-STANDARD.md` | The one-page rubric: what "done" means for a public repository. |

## Before the first push

1. Copy `templates/README.project.md` to `README.md` and fill every placeholder. A README
   with `<Project>` still in it is worse than no README.
2. Copy the matching `templates/ci/*.yml` to `.github/workflows/ci.yml` and change the
   commands to the repository's real ones.
3. Fill `.ci/private-refs.allow` only with justified entries, and run
   `bash scripts/ci/no-private-refs.sh`.
4. Read `docs/REPO-STANDARD.md` and apply it — the settings half is automated by
   `open-source-kit/lib/apply-settings.sh`.

## A note on forks

This template is for repositories this organisation owns. Never use it on a fork of
someone else's project: their security policy, contribution rules and licence are theirs.

## Licensing

The template itself is scaffolding, not a running service: it carries no licence-enforcement
code, and the Apache-2.0 licence in [`LICENSE`](LICENSE) is the only licence that applies.
Repositories created from it are Apache-2.0 and must state their own licensing posture in a
`## Licensing` section — which switch (if any) the code reads, what its default is, and that
the code runs without a licence server.

## License

Apache-2.0 — see [`LICENSE`](LICENSE) and [`NOTICE`](NOTICE).
