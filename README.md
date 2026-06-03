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
| VT323 | Terminal output, code | `VT323-Regular.woff2` |

### Tokens

Machine-readable token files in `tokens/`:

| File | Contents |
|------|----------|
| `colors.json` | 22+ oklch color tokens (Mac + NeXT palettes, semantic) |
| `typography.json` | Font families, scale, hierarchy |
| `spacing.json` | Section, nav, button, icon-square, sidebar, table, dialog, alert, toast spacing |
| `motion.json` | Easings, durations, stagger delays, component animations |
| `breakpoints.json` | sm/md/lg breakpoints |
| `forms.json` | Input heights, padding, focus rings, toggle/checkbox/radio sizing |
| `z-index.json` | Layer ordering (base through max) |

### Components

Self-contained HTML + CSS in `components/`. Each file is standalone: copy the HTML and `<style>` block into your project.

#### Brand Components (marketing, landing pages)

| Component | File | Description |
|-----------|------|-------------|
| CTA Button | `cta-button.html` | Primary call-to-action |
| Accent Bar | `accent-bar.html` | Section heading underline (3 sizes) |
| Accent Dot | `accent-dot.html` | List bullet, status marker (2 sizes + active pulse) |
| Section Badge | `section-badge.html` | Section label with `//` separator |
| Terminal | `terminal.html` | Mac/NeXT terminal container with typewriter |

#### Product Components (dashboard, console, app UI)

| Component | File | Description |
|-----------|------|-------------|
| Text Input | `text-input.html` | Label, input, help/error states, disabled |
| Text Area | `textarea.html` | Multi-line code input (VT323 monospace) |
| Select | `select.html` | Dropdown with custom chevron |
| Checkbox | `checkbox.html` | Checked, unchecked, disabled states |
| Radio | `radio.html` | Single-selection radio group |
| Toggle | `toggle.html` | On/off switch (NeXTSTEP-style) |
| Search | `search.html` | Resource search with keyboard hint |
| Tabs | `tabs.html` | Content tab navigation |
| Alert Banner | `alert-banner.html` | Info, positive, negative system alerts |
| Toast | `toast.html` | Ephemeral notification (positive/negative) |
| Progress Bar | `progress-bar.html` | Determinate progress with danger variant |
| Accordion | `accordion.html` | Collapsible sections |
| Dialog | `dialog.html` | Modal with title bar, body, actions |
| Sidebar | `sidebar.html` | App navigation with icon links |
| Breadcrumb | `breadcrumb.html` | Hierarchy path navigation |
| Pagination | `pagination.html` | Page navigation with ellipsis |
| Data Table | `data-table.html` | Bordered table with status indicators |
| Code Snippet | `code-snippet.html` | Code block with filename header and copy button |
| Empty State | `empty-state.html` | Centered placeholder with icon and CTA |
| Skeleton | `skeleton.html` | Loading placeholder with pulse animation |
| Status Dot | `status-dot.html` | Colored square for resource health (positive/negative/neutral) |

#### Shared Components (both registers)

| Component | File | Description |
|-----------|------|-------------|
| Nav Link | `nav-link.html` | Active and inactive nav states |
| Icon Square | `icon-square.html` | 48x48 accent square with icon |
| Tech Badge | `tech-badge.html` | Technology tag strip |
| Dropdown | `dropdown.html` | Floating context menu with danger variant |
| Command Palette | `command-palette.html` | ⌘K keyboard launcher |

### References

| File | Contents |
|------|----------|
| `references/layout-patterns.md` | Console page composition patterns (page shell, resource list, detail view, form, terminal) |
| `references/responsive.md` | Breakpoint rules and mobile adaptations per component |
| `references/interactive-states.md` | Complete state matrix (default, hover, active, focus, disabled, loading, selected, error) |
| `references/contrast-audit.md` | WCAG AA contrast ratios for all foreground/background pairs |

## Design Rules

1. **Zero border-radius** everywhere. Every corner is a right angle.
2. **Dual-era identity**: Mac System 1 (light) / NeXTSTEP (dark). Fonts consistent, only colors change.
3. **Dual-accent rule**: amber gold (light) / teal (dark). Never mix between modes.
4. **Flat text layout**: no bordered cards, no boxes wrapping content. Icon squares and accent dots punctuate.
5. **2px bevels in NeXT mode**: raised/sunken borders on interactive elements.
6. **No `#000` or `#fff`**: all neutrals are brand-hue tinted (amber 85 for Mac, slate 270 for NeXT).
7. **Alternating backgrounds**: sections alternate paper/surface (Mac), next-black/next-dark (NeXT).
8. **Respect `prefers-reduced-motion`**: all animations have static fallbacks.
9. **Use the spacing scale**: base values in `tokens/spacing.json`, CSS variables in `css/theme.css`.
10. **Use the type scale**: steps 1–8 in `tokens/typography.json`.
11. **Four semantic colors**: positive, warning, negative, info. Each has a Mac and NeXT variant.
12. **Use accent-gold-dark for text**: accent-gold is too light for text on paper (fails AA).

Full documentation: [DESIGN.md](DESIGN.md), [PRODUCT.md](PRODUCT.md).

## Projects Using This System

- [platform-website](https://github.com/rezuscloud/platform-website) — source of truth
- [LocalAI](https://github.com/rezuscloud/LocalAI) — AI inference landing page
- [rezuscloud/web-ui](https://github.com/rezuscloud/web-ui) — platform console (in development)

## License

Design tokens and component code are released under the same license as the platform-website project. Fonts (Silkscreen, VT323) are under their respective open source licenses.
