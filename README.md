# swop*

Developer documentation for the swop* suite — a collection of self-hosted media
applications built for personal use.

## Projects

| Project | Description |
|---|---|
| [swopcart](https://github.com/swopstar/swopcart/tree/main/docs) | Self-hosted game library manager |
| [swoptape](https://github.com/swopstar/swoptape/tree/main/docs) | Self-hosted music library manager |
| [gokit](https://github.com/swopstar/gokit/tree/main/docs) | Shared Go infrastructure library (being retired, see [ADR-0001](adr/0001-rust.md)) |
| [react-ui](https://github.com/swopstar/react-ui/tree/main/docs) | Shared React component library |

## Associate Projects

Projects that use swop* resources (such as react-ui) but are not part of the
suite. They follow their own conventions rather than the standards and ADRs
here.

| Project | Description | Uses |
|---|---|---|
| [pmhv](https://github.com/itisrazza/pmhv) | Small daemon and web UI for running VMs on a computer mainly used for something else | react-ui |

## Standards

Cross-project conventions that apply across the suite.

- [Versioning](standards/versioning.md)
- [Commit Conventions](standards/commit-conventions.md)
- [Licensing](standards/licensing.md)

## Architecture Decision Records

- [Suite-wide ADRs](adr/)
- Project-specific ADRs are in each project's repository, under `docs/adr/`

Each project's overview, architecture and roadmap live in its repository, under `docs/`.

## Licence

This repository is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE).

## Design

- [Mockups and design assets](design/)
