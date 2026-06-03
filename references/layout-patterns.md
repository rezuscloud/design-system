# Layout Patterns — RezusCloud Design System

Composition patterns for building console pages. Each pattern combines multiple components into a working page structure.

## 1. Page Shell

The standard console page layout: sidebar + header + content + optional status bar.

```
┌──────────────────────────────────────────────┐
│ Sidebar (14rem)  │  Header / Breadcrumb      │
│                  │────────────────────────────│
│  Logo            │                            │
│  ─────────       │  Content area              │
│  Nav item        │  (scrollable)              │
│  Nav item (act.) │                            │
│  Nav item        │                            │
│  Nav item        │                            │
│                  │                            │
│  ─────────       │                            │
│  Version string  │                            │
└──────────────────────────────────────────────┘
```

**Implementation:**
- Sidebar: `components/sidebar.html` — fixed width 14rem, full viewport height
- Header: breadcrumb + page title + action buttons, sticky with `border-bottom`
- Content: `padding: var(--spacing-6)` minimum, max-width 80rem
- Background alternation does NOT apply inside the console (only on marketing pages)

**CSS Grid layout:**
```css
.page-shell {
  display: grid;
  grid-template-columns: 14rem 1fr;
  grid-template-rows: auto 1fr;
  min-height: 100vh;
}
.page-shell-header {
  grid-column: 2;
  position: sticky;
  top: 0;
  z-index: 200; /* z-sticky */
}
```

## 2. Resource List

The most common console page: search + filter bar + data table + pagination.

```
┌──────────────────────────────────────────────┐
│  Page Title                    [+ New] button │
│──────────────────────────────────────────────│
│  [Search...]          [Filter ▼] [Filter ▼]  │
│──────────────────────────────────────────────│
│  Name        Status    CPU    Memory  Region  │
│  control-01  Ready     12%    2.1GB   eu-west │
│  worker-01   Ready     67%    14.3GB  eu-west │
│  worker-02   Pressure  94%    28.7GB  eu-west │
│──────────────────────────────────────────────│
│  Showing 1-4 of 12       [← 1 2 3 →]        │
└──────────────────────────────────────────────┘
```

**Components:** Search, Dropdown (for filters), Data Table, Pagination, Status Dot

**Responsive:** At mobile (<768px), the data table scrolls horizontally. Consider a card-list view for narrow screens where columns exceed 4.

## 3. Detail View

A resource detail page: breadcrumb + header with actions + tabbed content.

```
┌──────────────────────────────────────────────┐
│  Clusters / production-eu                    │
│──────────────────────────────────────────────│
│  ● production-eu                    [Actions]│
│  3 nodes · eu-west · healthy                 │
│──────────────────────────────────────────────│
│  Overview  Nodes  Workloads  Logs  Settings  │
│  ════════                                     │
│                                              │
│  Tab content area                            │
│                                              │
└──────────────────────────────────────────────┘
```

**Components:** Breadcrumb, Tabs, Dropdown (for actions), Status Dot

**Layout:** The tab strip uses `border-bottom` to separate from content. The active tab has an accent-colored bottom border (ink in Mac, teal in NeXT).

## 4. Form Pattern

Configuration and settings pages: section headers, field groups, validation, submit bar.

```
┌──────────────────────────────────────────────┐
│  Cluster Settings                            │
│──────────────────────────────────────────────│
│  GENERAL                                     │
│  ─────────                                   │
│  Cluster Name                                │
│  [production-eu        ]                     │
│                                              │
│  Region                                      │
│  [Europe West      ▼  ]                      │
│                                              │
│  NETWORKING                                  │
│  ─────────                                   │
│  Enable Mesh                            [○]  │
│  Mesh Type                                   │
│  [Istio        ▼  ]                          │
│                                              │
│──────────────────────────────────────────────│
│                    [Cancel]  [Save Changes]   │
└──────────────────────────────────────────────┘
```

**Components:** Text Input, Select, Toggle, CTA Button, Section Badge (for group headers)

**Submit bar:** Sticky at bottom on long forms. Background: surface-strong (Mac) / next-dark (NeXT) with top border.

**Validation:** Error state shifts border to negative color. Help text below field shows error message in negative color.

## 5. Terminal / Log View

Dedicated view for streaming output: terminal container fills the content area.

```
┌──────────────────────────────────────────────┐
│  ▤ rezusctl logs — worker-01         [Copy]  │
│──────────────────────────────────────────────│
│  $ rezusctl logs --follow worker-01          │
│  2024-01-15T08:23:01Z Starting health check  │
│  2024-01-15T08:23:02Z Health check passed    │
│  2024-01-15T08:23:05Z Received SIGTERM       │
│  2024-01-15T08:23:05Z Graceful shutdown...   │
│  _                                           │
└──────────────────────────────────────────────┘
```

**Components:** Terminal, Code Snippet (for copy button pattern)

**Layout:** Terminal container fills available height. VT323 monospace throughout. Dark background in both modes (terminal is always dark).

## Register Mixing Rule

When building console pages (product register), brand components may appear in these specific contexts:
- **Terminal** is allowed in console detail views (log output, boot sequences)
- **Accent Bars** may appear as section dividers in overview dashboards
- **Section Badges** may label console page sections

Brand components that should NOT appear in console pages:
- CTA Button (use Dialog primary button instead)
- Use Case Cards (marketing-only)

Product components may appear on the marketing site (brand register):
- Data Table (for the comparison section)
- Code Snippet (for installation instructions)
- Accordion (for FAQ sections)
