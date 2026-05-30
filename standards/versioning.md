# Versioning

All versions follow the general shape `a.b.c-d`, where the segments vary by context. See below for the full breakdown per target.

## End-user Applications

Format: `YYMM.RR.PP`

- `YYMM` — 2-digit year + 2-digit month (e.g. `2605` for May 2026)
- `RR` — zero-padded release number within the month, starting at `01`
- `PP` — zero-padded patch number for the release, starting at `00`

```
2605.01.00   ← first release of May 2026
2605.01.01   ← first patch of that release
2605.02.00   ← second release of May 2026
```

## Internal Shared Libraries

Format: `0.YYMM.RR`

The leading `0` signals that these libraries are internal and carry no stability guarantees for external consumers. No patch segment — breaking changes are expected during internal development.

```
0.2605.01   ← first release of May 2026
0.2605.02   ← second release of May 2026
```

If a library is extracted and published for general use, it is relicensed and versioned independently from that point onwards. See [Licensing](licensing.md).

## Public Libraries

[SemVer](https://semver.org/) using `MAJOR.MINOR.PATCH`:

- Bump `MAJOR` for breaking changes
- Bump `MINOR` for backwards-compatible new features
- Bump `PATCH` for backwards-compatible bug fixes

Applies to: any libraries extracted from gokit or react-ui for public consumption.

## API Schema

API schemas are versioned independently from the application using [SemVer](https://semver.org/). The major version is reflected in the URL path (e.g. `/api/v1/`). Minor and patch versions are informational and communicated via response headers or an info endpoint.

- Bump `MAJOR` for breaking changes to the API surface (removed/renamed fields, changed semantics) — this results in a new URL prefix
- Bump `MINOR` for backwards-compatible additions (new endpoints, new optional fields)
- Bump `PATCH` for backwards-compatible fixes (corrected docs, bug fixes with no observable schema change)

The API schema version is independent of the application release version. A `2605.02.00` release may still serve `v1` of the API.

## Build Variants

Build variant suffixes are appended after a `-` separator.

| Variant | Suffix | Example |
|---|---|---|
| Local development | `dev` or `0.0.0` (no suffix) | `dev`, `0.0.0` |
| Nightly | `-$channel-$hash` where `$hash` is the short commit hash | `2605.01.00-nightly-abc1234` |
| Early access | `-ea` | `2605.01.00-ea` |
