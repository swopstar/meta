# ADR-R001: react-ui Technology Stack

**Status:** accepted
**Date:** 2026-05-29

## Context

The swop* suite is a family of media library applications — swopcart (games),
swoptape (music), and future additions — spanning web and potentially desktop
(Electron-based) frontends. They are intentionally designed to be near-identical
in structure and interaction: same layout, same navigation chrome, same component
patterns. The only intentional differences are the type of media hosted and the
per-app brand colour.

swopcart originally used shadcn/ui components directly. The result looked
generic — shadcn is widely used and its defaults are recognisable. Bringing
swopcart's frontend in line with the mockups required significant customisation.
react-ui captures that customised layer as the shared starting point, so future
projects begin from the already-customised base rather than vanilla shadcn.

shadcn/ui advocates owning component code directly in each project rather than
importing from a shared library. react-ui adopts this approach but lifts that
ownership to one canonical location, so all swop* projects share the same base
while still owning the component code collectively.

## Decision

Build `@swopstar/react-ui` as a shared React component library using:

- **TypeScript** — consistent with the swop* frontend convention (ADR-0000)
- **React** + **Radix UI** — accessible headless primitives via shadcn/ui
- **Tailwind CSS** — utility styling (comes with shadcn/ui; all consumers have
  Tailwind in their build pipeline)
- **Vite** — library mode build, dual ESM + CJS output with TypeScript
  declarations; CSS emitted separately as `style.css`
- **culori** — colour-science-based palette generation for the theme system,
  enabling per-app brand colours from a single component set
- **Lucide React** — icon set
- **Storybook** — component development and visual documentation environment
- **GitHub Packages** — distribution as a scoped `@swopstar` package

shadcn/ui is used as a starting point and pattern reference, not as a runtime
dependency. Components are owned and customised directly within react-ui to
achieve the design direction drawn from the swopstar mockups.

## Alternatives considered

- **shadcn/ui directly in each app, customised independently** — what swopcart
  originally did. Ruled out because the customisation effort was significant and
  repeating it per-project with no shared base is where drift begins.
- **Custom component library from scratch** — more control, but significantly
  more effort particularly for accessibility. Radix UI solves the hard parts;
  building on top of it is the better trade-off.
- **Tailwind source scanning instead of compiled CSS** — since all consumers have
  Tailwind in their build pipeline, an alternative to shipping a compiled
  `style.css` is to have consumers add the library to their Tailwind `content`
  paths and process classes themselves. This would keep a single Tailwind
  instance in play but couples consumers to the library's source layout. Not yet
  decided; the current implementation emits compiled CSS by default.
- **Direct Git installs** — npm supports installing from a Git tag or branch
  directly, which would avoid a registry entirely. Ruled out because it requires
  consumers to have the full source available locally, which is too much overhead
  for contributors and packagers. See [versioning standards](/standards/versioning.md).
- **npm registry** — a private npm registry would work, but GitHub Packages
  integrates with the existing GitHub-hosted source, reducing moving parts.

## Consequences

- Components are available as soon as they are added but go through a style
  harmonisation phase to bring them in line with the swopstar design direction.
- react-ui is an internal library. Breaking changes will occur without
  deprecation cycles. The MIT licence permits external use, but no API stability
  guarantees are made.
- The theme system (`ThemeProvider` + `culori`) is how per-app brand colours are
  applied — consuming apps pass a palette config, not custom CSS overrides.
- New shared UI components go here first; app-specific variants live in the app.
- Consumers must import both the package and its stylesheet
  (`@swopstar/react-ui/style.css`).
- Storybook is the primary development and documentation environment; it is not
  included in the distributed package.
- Package versioning follows the swopstar versioning standard.
