# OTM UX Guidelines

The single source of truth for the look and feel of everything OTM (Old Town Media) builds. This repository holds a **collection** of guideline sets, one per surface we build for. Each set shares the same OTM brand foundation (palette, accents, type, accessibility bar) but adapts it to the constraints of its surface.

## Guideline sets

| Set | Folder | Use it when you are building… |
|-----|--------|-------------------------------|
| **Platform / Internal Tools** | [`platform/`](platform/) | An OTM internal tool, dashboard, or application (full app shell: navy sidebar, OAuth, Railway deploy). |
| **WordPress Plugins** | [`wordpress-plugins/`](wordpress-plugins/) | A WordPress plugin for management, maintenance, or small features (e.g. job boards). Lighter weight, lives inside wp-admin, OTM accents only. |

Start in the folder that matches what you are building. Each set has its own `README.md`, written guideline, design tokens / CSS, and a living HTML showcase.

## What stays constant across every set

These are the OTM brand constants. Individual sets reuse the exact same values; they never redefine them.

- **Accent palette:** Navy `#1a365d`, Blue `#1e4d8c`, Gold `#d4a029`, Teal `#1a8a7d`.
- **Button rule:** Primary actions are blue; the single highest-emphasis CTA may be gold. There is no teal button (teal is for success/growth/headings only).
- **Type:** Clean sans (Inter on our own surfaces; the host's native UI font where we are a guest, e.g. wp-admin). No serif or decorative display fonts. Never use em dashes in UI copy.
- **Accessibility:** 4.5:1 contrast for body text, visible keyboard focus rings, real semantic elements, `prefers-reduced-motion` respected.
- **Don't override your host.** Pull names, identity, and chrome from the host environment instead of hardcoding or overriding them. (Platform: product name + user come from the app/OAuth, see `platform/` §5.5/§8.5. WordPress: never restyle wp-admin globally — scope everything to your plugin, see `wordpress-plugins/`.)

The canonical hex values, type scale, spacing, and radius live in [`platform/otm-tokens.css`](platform/otm-tokens.css). Other sets cite those values as the source of truth for accents.

## What changes between sets

Each surface has different constraints, so each set adapts:

- **Platform** owns the whole screen → full OTM shell (navy sidebar, dark surfaces, heavier components).
- **WordPress plugins** are a guest inside someone else's admin → light, near-native, OTM accents only, no shell.

## Adding a new guideline set

1. Create a new folder (e.g. `marketing-sites/`).
2. Add: a `README.md`, the written guideline (`OTM-*-GUIDELINES.md`), the CSS/tokens for that surface, and an HTML showcase.
3. Reuse the constants above — same accents, same button rule, same accessibility bar — and document only what the surface changes.
4. Add a row to the table at the top of this file.

---

Internal OTM repository. Open the folder for the surface you are building.
