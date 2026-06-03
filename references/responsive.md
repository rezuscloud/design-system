# Responsive Guidance — RezusCloud Design System

Breakpoints and mobile adaptation rules per component. The system defines three breakpoints:

| Name | Value | Target |
|------|-------|--------|
| sm   | 640px | Mobile phones |
| md   | 768px | Tablets portrait |
| lg   | 1024px | Desktop and above |

## Console Layout (Product Register)

### Page Shell
- **≥1024px (lg):** Full sidebar visible (14rem) + content area
- **768–1023px (md):** Sidebar collapses to icon-only column (3rem). Labels hidden. Expand on hover.
- **<768px (sm):** Sidebar hidden. Bottom tab navigation or hamburger menu. Content full-width.

### Sidebar
- **≥1024px:** Full sidebar with labels
- **768–1023px:** Icon-only rail. Tooltips (Tooltip component) on hover showing label text
- **<768px:** Off-screen drawer, triggered by hamburger. Slides in from left with backdrop overlay.

### Data Table
- **≥768px:** Full table with all columns visible. Horizontal scroll on overflow.
- **<768px:** Two options:
  1. Horizontal scroll wrapper (current: `overflow-x: auto` on `.ds-table-wrapper`)
  2. Card-list mode: each row becomes a stacked card with label–value pairs
  Prefer horizontal scroll for tables with ≤5 columns. Switch to card-list for ≥6 columns or when critical columns are <100px wide on mobile.

### Tabs
- **≥768px:** Horizontal tab strip with bottom border
- **<768px:** Scrollable horizontal tabs with fade-out mask on right edge. No wrapping. Alternatively, convert to a Select dropdown on mobile.

### Search
- **≥768px:** Full search bar with keyboard hint
- **<768px:** Search collapses to icon-only button. Expands to full-width search bar on tap/activation.

### Pagination
- **≥768px:** Full button strip with page numbers
- **<768px:** Simplified: `[← Prev] Page 3 of 12 [Next →]`. Drop numbered page buttons.

### Dialog
- **≥768px:** Centered modal, max-width 28rem
- **<768px:** Full-width, positioned at bottom of viewport (sheet pattern). Min-height 50vh with drag handle.

### Breadcrumb
- **≥768px:** Full path visible
- **<768px:** Show only the parent page name with back chevron. E.g., `← Clusters` instead of `Clusters / production-eu / Settings`.

### Command Palette
- **All sizes:** Full-width on mobile (with padding), centered modal on desktop. Input and keyboard shortcuts remain the same.

### Dropdown
- **All sizes:** Same behavior. On mobile, ensure touch targets are ≥44px height per item. The dropdown width should not exceed viewport width minus 1rem margin.

### Forms
- **≥768px:** Labels left of inputs (inline) for simple forms, or stacked (label above input) for complex forms
- **<768px:** Always stacked. Full-width inputs. Toggle/checkbox groups stack vertically.

## Marketing Site (Brand Register)

### Navigation
- **≥768px:** Desktop horizontal nav with fixed top bar
- **<768px:** Hamburger menu with slide-down panel (current implementation)

### Hero Section
- **≥1024px:** Large display text (step-8: 6rem), full hero composition
- **768–1023px:** Display text scales down with `clamp(3rem, 8vw, 6rem)`
- **<768px:** Display text `clamp(2.5rem, 10vw, 4rem)`. Stack hero elements vertically. Terminal container full-width.

### Feature Grids
- **≥1024px:** 2-column grid
- **768–1023px:** 2-column grid with reduced padding
- **<768px:** Single column stack

### Comparison Table
- **≥768px:** Full table with all columns
- **<768px:** Horizontal scroll wrapper. First column (feature label) sticky with `position: sticky; left: 0; z-index: 1`.

### Use Case Cards
- **≥1024px:** Vertical stack with `space-y-10` spacing
- **<768px:** Reduced spacing. Icon squares may shrink to secondary size (2.5rem).

## General Responsive Rules

1. **Never shrink below readable size.** Minimum body text: 0.8125rem (13px). Minimum Silkscreen label: 0.625rem (10px).
2. **Touch targets ≥44px** on all interactive elements when the device viewport is <768px.
3. **Horizontal scroll is acceptable** for data tables. Card-list is the mobile alternative.
4. **No border-radius changes** at any breakpoint. Zero radius at all sizes.
5. **Bevel system persists** at all sizes. The NeXT aesthetic does not degrade on mobile.
6. **Background alternation** continues on mobile. Section padding reduces (use spacing-8 on mobile vs spacing-16 on desktop).
