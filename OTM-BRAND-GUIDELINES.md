# OTM Internal Tools Brand Guidelines

> **Version:** 1.1
> **Last Updated:** May 2026
> **Purpose:** Standardize the look and feel of all OTM internal tools, dashboards, and applications built in Cursor and deployed to Railway.
> **Audience:** Developers, AI coding assistants (Cursor, Claude), and anyone building internal OTM tooling.
> **Files:** `otm-tokens.css` (variables + type scale), `otm-components.css` (the canonical app shell + components), `otm-brand-showcase.html` (live reference).

---

## 1. Brand Foundation

### 1.1 Brand Personality

OTM's internal tools should feel **strategic, confident, and clean**. We are a growth consultancy, not a startup toy shop. Our tools should feel like they belong to a firm that advises CEOs on scaling their businesses.

**Design Principles:**

- **Professional, not flashy.** Clean layouts, generous whitespace, restrained use of color.
- **Data-forward.** Information density over decoration. Every pixel should earn its place.
- **Consistent.** Every internal tool should feel like it belongs to the same family.
- **Accessible.** High contrast ratios, readable font sizes, clear hierarchy.

### 1.2 Voice and Tone in UI

- Labels and headings: concise, title case
- Descriptions and helper text: sentence case, conversational but professional
- Error messages: direct and helpful, never blame the user
- Empty states: encouraging, with a clear next action
- Never use em dashes in UI copy. Use commas, semicolons, or separate sentences.

---

## 2. Color System

### 2.1 Primary Palette

These are the core brand colors derived from meetotm.com.

| Role | Name | Hex | RGB | Usage |
|------|------|-----|-----|-------|
| **Primary Dark** | Navy | `#1a365d` | `26, 54, 93` | Headers, nav backgrounds, primary surfaces, dark mode base |
| **Primary** | OTM Blue | `#1e4d8c` | `30, 77, 140` | Hero overlays, primary buttons, active states |
| **Primary Light** | Slate Blue | `#2d6ab1` | `45, 106, 177` | Links, hover states, secondary actions |
| **Accent Gold** | OTM Gold | `#d4a029` | `212, 160, 41` | CTAs, highlights, badges, accent text, warnings |
| **Accent Teal** | Growth Teal | `#1a8a7d` | `26, 138, 125` | Success states, secondary accent, section headings, charts |

### 2.2 Neutral Palette

| Role | Name | Hex | Usage |
|------|------|-----|-------|
| **White** | White | `#ffffff` | Page backgrounds, card surfaces |
| **Gray 50** | Snow | `#f8fafc` | Subtle backgrounds, alternating rows |
| **Gray 100** | Mist | `#f1f5f9` | Input backgrounds, sidebar backgrounds |
| **Gray 200** | Border Light | `#e2e8f0` | Borders, dividers, card outlines |
| **Gray 300** | Border | `#cbd5e1` | Stronger borders, disabled states |
| **Gray 500** | Muted Text | `#64748b` | Secondary text, placeholders, labels |
| **Gray 700** | Body Text | `#334155` | Primary body copy |
| **Gray 900** | Heading Text | `#0f172a` | Headings on light backgrounds |

### 2.3 Semantic / Functional Colors

| Role | Hex | CSS Variable | Usage |
|------|-----|-------------|-------|
| **Success** | `#16a34a` | `--color-success` | Confirmations, positive metrics, connected status |
| **Success Background** | `#f0fdf4` | `--color-success-bg` | Success alert backgrounds |
| **Warning** | `#d4a029` | `--color-warning` | (Reuses OTM Gold) Warnings, pending states |
| **Warning Text** | `#a16207` | `--color-warning-text` | Warning badge text, alert text on warning backgrounds |
| **Warning Background** | `#fefce8` | `--color-warning-bg` | Warning alert backgrounds |
| **Error** | `#dc2626` | `--color-error` | Errors, destructive actions, negative metrics |
| **Error Hover** | `#b91c1c` | `--color-error-hover` | Destructive button hover state |
| **Error Background** | `#fef2f2` | `--color-error-bg` | Error alert backgrounds |
| **Info** | `#2d6ab1` | `--color-info` | (Reuses Primary Light) Informational messages |
| **Info Background** | `#eff6ff` | `--color-info-bg` | Info alert backgrounds |

### 2.4 Dark Surface Palette (for nav, sidebars, hero sections)

| Role | Hex | Usage |
|------|-----|-------|
| **Surface Dark** | `#0f2442` | Deepest background (sidebar collapsed) |
| **Surface Navy** | `#1a365d` | Primary dark surface |
| **Surface Mid** | `#1e4d8c` | Hover on dark surfaces |
| **Text on Dark** | `#ffffff` | Primary text on dark surfaces |
| **Text Muted on Dark** | `#94a3b8` | Secondary text on dark surfaces |
| **Border on Dark** | `#2d4a7c` | Borders/dividers on dark surfaces |

---

## 3. Typography

### 3.1 Font Stack

```css
/* Primary font: Inter (load from Google Fonts or bundle) */
--font-sans: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;

/* Monospace: for code blocks, data tables, IDs */
--font-mono: 'JetBrains Mono', 'Fira Code', 'SF Mono', 'Cascadia Code', Consolas, monospace;
```

