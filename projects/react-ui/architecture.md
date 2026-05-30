# react-ui: Architecture

## Package structure

```
src/
  components/ui/    Primitive UI components (Button, Input, Dialog, etc.)
  lib/theme/        Theme system — ThemeProvider, palette generation, types
  hooks/            Shared hooks (use-theme, etc.)
  assets/fonts/     Bundled WOFF2 fonts (Nunito Sans, Geist Mono)
  styles/           Global CSS (Tailwind base, font declarations)
  index.ts          Public API — all exports
```

## Key dependencies

| Dependency | Role |
|---|---|
| shadcn/ui | Component patterns — owned and customised directly, not a runtime dependency |
| Radix UI | Headless, accessible component primitives (used by shadcn/ui) |
| Tailwind CSS | Utility-based styling |
| `culori` | Colour science for theme palette generation |
| Lucide React | Icon set |
| `class-variance-authority` | Component variant definitions |
| `clsx` + `tailwind-merge` | Class name composition |

## Build

Vite builds dual ESM + CJS output with TypeScript declarations. CSS is emitted
separately as `style.css` and must be imported by the consumer.

Storybook is used for component development and visual documentation. It is not
part of the distributed package.

## Theme system

The `ThemeProvider` generates a full colour palette from a base configuration
using `culori`. This allows swop* apps to share the component set while having
distinct but consistent visual identities.
