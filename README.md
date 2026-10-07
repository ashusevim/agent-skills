# agent-skills

Everyday skills built with [`turn-into-skill`](https://github.com/ashusevim/turn-into-skill). Each directory is one skill: dedup-checked, distilled from official docs, smoke-tested with a live trial.

## Install

```bash
# one skill (pick with -s), scoped to your agent (-a):
npx -y skills add ashusevim/agent-skills -s <skill-name> -g -a <agent> -y
# e.g. -a opencode | -a claude-code | -a cursor
# NOTE: bare -g fans out to all agents incl. PromptScript and fails. Always scope -a.
```

## Skills

| Skill | Does what | Source |
|---|---|---|
| `gmail-api` | Send/read/search Gmail via API (base64url send, `q` search, scopes) | Google Workspace docs |
| `tailwind-utilities` | Daily Tailwind v4: install, compose, variants, arbitrary values | tailwindcss.com/docs |
| `postgres-psql` | Postgres on-ramp: createdb, psql, first SELECTs | Official tutorial ch.1–2 |
| `github-actions` | First workflows: triggers, jobs, checkout, logs | GitHub docs quickstart |

Not here: Linear → use `openai/skills@linear` (exact match, 10K installs). Postgres tuning → `supabase/agent-skills@supabase-postgres-best-practices` (433K). Tailwind systems → `wshobson/agents@tailwind-design-system` (67K).

## Versioning

Each skill carries `version:` + `source:` frontmatter and a Changelog. Updates re-ingest the source and bump the version.