**Why Inter?** It is clean, highly legible at small sizes, free, and available on Google Fonts. It pairs well with OTM's professional positioning and works beautifully in data-dense UIs.

**Fallback:** If Inter is unavailable or you want zero external dependencies, the system font stack (`-apple-system, BlinkMacSystemFont, ...`) is the fallback. Never use decorative or serif fonts in internal tools.

### 3.2 Type Scale

| Level | Size | Weight | Line Height | Letter Spacing | Usage |
|-------|------|--------|-------------|----------------|-------|
| **Display** | 30px / 1.875rem | 700 | 1.2 | -0.025em | Page titles, hero text |
| **H1** | 24px / 1.5rem | 700 | 1.3 | -0.02em | Section titles |
| **H2** | 20px / 1.25rem | 600 | 1.35 | -0.015em | Card titles, panel headers |
| **H3** | 16px / 1rem | 600 | 1.4 | -0.01em | Subsection labels |
| **Body** | 14px / 0.875rem | 400 | 1.6 | 0 | Default body text |
| **Body Small** | 13px / 0.8125rem | 400 | 1.5 | 0 | Secondary info, helper text |
| **Caption** | 12px / 0.75rem | 500 | 1.4 | 0.01em | Labels, badges, timestamps |
| **Overline** | 11px / 0.6875rem | 600 | 1.3 | 0.06em | Uppercase section labels, stat labels |
| **Mono** | 13px / 0.8125rem | 400 | 1.5 | 0 | Code, IDs, technical values |

This scale is available as CSS variables (`--text-display-size`, `--text-h1-weight`, etc.) and ready-made utility classes (`.text-display`, `.text-h1`, `.text-h2`, `.text-h3`, `.text-overline`) in `otm-tokens.css`. Use those instead of hardcoding sizes so tools stay consistent.

### 3.3 Rules

- **Minimum readable size:** 12px. Never go smaller.
- **Body copy max width:** 680px (for readability in content-heavy sections).
- **Headings on light backgrounds:** Use `#0f172a` (Gray 900) or `#1a365d` (Navy).
- **Headings on dark backgrounds:** Use `#ffffff`.
- **Accent headings:** Use `#1a8a7d` (Growth Teal) for section subheadings when you want visual variety on white backgrounds, matching the meetotm.com "Your Path to Growth Starts Here" style.

---

## 4. Spacing and Layout

### 4.1 Spacing Scale (base 4px)

| Token | Value | Usage |
|-------|-------|-------|
| `--space-1` | 4px | Tight gaps (icon to label) |
| `--space-2` | 8px | Inline element spacing |
| `--space-3` | 12px | Input padding, small card padding |
| `--space-4` | 16px | Default card padding, stack gap |
| `--space-5` | 20px | Section padding (compact) |
| `--space-6` | 24px | Standard card padding |
| `--space-8` | 32px | Section gaps |
| `--space-10` | 40px | Large section gaps |
| `--space-12` | 48px | Page-level vertical rhythm |
| `--space-16` | 64px | Major section separators |

### 4.2 Border Radius

| Token | Value | Usage |
|-------|-------|-------|
| `--radius-sm` | 4px | Badges, tags, small chips |
| `--radius-md` | 6px | Inputs, buttons, small cards |
| `--radius-lg` | 8px | Cards, panels, modals |
| `--radius-xl` | 12px | Large cards, hero sections |
| `--radius-full` | 9999px | Pill buttons, avatars |

### 4.3 Shadow Scale

```css
--shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.05);
--shadow-md: 0 1px 3px rgba(0, 0, 0, 0.08), 0 1px 2px rgba(0, 0, 0, 0.04);
--shadow-lg: 0 4px 12px rgba(0, 0, 0, 0.1), 0 1px 3px rgba(0, 0, 0, 0.06);
--shadow-xl: 0 8px 24px rgba(0, 0, 0, 0.12), 0 2px 8px rgba(0, 0, 0, 0.06);
```

### 4.4 Layout Patterns

- **Max content width:** 1280px for full dashboards, 960px for form-heavy pages.
- **Sidebar width:** 240px expanded, 64px collapsed.
- **Page padding:** 24px on desktop, 16px on mobile.
- **Card grid gap:** 16px to 24px.

---

## 5. Component Patterns

### 5.1 Buttons

| Variant | Background | Text | Border | Usage |
|---------|-----------|------|--------|-------|
| **Primary** | `#1e4d8c` | `#ffffff` | none | Main actions (Save, Submit, Create) |
| **Primary Hover** | `#1a365d` | `#ffffff` | none | |
| **Secondary** | `#ffffff` | `#1e4d8c` | 1px `#e2e8f0` | Secondary actions (Cancel, Back) |
| **Secondary Hover** | `#f1f5f9` | `#1e4d8c` | 1px `#cbd5e1` | |
| **Accent / CTA** | `#d4a029` | `#ffffff` | none | High-emphasis CTAs, matching meetotm.com gold button |
| **Accent Hover** | `#b8891f` | `#ffffff` | none | |
| **Destructive** | `#dc2626` | `#ffffff` | none | Delete, remove, disconnect |
| **Destructive Hover** | `#b91c1c` | `#ffffff` | none | |
| **Ghost** | transparent | `#64748b` | none | Tertiary actions, icon buttons |
| **Ghost Hover** | `#f1f5f9` | `#334155` | none | |

