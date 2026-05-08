# RezusCloud Design System

Dual-era retro computing visual system. Mac System 1 (1984) for light mode, NeXTSTEP (1988) with teal accent for dark mode. Extracted from [platform-website](https://github.com/rezuscloud/platform-website).

## Quick Start

### Tailwind CSS

Copy `css/rezus.css` to your project and adjust font paths. Import as your Tailwind input:

```css
@import "./rezus.css";
```

### Fonts

Copy `fonts/` to your public assets directory. The CSS expects them at `/fonts/` (adjust the `@font-face` `src` paths in `rezus.css`).

Three font families:

| Font | Purpose | Files |
|------|---------|-------|
| Silkscreen (700) | Headings, labels, nav | `Silkscreen-Regular.woff2`, `Silkscreen-Bold.woff2` |
| system-ui | Body copy | System font, no files needed |
| VT323 | Terminal output | `VT323-Regular.woff2` |

### Tokens

Machine-readable token files in `tokens/`:

| File | Contents |
|------|----------|
| `colors.json` | 22+ oklch color tokens (Mac + NeXT palettes, semantic) |
| `typography.json` | Font families, scale, hierarchy |
| `spacing.json` | Section, nav, button, icon-square spacing |
| `motion.json` | Easings, durations, stagger delays |
| `breakpoints.json` | sm/md/lg breakpoints |

### Components

Self-contained HTML + CSS in `components/`:

| Component | File | Description |
|-----------|------|-------------|
| CTA Button | `cta-button.html` | Primary call-to-action |
| Icon Square | `icon-square.html` | 48x48 accent square with icon |
| Nav Link | `nav-link.html` | Active and inactive nav states |
| Tech Badge | `tech-badge.html` | Technology tag strip |
| Terminal | `terminal.html` | Mac/NeXT terminal container |

Each file is standalone: copy the HTML and `<style>` block into your project.

## Design Rules

1. **Zero border-radius** everywhere. Every corner is a right angle.
2. **Dual-era identity**: Mac System 1 (light) / NeXTSTEP (dark). Fonts consistent, only colors change.
3. **Dual-accent rule**: amber gold (light) / teal (dark). Never mix between modes.
4. **Flat text layout**: no bordered cards, no boxes wrapping content. Icon squares and accent dots punctuate.
5. **2px bevels in NeXT mode**: raised/sunken borders on interactive elements.
6. **No `#000` or `#fff`**: all neutrals are brand-hue tinted (amber 85 for Mac, slate 270 for NeXT).
7. **Alternating backgrounds**: sections alternate paper/surface (Mac), next-black/next-dark (NeXT).
8. **Respect `prefers-reduced-motion`**: all animations have static fallbacks.

Full documentation: [DESIGN.md](DESIGN.md), [PRODUCT.md](PRODUCT.md).

## Projects Using This System

- [platform-website](https://github.com/rezuscloud/platform-website) — source of truth
- [LocalAI](https://github.com/rezuscloud/LocalAI) — AI inference landing page

## License

Design tokens and component code are released under the same license as the platform-website project. Fonts (Silkscreen, VT323) are under their respective open source licenses.
