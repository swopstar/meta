# gokit: Roadmap

## Done

- `jobs` — background job scheduler, worker pools, cron scheduling, execution tracking (extracted from swopcart)
- `fsutil` — file system utilities (`EnsureFile`)
- `types` — shared types (`SimpleDate`)
- `testkit` — test harness with transaction-based DB isolation

## Upcoming

- `database` — shared GORM + PostgreSQL setup and auto-migrations (currently duplicated in swopcart and swoptape)
- `auth` — shared JWT and session implementation (currently duplicated in swopcart and swoptape)
