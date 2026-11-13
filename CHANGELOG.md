# Changelog

All notable changes to this project are documented here. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Fixed

- `.github/dependabot.yml` no longer declares a package ecosystem in the template itself.
  A template repository has no workflows, so the `github-actions` block made Dependabot's
  update job fail on `main` with `dependency_file_not_found`. The blocks are now commented
  out, to be uncommented in the generated repository.

## [0.1.0] - <date>

First public release.
