---
name: postgres-psql
version: 1
source: https://www.postgresql.org/docs/current/tutorial.html
description: Get going with PostgreSQL and psql. Use when creating databases with createdb, connecting with psql, running first SELECT queries with WHERE/ORDER BY/DISTINCT, reading access errors, or learning where joins and aggregates live in the tutorial.
---

# Postgres psql

From zero to querying: `createdb` → `psql` → SELECT with qualifications. Optimization work belongs to `supabase/agent-skills@supabase-postgres-best-practices` (433K installs) — this is the on-ramp.

Source: official tutorial ch. 1–2 (PG 18). Command reference in `references/first-steps.md`.

## When to use

- Creating/dropping databases, first `psql` session
- SELECT with WHERE, ORDER BY, DISTINCT, expressions + AS labels
- Diagnosing `command not found` / socket / role-missing / permission errors
- Finding the tutorial chapter for joins, aggregates, updates, views, transactions

## Instructions

1. **Create before connecting.** `createdb mydb` (no output = success; name defaults to OS user; `dropdb` destroys, no undo). `role X does not exist` → PG user missing (admin creates it, or `-U`/`PGUSER`); socket error → server not running; `command not found` → fix PATH. Done when: `createdb` silent.
2. **Enter psql, learn the prompt.** `psql mydb` (defaults to OS-user-named db). `=>` normal, `=#` superuser. `SELECT version();` proves the session. Meta: `\h` SQL help, `\?` psql help, `\q` quit. Done when: a query returns a row.
3. **Query in layers.** `SELECT * FROM t` (ad-hoc only — never production) → named columns → expressions with `AS` → `WHERE` (AND/OR/NOT) → `ORDER BY col [, col2]` (ties need both keys) → `DISTINCT` (+ ORDER BY for determinism). Done when: each layer returns the expected rows on the weather-table pattern.
4. **Grow via the map, not memory.** Joins → ch.2.6, aggregates → 2.7, updates/deletes → 2.8–2.9, views/FKs/transactions/window → ch.3. Done when: the next topic names its chapter.

## References

- `references/first-steps.md` — createdb/psql commands, error table, first queries

## Changelog

- v1: initial build from official tutorial (getting started + querying chapters)