> **There is no teal button.** Teal (`#1a8a7d`) is reserved for success states, growth metrics, and section headings, never as a button fill. Primary actions are **OTM Blue**; the single highest-emphasis CTA on a screen may be **Gold**. If you see a teal action button in a live tool (e.g. a "New Client" button), that is a deviation to correct, not a pattern to copy.

**Button Specs:**
- Height: 36px (small), 40px (default), 48px (large)
- Padding: 0 16px (small), 0 20px (default), 0 24px (large) — vertical centering via height + line-height
- Font size: 13px (small), 14px (default), 15px (large)
- Font weight: 500
- Border radius: `--radius-md` (6px)
- Transition: `all 150ms ease`

### 5.2 Cards

```
Background:    #ffffff
Border:        1px solid #e2e8f0
Border radius: 8px (--radius-lg)
Padding:       24px (--space-6)
Shadow:        --shadow-md
```

**Card with accent border (for status/category):**
```
Border-left: 4px solid [accent color]
    Teal (#1a8a7d)  - default / active / growth
    Gold (#d4a029)   - warning / pending / attention
    Blue (#1e4d8c)   - informational
    Red (#dc2626)    - error / critical
```

**Card title:**
```
Font size:     16px (H3 level)
Font weight:   600
Color:         #0f172a (Gray 900)
Margin bottom: 8px (--space-2)
```

**Card footer (for action buttons):**
```
Margin top:    16px (--space-4)
Padding top:   16px (--space-4)
Border top:    1px solid #e2e8f0
Display:       flex
Align items:   center
Gap:           12px (--space-3)
```

### 5.3 Inputs and Form Elements

**Text Input:**
```
Background:    #f1f5f9 (Gray 100)
Border:        1px solid #e2e8f0
Border radius: 6px (--radius-md)
Padding:       10px 12px
Font family:   var(--font-sans)
Font size:     14px
Color:         #334155 (Gray 700)
Height:        40px
Transition:    all 150ms ease
Outline:       none

Placeholder:   #64748b (Gray 500)

Focus:
  Border:      1px solid #1e4d8c
  Box shadow:  0 0 0 3px rgba(30, 77, 140, 0.15)
  Background:  #ffffff

Error:
  Border:      1px solid #dc2626
  Box shadow:  0 0 0 3px rgba(220, 38, 38, 0.1)
```

**Textarea:**
```
Same as text input, except:
  Height:      auto (min-height 100px)
  Resize:      vertical
```

**Select:**
```
Same as text input, plus:
  Appearance:  none (custom chevron via SVG background-image)
  Chevron:     12px, #64748b stroke, positioned right 12px center
  Padding-right: 36px (to clear chevron)
```

**Form Label:**
```
Font size:     13px
Font weight:   500
Color:         #334155 (Gray 700)
Margin bottom: 4px (--space-1)
Display:       block
```

**Form Hint (helper text below input):**
```
Font size:     12px
Color:         #64748b (Gray 500)
Margin top:    4px (--space-1)
```

**Form Error Message:**
```
Font size:     12px
Color:         #dc2626 (Error)
Margin top:    4px (--space-1)
```

**Form Group (field + label container):**
```
Margin bottom: 20px (--space-5)
```

**Form Row (side-by-side fields):**
```
Display:       grid
Columns:       1fr 1fr
Gap:           16px (--space-4)
```

### 5.4 Tables

**Table wrapper (container):**
```
Background:    #ffffff
Border:        1px solid #e2e8f0
Border radius: 8px (--radius-lg)
Overflow:      hidden
Shadow:        --shadow-sm
```

**Table specs:**
- Header row: `#f1f5f9` background, `#334155` text, 12px uppercase weight-600 labels, letter-spacing 0.04em
- Body rows: white background, `#334155` text, 14px
- Alternating rows (optional): `#f8fafc` on even rows
- Row hover: `#f1f5f9`
- Borders: 1px `#e2e8f0` horizontal only (no vertical gridlines for clean look)
- Cell padding: 12px 16px
- Last row: no bottom border (cleaner look inside rounded wrapper)

### 5.5 Navigation (Sidebar)

The left sidebar is the **primary navigation** for OTM tools (see §8.4). It is a full-height navy column with four stacked regions, top to bottom: **logo + product subtitle**, **scrollable nav**, and a **pinned user/account block**. All of this ships in `otm-components.css` (`.sidebar`, `.nav-item`, `.nav-group`, `.sidebar-user`); the spec below documents the intent.

**Shell:**
```
Background:    #1a365d (Navy)
Width:         240px (expanded) / 64px (collapsed)
Text:          #ffffff (active), #94a3b8 (inactive)
Icon size:     20px
Layout:        flex column, full viewport height, sticky
```

**Logo area (top, 56px):**
```
.OTM logo:     white, with the leading "." in gold (#d4a029)
Subtitle:      product / instance name below the logo, 12px, #94a3b8
               (e.g. ".OTM" over "Venn Intelligence")
Border bottom: 1px #2d4a7c
```

**Section label (non-interactive group heading):**
```
11px, uppercase, #94a3b8, weight 600, letter-spacing 0.06em
```

**Nav item:**
```
Padding:       8px 12px, gap 12px (icon to label), radius 6px
Inactive:      text #94a3b8
Hover:         background #1e4d8c, text #ffffff
Active:        background #1e4d8c, text #ffffff, left border 3px #d4a029
Markup:        use aria-current="page" on the active item
```

