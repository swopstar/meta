# react-ui: Overview

react-ui (`@swopstar/react-ui`) is the shared React component library for the
swop* suite. It provides a consistent design language across swopcart, swoptape,
and any future swop* frontends.

It takes a middle ground between using shadcn/ui directly and building from
scratch. [shadcn/ui](https://ui.shadcn.com/) advocates owning the components
directly in each project — react-ui does the same, but shares that ownership
across all swop* projects via a package. A custom design is applied on top so the applications have a distinctive look
rather than the generic shadcn defaults. The design direction is drawn from the
mockups in [swopstar-meta](../../../design/mockups/).

It is an internal library built with swoptape first, then backported to swopcart.
See [Versioning](../../../standards/versioning.md) and
[Licensing](../../../standards/licensing.md) for details.

## What it provides

- **Components** — accessible UI primitives built on Radix UI and styled with
  Tailwind CSS: buttons, inputs, dialogs, cards, dropdowns, and more
- **Theme system** — a `ThemeProvider` with palette generation via colour science
  (`culori`), allowing swop* apps to share a consistent but customisable look
- **Typography** — bundled fonts: Nunito Sans (body) and Geist Mono (monospace)
- **Icons** — via Lucide React
- **Storybook** — component development and documentation environment

## Distribution

Published as a scoped package (`@swopstar/react-ui`) to GitHub Packages.
Consumers import components and must also import the stylesheet:

```ts
import { Button } from '@swopstar/react-ui'
import '@swopstar/react-ui/style.css'
```
