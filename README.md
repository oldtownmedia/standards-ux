# OTM Build Standards

The single source of truth for how OTM (Old Town Media) builds — both how things **look** (UX) and how they're **structured, governed, and shipped** (technical/quality). This repository holds a **collection** of standards sets, one per surface we build for. Each set shares the same OTM foundation but adapts it to the constraints of its surface.

## Standards sets

| Set | Folder | Axis | Use it when you are building… |
|-----|--------|------|-------------------------------|
| **Platform / Internal Tools** | [`platform/`](platform/) | UX | An OTM internal tool, dashboard, or application (full app shell: navy sidebar, OAuth, Railway deploy). |
| **WordPress Plugins** | [`wordpress-plugins/`](wordpress-plugins/) | UX | A WordPress plugin for management, maintenance, or small features (e.g. job boards). Lighter weight, lives inside wp-admin, OTM accents only. |
| **Claude Skills** | [`claude-skills/`](claude-skills/) | Structure / quality | A Claude skill — a reusable instruction packet that runs one of our repeatable workflows the same way every time. Governs anatomy, the trigger contract, naming, versioning, and distribution. |

Start in the folder that matches what you are building. Each set has its own `README.md` and written standard; the UX sets also ship design tokens / CSS and a living HTML showcase.

## What stays constant across every set

OTM has two kinds of constants. The **brand** constants apply to anything with a visual surface (the two UX sets). The **authoring** constants apply to *everything*, including non-visual work like skills.

### Brand constants (UX sets)

- **Accent palette:** Navy `#1a365d`, Blue `#1e4d8c`, Gold `#d4a029`, Teal `#1a8a7d`.
- **Button rule:** Primary actions are blue; the single highest-emphasis CTA may be gold. There is no teal button (teal is for success/growth/headings only).
- **Type:** Clean sans (Inter on our own surfaces; the host's native UI font where we are a guest, e.g. wp-admin). No serif or decorative display fonts.
- **Accessibility:** 4.5:1 contrast for body text, visible keyboard focus rings, real semantic elements, `prefers-reduced-motion` respected.

The canonical hex values, type scale, spacing, and radius live in [`platform/otm-tokens.css`](platform/otm-tokens.css). Other UX sets cite those values as the source of truth.

### Authoring constants (every set)

- **OTM voice and formatting.** Clear sections, tables, and code blocks; plain language; **never use em dashes in copy.** Match the structure of the existing standards.
- **Don't override your host. Pull from the source.** Read names, identity, context, and chrome from the source of truth instead of hardcoding, inventing, or overriding them:
  - *Platform:* the product name and the user come from the app/OAuth, not local input (`platform/` §5.5 / §8.5).
  - *WordPress:* never restyle wp-admin globally — scope everything to your plugin (`wordpress-plugins/`).
  - *Skills:* ask for missing inputs and read context from connected tools; never fabricate client data (`claude-skills/` §3–§4).
- **Ship deliberately.** Each set has a release discipline — a deploy for tools, an enqueue/scope check for plugins, a version bump + `claude-skill` topic for skills.

## What changes between sets

Each surface has different constraints, so each set adapts:

- **Platform** owns the whole screen → full OTM shell (navy sidebar, dark surfaces, heavier components).
- **WordPress plugins** are a guest inside someone else's admin → light, near-native, OTM accents only, no shell.
- **Claude skills** are non-visual → no palette or CSS at all; the standard is about structure, the trigger contract, naming, and distribution via SkillSync.

## Adding a new standards set

1. Create a new folder (e.g. `marketing-sites/`).
2. Add: a `README.md`, the written standard (`OTM-*-GUIDELINES.md`), and — for a UX set — the CSS/tokens and an HTML showcase.
3. Reuse the constants above: the **authoring** constants always; the **brand** constants if the set has a visual surface. Document only what the surface changes.
4. Add a row to the table at the top of this file, noting its axis (UX or structure/quality).

---

Internal OTM repository. Open the folder for the surface you are building.
