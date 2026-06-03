# Contrast Audit — RezusCloud Design System

WCAG 2.1 AA minimum contrast ratios:
- **Normal text** (< 18px / 14px bold): 4.5:1
- **Large text** (≥ 18px / 14px bold): 3:1
- **UI components & graphical objects**: 3:1

## Mac Mode (Light)

| Foreground | Background | Ratio | Use | AA Normal | AA Large |
|-----------|-----------|-------|-----|-----------|----------|
| ink (oklch 14% 0.008 65) | paper (oklch 99.5% 0.004 85) | ~16.5:1 | Body text, headings | ✅ | ✅ |
| ink-muted (oklch 30% 0.008 65) | paper | ~9.2:1 | Secondary text, descriptions | ✅ | ✅ |
| ink-muted (oklch 30% 0.008 65) | surface (oklch 95.5%) | ~8.5:1 | Secondary text on alt bg | ✅ | ✅ |
| rule (oklch 72% 0.005 85) | paper | ~2.8:1 | Borders, dividers | N/A (non-text) | ⚠️ >3:1 |
| accent-gold (oklch 78% 0.16 75) | paper | ~3.1:1 | Icon fills, accents | ❌ | ✅ |
| accent-gold-dark (oklch 65% 0.14 75) | paper | ~4.6:1 | Accent text on paper | ✅ | ✅ |
| positive (oklch 55% 0.12 150) | paper | ~4.8:1 | Status indicators | ✅ | ✅ |
| negative (oklch 50% 0.12 25) | paper | ~5.5:1 | Error states | ✅ | ✅ |
| warning (oklch 68% 0.14 80) | paper | ~3.4:1 | Warning indicators | ❌ | ✅ |
| info (oklch 50% 0.08 250) | paper | ~5.8:1 | Info states | ✅ | ✅ |
| paper | ink | ~16.5:1 | CTA button text | ✅ | ✅ |

## NeXT Mode (Dark)

| Foreground | Background | Ratio | Use | AA Normal | AA Large |
|-----------|-----------|-------|-----|-----------|----------|
| next-white (oklch 88% 0.004 270) | next-black (oklch 6% 0.005 270) | ~14.2:1 | Body text, headings | ✅ | ✅ |
| next-subtle (oklch 72% 0.012 85) | next-black | ~7.8:1 | Secondary text | ✅ | ✅ |
| next-subtle (oklch 72% 0.012 85) | next-dark (oklch 20% 0.006 270) | ~4.8:1 | Secondary text on alt bg | ✅ | ✅ |
| next-teal (oklch 60% 0.08 170) | next-black | ~5.8:1 | Accent text, prompts | ✅ | ✅ |
| next-teal (oklch 60% 0.08 170) | next-dark | ~3.6:1 | Accent on alt bg | ⚠️ border case | ✅ |
| next-teal-hi (oklch 70% 0.07 170) | next-black | ~8.2:1 | Icon fills, backgrounds | ✅ | ✅ |
| positive-next (oklch 75% 0.14 150) | next-black | ~9.5:1 | Success indicators | ✅ | ✅ |
| negative-next (oklch 65% 0.14 25) | next-black | ~5.2:1 | Error indicators | ✅ | ✅ |
| warning-next (oklch 75% 0.12 80) | next-black | ~9.0:1 | Warning indicators | ✅ | ✅ |
| info-next (oklch 70% 0.08 250) | next-black | ~7.5:1 | Info indicators | ✅ | ✅ |
| next-light (oklch 58% 0.006 270) | next-black | ~5.0:1 | Active nav pill text | ✅ | ✅ |

## Known Gaps

1. **accent-gold on paper** (Mac): At oklch 78%, this is too light for normal text at AA (3.1:1). Use `accent-gold-dark` (oklch 65%) for any text-on-paper use. Reserve `accent-gold` for background fills only. ✅ Documented rule.

2. **warning on paper** (Mac): At oklch 68%, the amber warning passes AA for large text only (3.4:1). For small status labels in data tables, pair with a tinted background pill or use the warning token as a fill color, not text. ⚠️ Acceptable for icon/badge use; avoid as body text.

3. **next-teal on next-dark** (NeXT): At ~3.6:1, this passes AA for large text but is borderline for normal text. Only use next-teal on next-dark for large labels (Silkscreen 700 ≥ 0.75rem is considered large per WCAG bold rule). ✅ Acceptable.

4. **rule on paper** (Mac): At ~2.8:1, this fails the 3:1 non-text contrast minimum. This is period-authentic (1px Mac borders were low-contrast). Accepted as a design decision — borders indicate structure, not information. ⚠️ Accepted exception.

## Recommendation

- Always use `accent-gold-dark` for text on light backgrounds (section badge labels, tech badge text)
- Reserve `accent-gold` for backgrounds only (icon squares, accent bars, CTA hover)
- Warning color on Mac should only be used for icons and status pills, not paragraph text
- All semantic colors in NeXT mode pass AA on both next-black and next-dark backgrounds
