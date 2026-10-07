# Demo workflow, annotated

```yaml
name: GitHub Actions Demo
run-name: ${{ github.actor }} is testing out GitHub Actions
on: [push]                                   # trigger: any push to the branch
jobs:
  Explore-GitHub-Actions:                    # job id (sidebar label)
    runs-on: ubuntu-latest                   # runner image
    steps:
      - run: echo "triggered by a ${{ github.event_name }} event."  # ${{ }} = context
      - run: echo "running on ${{ runner.os }}, branch ${{ github.ref }}"
      - name: Check out repository code
        uses: actions/checkout@v6            # pinned action, clones repo
      - name: List files in the repository
        run: |
          ls ${{ github.workspace }}         # debug paths here first
      - run: echo "status is ${{ job.status }}."
```

## Template map (`actions/starter-workflows`)

- `ci/` — continuous integration per stack · `deployments/` — ship targets
- `automation/` — repo chores · `code-scanning/` — security
- `pages/` — GitHub Pages · use as-is or as starting points

## Concepts next

Workflows overview → `actions/concepts/workflows-and-actions/workflows` · contexts (`github.actor`, `github.event_name`, …) → contexts reference · matrices/concurrency/CLI → "choose what your workflow does" examples.