**Collapsible nav group (a parent that expands to nested items, e.g. "Settings"):**
```
Toggle row:    same styling as a nav item, plus a trailing chevron
               (16px) on the right that rotates 180deg when open
State:         button with aria-expanded="true|false" + aria-controls
Sub-items:     indented (padding-left 32px), 13px, #94a3b8
               hover background #1e4d8c; active sub-item is white + weight 500
Collapsed:     sub-nav hidden when the toggle is aria-expanded="false"
```

**User / account block (pinned to the sidebar bottom):**

This block is part of the standard shell and is the single most commonly missed element when tools are rebuilt. Always include it on authenticated tools. **Its contents come from the OAuth provider, not from local input** (see §8.5): the avatar is the Google profile photo, and the name and email are the signed-in identity.
```
Border top:    1px #2d4a7c
Avatar:        32px, border-radius full (Google/OAuth photo or initials fallback)
Name:          13px, weight 600, #ffffff, truncate with ellipsis
Email:         12px, #94a3b8, truncate with ellipsis
Sign out:      full-width row below the identity, 13px #94a3b8 with a 16px
               logout icon; hover background #1e4d8c, text #ffffff
A11y:          render "Sign out" as a <button> (or a real link to the logout
               route), never a bare div; it must be keyboard-focusable
```

### 5.6 Badges / Status Indicators

| Status | Background | Text | Dot Color |
|--------|-----------|------|-----------|
| Active / Success | `#f0fdf4` | `#16a34a` | `#16a34a` |
| Warning / Pending | `#fefce8` | `#a16207` | `#d4a029` |
| Error / Failed | `#fef2f2` | `#dc2626` | `#dc2626` |
| Info / Default | `#eff6ff` | `#1e4d8c` | `#2d6ab1` |
| Neutral / Inactive | `#f1f5f9` | `#64748b` | `#94a3b8` |

**Badge specs:** 12px font, weight 500, padding 2px 8px, border-radius 9999px, inline-flex with center alignment.

**Badge dot:** 6px width/height, border-radius 50%, 6px gap between dot and text.

**Category badge** (`.badge-category`): labels what product or tool a record belongs to (e.g. "Site Intelligence" on a project card). Distinguished from status badges by **square-ish corners** (`--radius-sm`) instead of the pill shape:
```
Background:    #e6f4f1 (teal tint)
Text:          #1a8a7d (Growth Teal), weight 600
Radius:        4px (--radius-sm)
```

**Integration status chip** (`.chip-integration`): a compact chip for connected data sources (e.g. `GSC`, `GA4`). It encodes connection state via color:
```
Connected:     background #f0fdf4, text #16a34a
Not connected: background #fef2f2, text #dc2626
Specs:         11px, weight 600, padding 2px 8px, radius 4px, letter-spacing 0.02em
```

### 5.7 Charts and Data Visualization

**Chart color sequence (use in order for multi-series):**

1. `#1e4d8c` (OTM Blue)
2. `#1a8a7d` (Growth Teal)
3. `#d4a029` (OTM Gold)
4. `#2d6ab1` (Slate Blue)
5. `#16a34a` (Success Green)
6. `#dc2626` (Error Red)
7. `#64748b` (Gray 500)
8. `#0f2442` (Surface Dark)

**Chart guidelines:**
- Background: white
- Grid lines: `#e2e8f0`, 1px, dashed
- Axis labels: 12px, `#64748b`
- Data labels: 13px, `#334155`
- Tooltips: `#0f172a` background, white text, 8px radius, `--shadow-lg`

### 5.8 Alerts

Alerts use semantic background colors with a colored left border, an icon, and title/body text. They follow the same color system as badges but in a larger, block-level format.

```
Padding:       16px (--space-4)
Border radius: 8px (--radius-lg)
Border left:   4px solid [semantic color]
Display:       flex
Gap:           12px (--space-3)
Align items:   flex-start
```

**Alert icon:** 20px width/height, flex-shrink 0, 1px top margin for optical alignment with title text.

**Alert title:** 14px, weight 600, 2px bottom margin.

**Alert body:** 13px, line-height 1.5.

| Variant | Background | Border Color | Text Color |
|---------|-----------|-------------|------------|
| **Info** | `#eff6ff` | `#2d6ab1` | `#1e4d8c` |
| **Success** | `#f0fdf4` | `#16a34a` | `#16a34a` |
| **Warning** | `#fefce8` | `#d4a029` | `#a16207` |
| **Error** | `#fef2f2` | `#dc2626` | `#dc2626` |

### 5.9 Metric Cards

Metric cards display KPI values on dashboards. They combine Overline styling for labels and Display styling for values.

```
Background:    #ffffff
Border:        1px solid #e2e8f0
Border radius: 8px (--radius-lg)
Padding:       20px (--space-5)
Shadow:        --shadow-sm
```

**Metric label (uses Overline style):**
```
Font size:        11px
Font weight:      600
Text transform:   uppercase
Letter spacing:   0.06em
Color:            #64748b (Gray 500)
Margin bottom:    4px (--space-1)
```

**Metric value (uses Display style):**
```
Font size:        30px
Font weight:      700
Line height:      1.2
Letter spacing:   -0.025em
Color:            #0f172a (Gray 900)
```

