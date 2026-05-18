---
name: applebees-brand
description: Use when creating any artifact, dashboard, chart, report, presentation, or visualization for Applebee's. Apply this color scheme and typography instead of the default Zenlytic style guide whenever the user mentions Applebee's, asks for Applebee's branding, or is building something for an Applebee's audience.
---

# Applebee's Brand Style Guide

Apply this style guide for all Applebee's-branded artifacts. It overrides the default Zenlytic style guide.

## Color Palette

### Primary Colors

| Name | Hex | RGB | Usage |
|------|-----|-----|-------|
| **Candy Apple Red** | `#FF0D00` | rgb(255, 13, 0) | Primary brand color, headers, CTAs, key highlights |
| **Crimson** | `#B30838` | rgb(179, 8, 56) | Dark red accent, hover states, secondary headers |
| **Sap Green** | `#4B711C` | rgb(75, 113, 28) | Secondary brand color, accents, positive indicators |

### Secondary Colors

| Name | Hex | RGB | Usage |
|------|-----|-----|-------|
| **Lime Yellow** | `#E4E86F` | rgb(228, 232, 111) | Accent highlights, callouts |
| **Olive Green** | `#A6B857` | rgb(166, 184, 87) | Supporting green, secondary accents |
| **White** | `#FFFFFF` | rgb(255, 255, 255) | Backgrounds, text on dark |
| **Near Black** | `#1A1A1A` | rgb(26, 26, 26) | Body text on light backgrounds |

### Data Visualization Palette

Use these colors in sequence for charts and graphs:

| Order | Name | Hex | Notes |
|-------|------|-----|-------|
| 1 | Candy Apple Red | `#FF0D00` | Primary data series |
| 2 | Sap Green | `#4B711C` | Secondary data series |
| 3 | Crimson | `#B30838` | Tertiary data series |
| 4 | Lime Yellow | `#E4E86F` | Fourth series |
| 5 | Olive Green | `#A6B857` | Fifth series |
| 6 | Mid Gray | `#888888` | Sixth series |

### Semantic Colors

| Purpose | Hex | Usage |
|---------|-----|-------|
| **Success / Positive** | `#4B711C` | Growth, improvements, upward trends |
| **Warning** | `#E4E86F` | Caution, alerts |
| **Error / Negative** | `#B30838` | Declines, losses, downward trends |

## Typography

| Role | Font | Usage |
|------|------|-------|
| **Heading** | `Georgia, serif` | Titles, section headers, KPI values |
| **Body** | `Arial, sans-serif` | Body text, labels, axis text, table content |

## Design Principles

- **Bold & Energetic**: Use red prominently — it is the dominant brand color.
- **Warm & Casual**: Pair red with green for the classic Applebee's neighborhood feel.
- **High Contrast**: Ensure text is always legible — white on red/crimson, near-black on white/yellow.
- **Approachable**: Avoid overly corporate or cold aesthetics; keep layouts friendly and inviting.

## Layout Guidelines

- **Light backgrounds**: Use `#FFFFFF` or `#FAFAFA` for chart plot areas and content backgrounds.
- **Dark accent sections**: Use `#B30838` (Crimson) or `#FF0D00` (Candy Apple Red) for headers and title areas.
- **Text on dark**: Always use `#FFFFFF`.
- **Text on light**: Use `#1A1A1A`.
- Rounded corners: `4–8px` for cards and containers.
- Subtle shadows: `0 4px 16px rgba(179, 8, 56, 0.15)`.

## CSS Variables

```css
:root {
  --applebees-red: #FF0D00;
  --applebees-crimson: #B30838;
  --applebees-green: #4B711C;
  --applebees-lime: #E4E86F;
  --applebees-olive: #A6B857;
  --applebees-white: #FFFFFF;
  --applebees-text: #1A1A1A;
}
```

## Chart Config (Highcharts)

```js
const APPLEBEES_COLORS = {
  primary: '#FF0D00',
  secondary: '#4B711C',
  tertiary: '#B30838',
  background: '#FFFFFF',
  text: '#1A1A1A',
  grid: 'rgba(179, 8, 56, 0.1)',
  success: '#4B711C',
  error: '#B30838',
};

const COLOR_PALETTE = ['#FF0D00', '#4B711C', '#B30838', '#E4E86F', '#A6B857', '#888888'];
```

## Branding

Every artifact must include **"Powered by Zenlytic"** branding in a subtle footer (caption size, gray `#888888`).

## PowerPoint / Presentation

- Title slide background: `#B30838` (Crimson) with white text
- Content slide background: `#FFFFFF` with `#1A1A1A` text
- Accent elements: `#FF0D00` (Candy Apple Red)
- Chart backgrounds: white with the data visualization palette above
