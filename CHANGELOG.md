# Changelog

All notable changes to this project are documented here. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Changed

- The Dependabot configuration moved from `.github/dependabot.yml` to
  `templates/dependabot.yml`. A template repository has no dependency manifest and no
  workflows of its own, so the live config made Dependabot's update job fail on `main` with
  `dependency_file_not_found` — and an empty `updates:` list is rejected by Dependabot's own
  validator (`'#/updates' did not contain a minimum number of items 1`). It now ships as a
  template asset, next to `templates/ci/`, to be copied to `.github/` in the generated repo.

## [0.1.0] - <date>

First public release.