**Metric change indicator:**
```
Font size:     13px
Font weight:   500
Margin top:    4px (--space-1)
Positive:      #16a34a (Success)
Negative:      #dc2626 (Error)
```

**Attention metric value** (`.metric-value.is-attention`): when a metric represents something the user must act on (e.g. "Needs Attention: 21" — missing connections or stale data), render the value itself in warning gold rather than the default heading color:
```
Color:         #a16207 (Warning Text)
```
Use sparingly: at most one attention metric per metric row, reserved for genuinely actionable counts.

**Metric grid layout:** Use CSS grid with `repeat(auto-fill, minmax(180px, 1fr))` and 16px gap.

---

## 6. CSS Variables Reference

Copy this into your project's root CSS file or Tailwind config.

```css
:root {
  /* ===== OTM BRAND COLORS ===== */

  /* Primary */
  --color-navy: #1a365d;
  --color-blue: #1e4d8c;
  --color-blue-light: #2d6ab1;
  --color-gold: #d4a029;
  --color-gold-hover: #b8891f;
  --color-teal: #1a8a7d;

  /* Neutrals */
  --color-white: #ffffff;
  --color-gray-50: #f8fafc;
  --color-gray-100: #f1f5f9;
  --color-gray-200: #e2e8f0;
  --color-gray-300: #cbd5e1;
  --color-gray-500: #64748b;
  --color-gray-700: #334155;
  --color-gray-900: #0f172a;

  /* Semantic */
  --color-success: #16a34a;
  --color-success-bg: #f0fdf4;
  --color-warning: #d4a029;
  --color-warning-text: #a16207;
  --color-warning-bg: #fefce8;
  --color-error: #dc2626;
  --color-error-hover: #b91c1c;
  --color-error-bg: #fef2f2;
  --color-info: #2d6ab1;
  --color-info-bg: #eff6ff;

  /* Dark surfaces */
  --color-surface-dark: #0f2442;
  --color-surface-navy: #1a365d;
  --color-surface-mid: #1e4d8c;
  --color-border-dark: #2d4a7c;
  --color-text-dark-muted: #94a3b8;

  /* ===== TYPOGRAPHY ===== */
  --font-sans: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  --font-mono: 'JetBrains Mono', 'Fira Code', 'SF Mono', Consolas, monospace;

  /* ===== SPACING ===== */
  --space-1: 4px;
  --space-2: 8px;
  --space-3: 12px;
  --space-4: 16px;
  --space-5: 20px;
  --space-6: 24px;
  --space-8: 32px;
  --space-10: 40px;
  --space-12: 48px;
  --space-16: 64px;

  /* ===== BORDER RADIUS ===== */
  --radius-sm: 4px;
  --radius-md: 6px;
  --radius-lg: 8px;
  --radius-xl: 12px;
  --radius-full: 9999px;

  /* ===== SHADOWS ===== */
  --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.05);
  --shadow-md: 0 1px 3px rgba(0, 0, 0, 0.08), 0 1px 2px rgba(0, 0, 0, 0.04);
  --shadow-lg: 0 4px 12px rgba(0, 0, 0, 0.1), 0 1px 3px rgba(0, 0, 0, 0.06);
  --shadow-xl: 0 8px 24px rgba(0, 0, 0, 0.12), 0 2px 8px rgba(0, 0, 0, 0.06);

  /* ===== TRANSITIONS ===== */
  --transition-fast: 100ms ease;
  --transition-base: 150ms ease;
  --transition-slow: 300ms ease;

  /* ===== LAYOUT ===== */
  --max-width-content: 1280px;
  --max-width-form: 960px;
  --max-width-prose: 680px;
  --sidebar-width: 240px;
  --sidebar-collapsed: 64px;
  --nav-height: 56px;
}
```

---

## 7. Tailwind CSS Configuration

If using Tailwind in your project, extend the default config:

```javascript
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      colors: {
        otm: {
          navy: '#1a365d',
          blue: '#1e4d8c',
          'blue-light': '#2d6ab1',
          gold: '#d4a029',
          'gold-hover': '#b8891f',
          teal: '#1a8a7d',
        },
        surface: {
          dark: '#0f2442',
          navy: '#1a365d',
          mid: '#1e4d8c',
          border: '#2d4a7c',
        },
        gray: {
          50: '#f8fafc',
          100: '#f1f5f9',
          200: '#e2e8f0',
          300: '#cbd5e1',
          500: '#64748b',
          700: '#334155',
          900: '#0f172a',
        },
        success: '#16a34a',
        warning: '#d4a029',
        'warning-text': '#a16207',
        error: '#dc2626',
        info: '#2d6ab1',
      },
      fontFamily: {
        sans: ['Inter', '-apple-system', 'BlinkMacSystemFont', 'Segoe UI', 'Roboto', 'Helvetica Neue', 'Arial', 'sans-serif'],
        mono: ['JetBrains Mono', 'Fira Code', 'SF Mono', 'Consolas', 'monospace'],
      },
      fontSize: {
        display: ['30px', { lineHeight: '1.2', letterSpacing: '-0.025em', fontWeight: '700' }],
        h1: ['24px', { lineHeight: '1.3', letterSpacing: '-0.02em', fontWeight: '700' }],
        h2: ['20px', { lineHeight: '1.35', letterSpacing: '-0.015em', fontWeight: '600' }],
        h3: ['16px', { lineHeight: '1.4', letterSpacing: '-0.01em', fontWeight: '600' }],
        body: ['14px', { lineHeight: '1.6' }],
        'body-sm': ['13px', { lineHeight: '1.5' }],
        caption: ['12px', { lineHeight: '1.4', letterSpacing: '0.01em' }],
        overline: ['11px', { lineHeight: '1.3', letterSpacing: '0.06em', fontWeight: '600' }],
      },
      borderRadius: {
        sm: '4px',
        md: '6px',
        lg: '8px',
        xl: '12px',
      },
      boxShadow: {
        sm: '0 1px 2px rgba(0, 0, 0, 0.05)',
        md: '0 1px 3px rgba(0, 0, 0, 0.08), 0 1px 2px rgba(0, 0, 0, 0.04)',
        lg: '0 4px 12px rgba(0, 0, 0, 0.1), 0 1px 3px rgba(0, 0, 0, 0.06)',
        xl: '0 8px 24px rgba(0, 0, 0, 0.12), 0 2px 8px rgba(0, 0, 0, 0.06)',
      },
      maxWidth: {
        content: '1280px',
        form: '960px',
        prose: '680px',
      },
    },
  },
};
```

