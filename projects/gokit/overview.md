# gokit: Overview

gokit is the shared Go infrastructure library for the swop* suite. It contains
common primitives and utilities extracted from swop* applications so they can be
used across swopcart, swoptape, and any future projects without duplication.

It is an internal library — no API stability guarantees are made. See
[Versioning](../../../standards/versioning.md) and
[Licensing](../../../standards/licensing.md) for details.

## Packages

| Package | Description |
|---|---|
| `jobs` | Background job scheduler, worker pools, and execution tracking |
| `fsutil` | File system utilities |
| `types` | Shared types (e.g. `SimpleDate` for YYYY-MM-DD dates) |
| `testkit` | Test harness with database transaction rollback for isolated tests |

## Planned Packages

| Package | Description |
|---|---|
| `database` | Shared database connection and migration logic |
| `auth` | Shared JWT and session implementation |
