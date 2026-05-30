# Commit Conventions

All repositories in the swop* suite use [Conventional Commits](https://www.conventionalcommits.org/).

Commit types are load-bearing — they are used to auto-generate release notes, so consistency matters. Use the correct type even for small changes.

## Format

```
type(scope): short description

Optional body explaining the why, not the what.

Optional footer (e.g. breaking change notice).
```

The `scope` is optional. When used, it should name the subsystem or package affected (e.g. `jobs`, `auth`, `scanner`).

## Types

| Type | When to use |
|---|---|
| `feat` | A new feature visible to users or API consumers |
| `fix` | A bug fix |
| `refactor` | Code change that neither adds a feature nor fixes a bug |
| `test` | Adding or updating tests |
| `docs` | Documentation only |
| `chore` | Maintenance tasks (dependency updates, tooling, formatting, renames) |
| `perf` | Performance improvements |
| `ci` | CI/CD pipeline changes |
| `merge` | Merging branches |
| `revert` | Reverting a previous commit |

## Breaking Changes

Append `!` after the type/scope, and include a `BREAKING CHANGE:` footer:

```
feat(auth)!: replace session tokens with JWTs

BREAKING CHANGE: existing sessions are invalidated. Clients must re-authenticate.
```

## Reverting Commits

When reverting, reference the original commit hash(es) in a `Refs:` footer:

```
revert: add experimental caching layer

Refs: 676104e, a215868
```

## Notes

- Subject line should be lowercase and imperative mood: "add", not "adds" or "added"
- No period at the end of the subject line
- Keep the subject line under 72 characters
