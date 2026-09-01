# For anyone (human or agent) working in this repo

## This repo is a GitHub fork — `gh` targets the wrong repo by default

This repository (`Catchswim/catch-health-plugin`) is a fork of
`carp-dk/carp-health-flutter`. Because of the fork link, the GitHub CLI
(`gh`) resolves the **upstream project's repo** as its default target — so
`gh pr create` run here opens the PR on their repository, not ours. The same
mistake has already happened twice in the sibling
`flutter_workout_bridge-watchos11` fork.

Rules:

- In a fresh clone, run `gh repo set-default Catchswim/catch-health-plugin`
  before any other `gh` command. The setting is local and does not travel
  with clones.
- Pass `--repo Catchswim/catch-health-plugin` explicitly on any `gh` command
  that creates, merges, comments, or closes anything.
- Check the URL `gh` prints back. If it does not contain `Catchswim/`, stop
  and undo before doing anything else.

## What this plugin is to CatchSwim

The `health` package fork that adds Apple HealthKit push support. The
CatchSwim app (`Catchswim/catch_swim`) builds against it **only for iOS**,
via a gitignored `pubspec_overrides.yaml` written by
`tool/set_health_dependency.sh ios` — the committed default is the public
pub.dev `health` package, because this fork does not build on Android. Never
commit this fork as the app's default dependency.