---

## 8. Railway Deployment Conventions

### 8.1 Project Naming

All OTM internal tools deployed to Railway should follow this naming pattern:

```
otm-[tool-name]
```

Examples: `otm-schema-viewer`, `otm-lead-scorer`, `otm-research-agent`, `otm-call-prep`

### 8.2 Environment Variables

Every Railway project should include:

```
NODE_ENV=production
APP_NAME=otm-[tool-name]
APP_VERSION=1.0.0
PORT=3000
```

Authenticated tools also need the Google OAuth vars (see §8.6):
```
GOOGLE_CLIENT_ID=...
GOOGLE_CLIENT_SECRET=...
OAUTH_REDIRECT_URI=https://otm-[tool-name].up.railway.app/auth/callback
ALLOWED_HD=meetotm.com
```

### 8.3 Health Check Endpoint

Every app should expose `GET /health` returning:

```json
{
  "status": "ok",
  "app": "otm-[tool-name]",
  "version": "1.0.0",
  "timestamp": "2026-02-05T00:00:00Z"
}
```

### 8.4 Standard Page Structure

**The default OTM shell is sidebar-first.** Most internal tools are multi-page dashboards, so the standard layout is a full-height left sidebar plus a content header bar, not a top nav bar. The complete shell ships in `otm-components.css` (`.app-shell`, `.sidebar`, `.content-header`, `.app-footer`).

A standard multi-page tool includes:

1. **Left sidebar** (navy, 240px) containing, top to bottom: the `.OTM` logo + product subtitle, the nav (with section labels and collapsible groups), and the pinned **user/account block with Sign out** (see §5.5). This is the primary navigation.
2. **Content header bar** (56px, white) at the top of the content column showing the current page title / breadcrumb and any page-level actions.
3. **Main content area** (gray-50 background, max-width 1280px).
4. **Footer** (minimal: "OTM Internal Tools · 1.0.0").

**Single-page / utility tools** (no multi-page nav) may instead use a **top nav bar** (56px height, navy background, white `.OTM` logo left-aligned, tool name next to logo) with no sidebar. Use the sidebar shell whenever the tool has more than one view.

**Content header bar (when sidebar is present):**
```
Background:    #ffffff
Border bottom: 1px solid #e2e8f0
Height:        56px (--nav-height)
Display:       flex, vertically centered
Padding:       0 32px (--space-8)
Position:      sticky, top: 0, z-index: 50

Title:         16px, weight 600, #0f172a (Gray 900)
Breadcrumb:    13px, #64748b (Gray 500), left margin 12px
Actions area:  margin-left: auto, flex with 12px gap
```

**Footer:**
```
Text align:    center
Padding:       32px 24px (--space-8 --space-6)
Color:         #64748b (Gray 500)
Font size:     13px
Border top:    1px solid #e2e8f0
Format:        "OTM Internal Tools · {version}"   e.g. "OTM Internal Tools · 1.0.0"
```

### 8.5 Authentication and User Identity

> **Principle: OTM tools authenticate through OAuth, never local user management.**
> Tools do not store passwords, do not run their own sign-up flow, and do not keep
> a local users table for authentication. A user's identity (name, email, avatar)
> always comes from the OAuth provider and is treated as the source of truth.
> The standard provider is **Google Workspace**, and sign-in is **restricted to
> `@meetotm.com` accounts**.

This is a hard rule for every authenticated OTM tool. If you are an AI assistant
generating a tool, implement Google OAuth (e.g. Google Identity Services / an
OAuth library for the stack), hosted-domain restricted to `meetotm.com`, and read
the user's profile from the provider. Never scaffold email/password auth or a
local account system.

**OAuth sign-in gate** (the screen shown when a user is not yet authenticated):
```
Page background:   #1a365d (navy)
Card:              white, 400px max-width, 8px radius (--radius-lg), --shadow-xl
Logo:              .OTM above the card (white) with the gold leading dot
Heading:           "Sign in to {Tool Name}" (H2)
Helper text:       "Use your @meetotm.com Google account." (Body Small, muted)
Primary action:    a single "Continue with Google" provider button:
                     - white background, 1px #e2e8f0 border, #334155 text
                     - Google "G" logo at left, 40px height, full card width
                     - never restyle the Google mark; follow Google's button rules
No password fields. No "Create account" link. No email/password inputs.
Domain note:       reject non-@meetotm.com accounts with a clear error
                   ("Use your @meetotm.com account to sign in.")
```

