# BRB Design System

A lightweight, token-driven design system for the BRB brand. Provides design tokens, component styles, and logo assets sourced directly from the Figma Brand Guidelines.
https://jonmccon.github.io/brb-design-system/

## What's included

```
brb-design-system/
├── tokens.json        # Design tokens as raw JSON (source of truth)
├── tokens.css         # CSS custom properties generated from tokens
├── components.css     # Component styles built on top of the tokens
├── index.html         # Live reference page / style guide
└── logos/             # Logo assets (SVG + PNG + @4x PNG)
```

---

## Getting started

### Option A — Link the CSS files directly

Copy `tokens.css` and `components.css` into your project and link them in your HTML:

```html
<!-- Google Fonts (required) -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Hanken+Grotesk:wght@400;500;600;700;800&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet" />

<!-- BRB Design System -->
<link rel="stylesheet" href="tokens.css" />
<link rel="stylesheet" href="components.css" />
```

> `components.css` already `@import`s `tokens.css`, so linking both is optional — linking only `components.css` is enough.

### Option B — Tokens only

If you only need the design tokens (e.g. in a project with its own component library), link `tokens.css` alone and reference the CSS custom properties in your own styles.

---

## Design tokens

Tokens are defined in `tokens.json` and mirrored as CSS custom properties in `tokens.css`. They cover:

### Color

| Group | Scale steps | Role |
|-------|------------|------|
| Orange | 100–500 | Primary brand color |
| Pink | 100–600 | Accent color |
| Green | 100–500 | Secondary color |
| Blue | 100–500 | Tertiary color |
| Purple | 300–600 | Supporting color |
| Yellow | 100, base, 700 | Supporting color |
| Grey | 100, 300, 700 | Neutral / UI color |

**Semantic aliases** make it easy to use the right color without memorizing scale numbers:

```css
var(--color-primary)          /* orange-300 — main CTA color */
var(--color-primary-light)    /* orange-100 */
var(--color-primary-dark)     /* orange-500 */

var(--color-accent)           /* pink-300 */
var(--color-secondary)        /* green-200 */
var(--color-tertiary)         /* blue-300 */

var(--color-surface)          /* #ffffff */
var(--color-surface-muted)    /* grey-100 */
var(--color-text)             /* grey-700 */
var(--color-text-muted)       /* grey-300 */
var(--color-text-inverse)     /* #ffffff — for use on dark backgrounds */
```

### Typography

Two typefaces are used:

- **Hanken Grotesk** — display and body text (weights 400–800)
- **JetBrains Mono** — monospace / code / labels

```css
var(--font-display)   /* 'Hanken Grotesk', sans-serif */
var(--font-mono)      /* 'JetBrains Mono', monospace  */
```

**Type scale:**

| Token | Size | Pixels |
|-------|------|--------|
| `--text-display` | 3rem | 48px |
| `--text-h1` | 2.25rem | 36px |
| `--text-h2` | 1.5rem | 24px |
| `--text-h3` | 1.25rem | 20px |
| `--text-h4` | 1rem | 16px |
| `--text-body` | 0.875rem | 14px |
| `--text-sm` | 0.75rem | 12px |
| `--text-xs` | 0.625rem | 10px |

### Spacing

4px base grid:

```css
var(--space-1)   /* 4px  */
var(--space-2)   /* 8px  */
var(--space-3)   /* 12px */
var(--space-4)   /* 16px */
var(--space-5)   /* 20px */
var(--space-6)   /* 24px */
var(--space-8)   /* 32px */
var(--space-10)  /* 40px */
var(--space-12)  /* 48px */
var(--space-16)  /* 64px */
```

### Border radius

```css
var(--radius-sm)    /* 4px    */
var(--radius-md)    /* 8px    */
var(--radius-lg)    /* 12px   */
var(--radius-full)  /* 9999px */
```

### Transitions

```css
var(--transition-fast)    /* 120ms ease */
var(--transition-normal)  /* 200ms ease */
```

---

## Components

### Typography classes

Apply typographic styles with utility classes:

```html
<p class="type-display">Display text</p>
<h1 class="type-h1">Heading 1</h1>
<h2 class="type-h2">Heading 2</h2>
<h3 class="type-h3">Heading 3</h3>
<h4 class="type-h4">Heading 4</h4>
<p class="type-body">Body text</p>
<p class="type-body-medium">Body medium weight</p>
<p class="type-sm">Small text</p>
<span class="type-mono">MONO LABEL</span>
<span class="type-mono-sm">Mono small</span>
<span class="type-mono-base">Mono base size</span>
```

### Buttons

All buttons use the base `.btn` class plus a variant modifier. An optional size modifier and shape modifier can be added.

**Variants:**

```html
<button class="btn btn--primary">Primary</button>
<button class="btn btn--accent">Accent</button>
<button class="btn btn--secondary">Secondary</button>
<button class="btn btn--tertiary">Tertiary</button>
<button class="btn btn--purple">Purple</button>

<!-- Outline variants -->
<button class="btn btn--outline-primary">Outline Primary</button>
<button class="btn btn--outline-accent">Outline Accent</button>
<button class="btn btn--outline-secondary">Outline Secondary</button>
<button class="btn btn--outline-tertiary">Outline Tertiary</button>

<!-- Ghost -->
<button class="btn btn--ghost">Ghost</button>
```

**Sizes:**

```html
<button class="btn btn--primary btn--sm">Small</button>
<button class="btn btn--primary">Default</button>
<button class="btn btn--primary btn--lg">Large</button>
```

**Pill shape:**

```html
<button class="btn btn--primary btn--pill">Pill Button</button>
```

**Disabled state:**

```html
<button class="btn btn--primary" disabled>Disabled</button>
<!-- or for non-button elements: -->
<a class="btn btn--primary" aria-disabled="true">Disabled Link</a>
```

---

## Logos

Logo assets are in the `logos/` directory. Each mark is available in three formats:

| File suffix | Format | Use case |
|-------------|--------|----------|
| `.svg` | Vector | Web, print, any scalable context |
| `.png` | Raster 1× | General use |
| `@4x.png` | Raster 4× | High-DPI / retina displays |

### Available marks

| Name | File prefix | Description |
|------|-------------|-------------|
| Little B | `BRB-Logo-LittleB` | Minimal lettermark, ideal for favicons |
| B Stamp | `BRB-Logo-BStamp` | Primary circular badge mark |
| B Stamp + Tagline | `BRB-Logo-BStampTagline` | Primary mark with tagline lockup |
| Badge Small | `BRB-Logo-BadgeSmall` | Compact badge for tight spaces |
| Badge Full | `BRB-Logo-BadgeFull` | Full circular badge with text |

---

## Reference page

Open `index.html` in a browser to view the full living style guide, including:

- All logo marks across light, muted, and dark backgrounds
- Complete color palette with swatches and hex values
- Typography specimens with size, weight, and leading metadata
- All button variants and states
- Full token reference tables

No build step required — just open the file directly or serve it with any static file server:

```bash
npx serve .
# or
python3 -m http.server
```

---

## Figma source

Tokens and assets are sourced from the **BRB — Brand Guidelines** Figma file. When the Figma file is updated, sync changes by:

1. Exporting updated color/typography values and updating `tokens.json`
2. Regenerating `tokens.css` to match
3. Exporting updated logo SVGs into `logos/`
