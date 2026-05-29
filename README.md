# OTM Platform UX Guidelines

The single source of truth for the look and feel of OTM (Old Town Media) internal tools, dashboards, and applications. Use this when building any internal tool in Cursor and deploying to Railway.

## What's in here

| File | Purpose |
|------|---------|
| **`OTM-BRAND-GUIDELINES.md`** | The written spec: color, type, spacing, components, the app shell, accessibility, and Railway conventions. Start here. |
| **`otm-tokens.css`** | Design tokens (CSS custom properties): colors, the type scale, spacing, radius, shadows, plus a base reset, type utilities, and accessibility defaults (`:focus-visible`, reduced-motion). |
| **`otm-components.css`** | The canonical, reusable implementation of the app shell and components: sidebar (logo + subtitle, nav, **collapsible groups**, **user/account block + Sign out**), content header, buttons, cards, badges, integration chips, metric cards, footer. |
| **`otm-brand-showcase.html`** | A living visual reference. Open it in any browser to see every token and component rendered. |

## Quick start

Add the two stylesheets to the root of your tool, tokens first:

```html
<link rel="stylesheet" href="otm-tokens.css">
<link rel="stylesheet" href="otm-components.css">
```

Then build with the documented classes (`.app-shell`, `.sidebar`, `.nav-item`, `.nav-group`, `.sidebar-user`, `.btn`, `.card`, `.badge`, etc.) instead of hardcoding colors or rebuilding the shell. See `OTM-BRAND-GUIDELINES.md` §5 (components) and §8.4 (page structure).

## Most-missed elements (check these every time)

When tools get rebuilt, these are what drift or go missing. They are now fully specified in §5.5 and shipped in `otm-components.css`:

1. **Sidebar user/account block + Sign out** at the bottom of the sidebar.
2. **Collapsible nav groups** (`<button aria-expanded>` toggle + nested items).
3. **Logo + product subtitle** at the top of the sidebar (`.OTM` over the instance name).
4. **Buttons are blue/gold only** — there is no teal button.
5. **Auth is Google OAuth (@meetotm.com), never email/password or local accounts** — the signed-in user's name, email, and avatar come from the provider and show in the sidebar block. See §8.5.

## Using with Cursor / Claude

Paste the prompt prefix in `OTM-BRAND-GUIDELINES.md` §10 as context so the assistant follows the palette, type scale, shell structure, and accessibility rules.

---

Internal OTM repository. See `OTM-BRAND-GUIDELINES.md` for the full standard.
