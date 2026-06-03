# Interactive States — RezusCloud Design System

Complete state matrix for interactive components. Every interactive element must define these states.

## State Definitions

| State | Trigger | Visual Expression (Mac) | Visual Expression (NeXT) |
|-------|---------|------------------------|--------------------------|
| **Default** | Initial render | Base styles | Base styles |
| **Hover** | Mouse hover | Background shift, border accent | Background shift, bevel highlight |
| **Active/Pressed** | Mouse down | `translateY(1px)` + background darken | `translateY(1px)` + inverted bevel |
| **Focus** | Keyboard tab | 2px accent-gold outline, 2px offset | 2px next-light outline, 2px offset |
| **Disabled** | `aria-disabled="true"` | 50% opacity, `cursor: not-allowed` | 50% opacity, `cursor: not-allowed` |
| **Loading** | Async action in progress | Skeleton pulse on content area | Skeleton pulse on content area |
| **Selected** | Multi-select toggle | Ink background, paper text | Next-mid background, next-white text |
| **Error** | Validation failure | Negative border color | Negative border color |

## Component State Matrix

### CTA Button
- **Default:** ink bg (Mac) / next-teal-hi bg (NeXT)
- **Hover:** accent-gold bg, ink text (Mac) / next-mid bg (NeXT)
- **Active:** `translateY(1px)` physical press
- **Focus:** `focus-visible` ring
- **Disabled:** 50% opacity, `pointer-events: none`

### Text Input / Text Area / Select
- **Default:** paper bg, rule border (Mac) / next-black bg, sunken bevel (NeXT)
- **Hover:** Slight border darkening
- **Focus:** border → ink (Mac) / top-left bevel → next-teal (NeXT)
- **Disabled:** 50% opacity, `cursor: not-allowed`, value persists
- **Error:** border → negative color, error message below in negative color

### Checkbox / Radio
- **Default:** paper bg, rule border (Mac) / next-black bg, raised bevel (NeXT)
- **Checked:** ink fill, paper checkmark (Mac) / next-teal-hi fill (NeXT)
- **Disabled:** 50% opacity, no interaction
- **Error:** border → negative color (validation group)

### Toggle
- **Default:** rule track, paper thumb (Mac) / next-mid sunken track (NeXT)
- **On:** ink track, paper thumb (Mac) / next-teal track (NeXT)
- **Disabled:** 50% opacity, `cursor: not-allowed`

### Tabs
- **Default:** transparent bg, muted text
- **Active:** accent bottom border (ink / next-teal)
- **Hover:** text brightens, subtle bg tint
- **Disabled:** 40% opacity, `cursor: not-allowed`

### Data Table Rows
- **Default:** alternating backgrounds
- **Hover:** surface / next-mid background
- **Selected:** ink bg, paper text (Mac) / next-mid bg, next-white text (NeXT). Use `.ds-table-row--selected` class.
- **Loading:** Replace row content with Skeleton component

### Nav Links
- **Default:** muted text, transparent bg
- **Active:** pill background (paper / next-light)
- **Hover:** surface / next-mid background
- **Current section:** Same as active (driven by IntersectionObserver)

### Dropdown Items
- **Default:** transparent bg
- **Hover:** surface / next-mid background
- **Active:** surface-strong / next-dark background (mouse down)
- **Disabled:** 40% opacity, `pointer-events: none`
- **Danger variant:** negative text color, tinted bg on hover

### Command Palette Items
- **Default:** transparent bg
- **Hover:** surface / next-mid background
- **Active (keyboard):** same as hover, driven by arrow key navigation
- **Selected:** Enter key triggers action

### Dialog Buttons
- **Primary:** Same as CTA Button states
- **Secondary:** surface bg, rule border (Mac) / next-mid bg, raised bevel (NeXT)
- **Secondary Hover:** ink bg, paper text (Mac) / next-dark bg (NeXT)
- **Disabled:** 50% opacity

## Loading Patterns

### Button Loading
Replace button text with a VT323 animation: `Loading...` with a blinking dot. Button becomes non-interactive. Width stays the same.

```html
<button class="ds-cta" disabled>
  <span class="ds-loading-text">Loading<span class="ds-loading-dots">...</span></span>
</button>
```

```css
.ds-loading-dots {
  animation: ds-loading-blink 1s step-end infinite;
}
@keyframes ds-loading-blink {
  0%, 33% { opacity: 1; }
  34%, 100% { opacity: 0; }
}
```

### Table Loading
Replace table body with Skeleton rows matching column count.

### Page Loading
Full-page Skeleton matching the expected layout structure.

## Selected State for Data Table

Add to `.ds-table-row`:

```css
.ds-table-row--selected {
  background: oklch(14% 0.008 65) !important;
  color: oklch(99.5% 0.004 85);
}
.dark .ds-table-row--selected {
  background: oklch(34% 0.006 270) !important;
  color: oklch(88% 0.004 270);
}
```

Use with checkbox in first column for multi-select. Selected row + checked checkbox = confirmed selection.
