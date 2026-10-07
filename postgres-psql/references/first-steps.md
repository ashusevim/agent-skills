# First steps

## Create + connect

```bash
createdb mydb      # silent = success; bare `createdb` uses OS username
psql mydb          # no name = OS-username db; `=>` prompt, `=#` = superuser
dropdb mydb        # destroys everything, no undo — always name it explicitly
```

## Error → fix

| Error | Fix |
|---|---|
| `command not found` | Postgres not installed or not on PATH (`/usr/local/pgsql/bin/…`) |
| socket `…5432 failed` | server not started / wrong socket dir |
| `FATAL: role "x" does not exist` | no PG user (admin creates; or `-U`/`PGUSER`) |
| `permission denied to create database` | user lacks CREATEDB — admin grants |

## psql survival

`SELECT version();` smoke test · `\h` SQL syntax · `\?` all meta-commands · `\q` quit · semicolon ends statements.

## First queries (weather-table pattern)

```sql
SELECT * FROM weather;                                            -- ad-hoc only
SELECT city, (temp_hi+temp_lo)/2 AS temp_avg, date FROM weather;  -- expr + label
SELECT * FROM weather WHERE city='San Francisco' AND prcp > 0.0; -- qualify
SELECT * FROM weather ORDER BY city, temp_lo;                     -- break ties
SELECT DISTINCT city FROM weather ORDER BY city;                   -- dedupe, deterministic
```
