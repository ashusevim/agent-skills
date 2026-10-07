---
name: github-actions
version: 1
source: https://docs.github.com/en/actions/writing-workflows/quickstart
description: Ship GitHub Actions workflows. Use when creating a first workflow file, wiring triggers and jobs, using actions/checkout and contexts, reading run logs, or moving from templates to custom CI.
---

# GitHub Actions

Automate on events: workflow file in `.github/workflows` → trigger fires → jobs run on runners → read the logs.

Source: official quickstart. Anatomy + next-moves in `references/anatomy.md`.

## When to use

- First workflow (push-triggered demo → real CI)
- Triggers, jobs, steps, `uses` vs `run`, contexts (`${{ }}`)
- `actions/checkout`, runner choice, log reading
- Templates (`actions/starter-workflows`) → custom workflow

## Instructions

1. **Place it where discovery works.** `.github/workflows/<name>.yml` (or `.yaml`) — anywhere else is invisible to GitHub. Done when: file committed on a branch.
2. **Trigger small, grow later.** Start `on: [push]`; verify green before adding PR paths, schedules, or `workflow_dispatch`. Done when: one push produces one run.
3. **Jobs run, steps do.** `runs-on: ubuntu-latest` per job; steps are `run:` shell lines or `uses:` actions (pin versions: `actions/checkout@v6`). `run-name:` with `${{ github.actor }}` makes runs findable. Done when: steps read top-to-bottom like a script.
4. **Checkout before touching code.** `uses: actions/checkout@v6` clones into `${{ github.workspace }}` — `ls` it first when debugging paths. Done when: a list-files step shows the repo.
5. **Read runs inside-out.** Actions tab → workflow → run → job → expand failing step. Fix the step, not the workflow. Templates for CI/deploy/pages live in `actions/starter-workflows`. Done when: red run names its step.

## References

- `references/anatomy.md` — demo workflow annotated + template map

## Changelog

- v1: initial build from official quickstart