**Surfacing the user (required on every authenticated screen).**
The signed-in user must always be visible, sourced from the OAuth profile:
- Render the **sidebar user/account block** (see §5.5) with the provider **photo**
  (`picture` claim) as the avatar, the user's **name**, and **email**. Fall back
  to initials only when no photo is available.
- **Sign out** clears the session and returns to the OAuth gate (a provider
  logout / token revoke), not a local logout.
- Anywhere the UI attributes an action to "you" (audit trails, "created by",
  greetings), use the OAuth identity rather than a manually entered name.

**Legacy: shared-password gate (avoid for new tools).**
Only for a simple internal utility that has no per-user identity needs, a single
shared-password gate is acceptable as a stopgap. It provides access control, not
identity, so tools using it have no user block. Migrate to Google OAuth when the
tool needs to know *who* is using it.
```
Page background:   #1a365d
Card:              white, 400px max-width, 8px radius, --shadow-xl
Input:             Standard input style (single password field)
Button:            Gold accent (#d4a029) for "Access"
```

### 8.6 Google OAuth Implementation Checklist

Stack-agnostic steps to wire up the §8.5 standard. The specific library differs by
stack (Passport/NextAuth/Authlib/Google Identity Services, etc.), but every OTM
tool covers these same points.

**1. Google Cloud Console**
- Create (or reuse) a project and configure the **OAuth consent screen** as
  **Internal** (Workspace-only — this alone limits sign-in to your org).
- Create an **OAuth 2.0 Client ID** of type **Web application**.
- Add **Authorized redirect URIs** for every environment:
  - `http://localhost:3000/auth/callback` (local dev)
  - `https://otm-<tool-name>.up.railway.app/auth/callback` (Railway)
  - any custom domain you map.
- Store the client ID/secret as Railway env vars; never commit them:
  ```
  GOOGLE_CLIENT_ID=...
  GOOGLE_CLIENT_SECRET=...
  OAUTH_REDIRECT_URI=https://otm-<tool-name>.up.railway.app/auth/callback
  ALLOWED_HD=meetotm.com
  ```

