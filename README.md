# @autodrive/design-tokens

Shared design tokens for Autodrive frontends. Clinical palette.

## Contents

- `tokens.css` — CSS custom properties (light + dark mode) using HSL components
- `tailwind-preset.cjs` — Tailwind preset wrapping the CSS vars with `hsl(var(--…) / <alpha-value>)`
- `package.json` — installable as a git dependency

## Install (in a consumer repo)

```jsonc
// package.json
{
  "dependencies": {
    "@autodrive/design-tokens": "github:ARX-SOLUTION/autodrive-design-tokens#main"
  }
}
```

```ts
// tailwind.config.ts
import preset from '@autodrive/design-tokens/tailwind-preset';

export default {
  presets: [preset],
  content: ['./index.html', './src/**/*.{ts,tsx}'],
};
```

```css
/* src/index.css (top of file) */
@import '@autodrive/design-tokens/tokens.css';
```

## Adding a new token

1. Add the CSS var to `tokens.css` (both `:root` and `.dark`)
2. Add the Tailwind mapping to `tailwind-preset.cjs`
3. Bump version in `package.json`
4. Commit + push
5. Consumers run `pnpm update @autodrive/design-tokens`

## Why a package, not copy-paste

- Single source of truth
- Versioned change history
- Update propagates to all repos with one command
- Future: published to npm registry if needed

## Roadmap

- v0.1 — Clinical palette (this release)
- v0.2 — Add semantic tokens for chart series
- v1.0 — Dark mode parity audit + lock contract
