# agent-skills

Four skills for everyday work, built with [turn-into-skill](https://github.com/ashusevim/turn-into-skill). Each one was checked against its source docs and test-ran before publishing.

## Install

One skill at a time (replace `-a opencode` with your agent):

```bash
npx -y skills add ashusevim/agent-skills -s gmail-api -g -a opencode -y
npx -y skills add ashusevim/agent-skills -s tailwind-utilities -g -a opencode -y
npx -y skills add ashusevim/agent-skills -s postgres-psql -g -a opencode -y
npx -y skills add ashusevim/agent-skills -s github-actions -g -a opencode -y
```

## What each does

**gmail-api** — Send, read, and search Gmail through the API. Base64url sending, drafts, `q` search syntax, minimal OAuth scopes. Source: Google Workspace docs.

**tailwind-utilities** — Day-to-day Tailwind v4: install via Vite, compose utilities in markup, `hover:`/`sm:`/`dark:` variants, arbitrary values, conflict fixes. Source: tailwindcss.com/docs. For design systems (tokens, components), use `wshobson/agents@tailwind-design-system` instead.

**postgres-psql** — From zero to querying: `createdb`, first `psql` session, SELECT with WHERE/ORDER BY/DISTINCT, common errors and fixes. Source: official tutorial chapters 1–2. For query tuning, use `supabase/agent-skills@supabase-postgres-best-practices`.

**github-actions** — First workflows that work: file placement, push triggers, jobs vs steps, `actions/checkout`, reading run logs. Source: GitHub docs quickstart.

For Linear, use `openai/skills@linear` — it already exists and is good, so we didn't duplicate it.

## Updates

Every skill has `version:` and `source:` in its frontmatter plus a changelog. When the source docs change, the skill gets re-ingested and the version bumps.