**2. Authorization request**
- Scopes: `openid email profile` (that's all you need for identity).
- Add the hosted-domain hint so Google pre-filters the account chooser:
  ```
  https://accounts.google.com/o/oauth2/v2/auth
    ?client_id=$GOOGLE_CLIENT_ID
    &redirect_uri=$OAUTH_REDIRECT_URI
    &response_type=code
    &scope=openid%20email%20profile
    &hd=meetotm.com
    &access_type=offline
    &state=<csrf-token>
  ```
- `hd` is a UX hint only; it is **not** a security control (see step 4).

**3. Token exchange + identity**
- Exchange the `code` for tokens server-side, then read the verified ID-token
  claims: `email`, `name`, `picture`, `hd`, `sub` (`sub` is the stable user key).
- Feed `name` / `email` / `picture` straight into the sidebar user block (§5.5).

**4. Enforce the domain server-side (do not trust the client)**
- Verify the ID token's signature, `aud` (your client ID), and `iss`
  (`accounts.google.com`).
- Reject sign-in unless `hd === "meetotm.com"` **and** `email_verified === true`
  **and** the email ends in `@meetotm.com`. Show: "Use your @meetotm.com account
  to sign in."

**5. Session + sign out**
- Establish a session (signed cookie / server session) after verification.
- **Sign out** clears that session and returns to the gate; optionally hit
  Google's revocation endpoint. There is no local password to reset.

**6. CSRF**
- Use the `state` parameter to protect the callback.

---

## 9. Favicon and Logo Usage

### 9.1 Logo

The OTM logo is "**.OTM**" (with leading period) in a clean sans-serif. Usage rules:

- On dark backgrounds: white logo
- On light backgrounds: navy (`#1a365d`) logo
- Never stretch, rotate, or add effects
- Minimum clear space: height of the period on all sides

### 9.2 Favicon

Use a simple navy square with white "O" or the OTM mark. For Railway apps, include:

```html
<link rel="icon" type="image/svg+xml" href="/favicon.svg">
```

Minimal SVG favicon:
```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32">
  <rect width="32" height="32" rx="6" fill="#1a365d"/>
  <text x="16" y="22" font-family="Inter, Arial, sans-serif" font-size="16"
        font-weight="700" fill="#ffffff" text-anchor="middle">O</text>
</svg>
```

---

## 10. Cursor / AI Assistant Instructions

When using this file as context in Cursor or with Claude for code generation, include this prompt prefix:

```
You are building an internal tool for OTM (Old Town Media). Follow the brand
guidelines in OTM-BRAND-GUIDELINES.md. Key rules:

- Import otm-tokens.css and otm-components.css; use those classes/variables
  instead of hardcoding colors, type sizes, or rebuilding the shell
- Use the OTM color palette (navy, blue, gold, teal as defined in the guide)
- Use Inter font family with the defined type scale (--text-* tokens)
- Default shell is the left navy SIDEBAR + content header bar (see §5.5, §8.4),
  not a top nav bar
- The sidebar MUST include: .OTM logo + product subtitle at top, and a pinned
  user/account block at the bottom (avatar, name, email, Sign out button).
  Collapsible nav groups use a <button aria-expanded> toggle with nested items.
- Primary buttons are blue; the single highest-emphasis CTA may be gold.
  There is NO teal button (teal is for success/growth/headings only).
- Authenticate with Google OAuth restricted to @meetotm.com (see §8.5). Never
  scaffold email/password auth or a local users table. Pull the user's name,
  email, and avatar from the OAuth profile and show them in the sidebar user
  block; Sign out performs a provider logout.
- Clean, data-forward design with generous whitespace
- Cards with subtle borders and shadows, optional colored left borders
- Keyboard-focusable controls with visible focus rings; aria-current on the
  active nav item; real <button>/<a> for Sign out (never a bare div)
- Never use em dashes in UI copy
- Deploy-ready for Railway with health check endpoint
```

---

## 11. Quick Copy Reference

### HTML Head Boilerplate

```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<link rel="icon" type="image/svg+xml" href="/favicon.svg">
```

### Minimal Page Shell (HTML)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <!-- boilerplate from above -->
  <title>Tool Name | OTM Internal</title>
  <style>
    /* paste CSS variables from Section 6 */
    body {
      font-family: var(--font-sans);
      font-size: 14px;
      line-height: 1.6;
      color: var(--color-gray-700);
      background: var(--color-gray-50);
      margin: 0;
    }
    .nav {
      background: var(--color-navy);
      height: var(--nav-height);
      display: flex;
      align-items: center;
      padding: 0 var(--space-6);
      color: var(--color-white);
    }
    .nav-logo {
      font-weight: 700;
      font-size: 18px;
      letter-spacing: -0.02em;
    }
    .nav-title {
      margin-left: var(--space-4);
      font-size: 14px;
      color: var(--color-text-dark-muted);
      font-weight: 400;
    }
    .main {
      max-width: var(--max-width-content);
      margin: 0 auto;
      padding: var(--space-8) var(--space-6);
    }
  </style>
</head>
<body>
  <nav class="nav">
    <span class="nav-logo">.OTM</span>
    <span class="nav-title">Tool Name</span>
  </nav>
  <main class="main">
    <!-- content -->
  </main>
</body>
</html>
```

---

## 12. Do's and Don'ts

### Do

- Use the defined color palette consistently
- Lean on navy + white as the primary combination
- Use gold sparingly for emphasis and CTAs
- Use teal for positive/growth-related metrics
- Maintain at least 4.5:1 contrast ratio for text
- Include the `.OTM` mark on every tool's navigation
- Keep layouts clean and information-dense
- Authenticate with Google OAuth and surface the signed-in user (photo, name, email) from the provider

### Don't

- Use colors outside the defined palette for UI elements
- Use gradients (keep surfaces flat)
- Use decorative fonts, serif fonts, or custom display typefaces
- Use rounded-full (pill shape) on cards or large containers
- Use heavy drop shadows or glow effects
- Use em dashes in any UI copy
- Add animations beyond subtle hover transitions (150ms)
- Use more than 3 colors from the chart palette in a single visualization unless absolutely necessary
- Use teal (or any non-blue/gold color) as a button fill
- Ship an authenticated tool without the sidebar user/account + Sign out block
- Build email/password auth, a sign-up flow, or a local users table — use Google
  OAuth (`@meetotm.com`) and read identity from the provider (see §8.5)

### Common deviations to watch for

These are the elements most often missed or done off-brand when tools are rebuilt. Check them on every tool:

1. **Sidebar user/account block + Sign out** is present and styled per §5.5 (avatar, name, email, focusable Sign out).
2. **Collapsible nav groups** use a real `<button aria-expanded>` toggle, with a chevron that rotates and nested sub-items that hide when collapsed.
3. **Logo + product subtitle** at the top of the sidebar (`.OTM` over the instance name, with the leading dot in gold).
4. **Button colors** are blue/gold only. No teal buttons.
5. **Footer string** reads "OTM Internal Tools · {version}".

---

## 13. Accessibility

Accessibility is part of the brand, not an add-on. Minimum bar for every tool:

- **Contrast:** Maintain at least 4.5:1 for body text and 3:1 for large text / UI borders. On the navy sidebar, use `#ffffff` for active text and `#94a3b8` only for secondary labels (it clears 4.5:1 on `#1a365d`).
- **Keyboard:** Every interactive element (nav items, nav-group toggles, Sign out, buttons, links, inputs) must be reachable and operable by keyboard and show a visible focus ring. `otm-tokens.css` provides a default `:focus-visible` outline; do not remove it.
- **Semantics:** Use real elements: `<button>` for actions, `<a href>` for navigation, `<nav>` for the sidebar. Mark the active nav item with `aria-current="page"`. Collapsible groups use `aria-expanded` + `aria-controls`.
- **Images:** Avatars and icons need `alt` text or `aria-label` (e.g. the Sign out icon button).
- **Motion:** Respect `prefers-reduced-motion`; `otm-tokens.css` already neutralizes transitions/animations under that media query.
- **Targets:** Interactive rows/buttons should present at least a ~36px tall hit area.
