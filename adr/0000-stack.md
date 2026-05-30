# ADR-0000: swopcart Technology Stack

**Status:** accepted  
**Date:** 2026-01-14

## Context

We need to establish the framework needed for swopcart.

The target hardware we're aiming is an off-the-shelf entry level NAS, which has a low-power ARM64 CPU, 1GB RAM.

It should ship as a single binary or folder to make it easy to deploy for users who want to do things manually, and to simplify packaging for NAS-specific app stores.

The application is expected to run behind a reverse proxy.

The recommended installation path will be via [Docker Compose](https://docs.docker.com/compose/).

The web frontend is likely to be run on capable modern hardware (gaming PCs, handhelds, and modern smartphones), so it would be acceptable to use a single-page application we can embed in the app.

## Decision

### Backend

Use [**Go**](https://go.dev/) with:

- Web: [Gin](https://gin-gonic.com/)
- Database: [GORM](https://gorm.io/) + [PostgreSQL](https://www.postgresql.org/)

Go compiles to native code and is easily cross-compilable with low memory overhead. It's also fairly friendly to both humans and LLMs for development.

### Frontend

For the frontend, use [**TypeScript**](https://www.typescriptlang.org/) with:

- Framework: [React](https://react.dev/)
- Bundler: [Vite](https://vite.dev/)
- UI: [@shadcn/ui](https://ui.shadcn.com/)

## Alternatives Considered

### Backend

- **Python** and **Ruby on Rails** — dismissed early due to memory footprint and packaging complexity concerns.
- [Node.js](https://nodejs.org/en) / [Bun](https://bun.sh/) — using TypeScript on both frontend and backend would allow tight schema coupling between the two, which is desirable since they only interact with each other. [Express](https://expressjs.com/en/) and [Next](https://nextjs.org/) were evaluated as backend options in this context. However, running a JavaScript runtime is too costly for the target hardware, making this a non-starter.
- [ASP.NET](https://dotnet.microsoft.com/en-us/apps/aspnet) — higher memory usage, but can be cross-compiled and gave a lot more built-in things to work on. Go was simpler to get going and distribute.
- [Rust](https://rust-lang.org/) — lower memory, but slower iteration and steeper learning curve for new contributors.

### Database

- [MySQL](https://www.mysql.com/) / [MariaDB](https://mariadb.org/) — more familiar choice, but PostgreSQL was selected to gain experience with it. No significant issues have been encountered; this could be revisited if a strong reason arises.

### Frontend

- [Tailwind](https://tailwindcss.com/) standalone or hand-rolled component-tied stylesheets — both were viable options. shadcn/ui was chosen to gain experience with it; Tailwind comes as a dependency of shadcn rather than a standalone decision.

## Consequences

- Single binary deployment: frontend assets are embedded via `go:embed` and loaded on demand, with the OS swapping them out under memory pressure. The alternative would be shipping assets on disk and loading them at runtime, which complicates distribution.
- Frontend and backend API schema are currently kept in sync manually. The official OpenAPI generator outputs a full web server rather than a router that can be embedded in the app. Using OpenAPI would require building or finding a custom generator. Future work will be needed to define the schema or find another mechanism to simplify remote procedure calls from the frontend.
