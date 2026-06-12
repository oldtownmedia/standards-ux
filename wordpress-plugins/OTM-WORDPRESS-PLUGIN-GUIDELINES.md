# OTM WordPress Plugin Guidelines

How OTM builds WordPress plugins for client sites: management, maintenance, and small features such as job boards. These plugins are **guests inside someone else's WordPress admin** and, often, someone else's public theme. The brand rule that follows from that: be light, be near-native, and add OTM polish with **accents only** — never a full takeover.

> **Files in this set:** `otm-wp-admin.css` (the scoped accent layer for wp-admin screens), `otm-wp-showcase.html` (a living reference that renders the components against a wp-admin-style page). The OTM accent hex values are the brand constants and match `../platform/otm-tokens.css`.
>
> **Relationship to the platform guidelines:** Same brand (palette, button rule, accessibility bar). Different surface. The platform set owns the whole screen and ships a heavy navy app shell; **none of that applies here.** No OTM sidebar, no dark surfaces, no OAuth/identity block, no Railway shell. WordPress provides the chrome; we provide accents.

---

## 1. Principles

1. **You are a guest.** WordPress (and on the front end, the client's theme) owns the chrome. Fit in first, brand second.
2. **Accents only.** OTM shows up as small touches — a navy heading, a gold CTA, a teal success state, a focus ring, a left-border accent on a card. Never as a wholesale restyle.
3. **Lighter and lower-contrast than the platform.** White and light-gray surfaces, hairline borders, minimal shadow. The heavy navy of internal tools would look wrong in wp-admin.
4. **Native-first.** Reach for WordPress's own components (`.button`, `.notice`, `.form-table`, `.nav-tab-wrapper`, `.postbox`) before building your own. Style on top, don't replace.
5. **Scope everything.** All custom CSS lives under a single `.otm-wp` wrapper so it is impossible to leak into the rest of the dashboard. This is the WordPress equivalent of the platform's "don't override the host" rule.
6. **Follow WordPress, not just OTM.** Plugin code must meet WordPress engineering standards (prefixing, escaping, nonces, capabilities, i18n). Brand polish never comes at the cost of these.

---

## 2. Brand constants (shared with all OTM work)

These do not change between surfaces. Values are canonical in `../platform/otm-tokens.css`.

```
Navy   #1a365d   headings, primary emphasis, accent borders
Blue   #1e4d8c   links, primary buttons
Gold   #d4a029   the single highest-emphasis CTA, sparing emphasis
Teal   #1a8a7d   success / growth / positive metrics (never a button)
```

- **Button rule (unchanged):** primary actions are blue; the one highest-emphasis CTA on a screen may be gold; **there is no teal button.**
- **No em dashes** in UI copy. Use a colon, a period, or parentheses.
- **No gradients, no decorative fonts, no heavy shadows or glows.**

### Where this set deliberately differs from the platform

| | Platform / Internal Tools | WordPress Plugins |
|---|---|---|
| Surface ownership | Owns the whole screen | Guest inside wp-admin |
| Shell | Full navy sidebar + header | None — use wp-admin's chrome |
| Base palette | Navy / dark surfaces prominent | White + light gray; navy used only as an accent |
| Typography | Inter (loaded by the tool) | wp-admin's native UI font (do not load Inter) |
| Auth / identity | Google OAuth, user block in sidebar | WordPress's own auth + `current_user_can()` |
| Density | Information-dense app | Light, native admin spacing |

---

## 3. Typography

Use the **WordPress admin UI font** (the system stack wp-admin already applies). Do **not** enqueue Inter or any web font for admin screens — it adds weight and makes the plugin look foreign to the dashboard.

- Screen title (`<h1>` / `.otm-title`): 20px, weight 600, navy.
- Card title: 14px, weight 600, default text color (`#1d2327`).
- Body: inherit wp-admin (13–14px). Secondary text `#50575e`.
- Section label / overline: 11px, uppercase, weight 600, letter-spacing 0.06em, muted.
- Monospace (keys, shortcodes, code): the system mono stack or WP's `<code>`.

The leading-dot OTM mark (`.OTM`) may appear once in a screen header if you want a light brand signature (`<span class="otm-title">.OTM Job Board</span>` with the dot in gold). It is optional here and should never dominate.

---

## 4. Layout

Standard WordPress admin page structure. Wrap your screen so the accent layer can scope to it:

```html
<div class="wrap">
  <div class="otm-wp">
    <div class="otm-header">
      <div>
        <h1 class="otm-title">Job Board Settings</h1>
        <div class="otm-subtitle">Manage listings, sync, and display options</div>
      </div>
      <button class="button otm-btn-primary">Add listing</button>
    </div>

    <!-- tabs (WordPress-native) -->
    <h2 class="nav-tab-wrapper">
      <a href="#" class="nav-tab nav-tab-active">General</a>
      <a href="#" class="nav-tab">Display</a>
      <a href="#" class="nav-tab">Advanced</a>
    </h2>

    <div class="otm-card otm-card--accent">
      <div class="otm-card-title">Listing source</div>
      <!-- use the Settings API + .form-table for fields -->
    </div>
  </div>
</div>
```

- Keep `.wrap` so the page sits correctly within wp-admin.
- Use `nav-tab-wrapper` for tabbed settings, the **Settings API** + `.form-table` for option forms, and `.postbox` or `.otm-card` for grouped content.
- Don't impose a fixed-width OTM container or a custom sidebar; let wp-admin handle page width and navigation.

---

## 5. Components

All components ship in `otm-wp-admin.css`, scoped under `.otm-wp`. See `otm-wp-showcase.html` for rendered examples.

- **Header** (`.otm-header`, `.otm-title`, `.otm-subtitle`): screen title with optional right-aligned action and a bottom hairline.
- **Card** (`.otm-card`, `.otm-card-title`): a lighter cousin of `.postbox`. Optional accent left border: `.otm-card--accent` (navy), `--gold`, `--teal`.
- **Buttons:** add `.otm-btn-primary` (blue) or `.otm-btn-cta` (gold, one per screen) to WordPress's `.button`. Plain secondary actions can stay as native `.button`. No teal button.
- **Badges** (`.otm-badge` + `--neutral / --success / --warning / --error / --info`): compact status pills.
- **Callout** (`.otm-callout`, `--gold`, `--teal`): inline tip/info block with an accent left border. For system-level admin messages (saved, error, update available) use WordPress's native `.notice .notice-success|warning|error` instead.
- **Table** (`.otm-table`): a light table for plugin data views. For full list management (sortable, bulk actions, pagination) use WordPress's `WP_List_Table` / `.wp-list-table` instead.
- **Section label** (`.otm-section-label`): uppercase group heading.

Use native components where one exists; only reach for the OTM component when you genuinely need the lighter, branded variant.

---

## 6. Color usage in wp-admin

- Keep surfaces **white / light gray**. Navy is an **accent** (headings, a card's left border), not a background.
- Be mindful that admins can choose their own **admin color scheme**. Stick to OTM accents (navy/gold/teal) plus neutral grays, which read fine across schemes; don't assume the default blue admin theme.
- Reserve **gold** for the single highest-emphasis CTA or a small emphasis. Reserve **teal** for success/positive states (and never as a button).
- Semantic states use the light backgrounds defined in the CSS (`--otm-success-bg`, etc.).

---

## 7. WordPress engineering standards (non-negotiable)

Brand polish never overrides correct, safe WordPress code. Every OTM plugin must:

- **Prefix everything** — functions, classes, hooks, option keys, handles, CSS — with an `otm_` / `OTM_` / `.otm-` prefix to avoid collisions. The CSS wrapper class is `.otm-wp`.
- **Scope your styles.** Never style bare element selectors globally. All rules sit under `.otm-wp` (this file already does). Enqueue your admin CSS **only on your screen** via the `admin_enqueue_scripts` hook-suffix check — never load it dashboard-wide.
- **Enqueue properly** with `wp_enqueue_style` / `wp_enqueue_script` and a version string. Do not inline `<link>`/`<style>` or hardcode asset URLs; use `plugins_url()`.
- **Check capabilities** with `current_user_can()` on every admin action; render screens only for permitted roles. Authentication is WordPress's — there is no OAuth/identity block here.
- **Verify nonces** (`wp_nonce_field()` / `check_admin_referer()`) on every form submission and AJAX request.
- **Sanitize on input, escape on output** — `sanitize_text_field()`, `esc_html()`, `esc_attr()`, `esc_url()`, `wp_kses()` as appropriate. Never echo unescaped data.
- **Use the Settings API** (`register_setting`, `add_settings_section`, `add_settings_field`) for option screens rather than rolling your own form handling.
- **Internationalize** all user-facing strings with `__()` / `esc_html__()` and a consistent text domain that matches the plugin slug.
- **Respect the data lifecycle** — register activation/deactivation hooks, and clean up options/tables on uninstall via `uninstall.php` or `register_uninstall_hook()`.
- **Don't dequeue or override core/admin styles**, and don't ship a plugin that restyles screens you don't own.

---

## 8. Accessibility

Same bar as the rest of OTM:

- **Contrast** at least 4.5:1 for body text; 3:1 for large text and UI borders. Navy and the muted gray both clear this on white.
- **Keyboard:** every control reachable and operable, with a visible focus ring (shipped in `otm-wp-admin.css`; do not remove WordPress's focus styles either).
- **Semantics:** real `<button>` for actions, `<a href>` for navigation, `<label>` tied to every field. Mirror WordPress's own accessible patterns.
- **Motion:** respect `prefers-reduced-motion` (already handled in the CSS).

---

## 9. Front end (client-facing components)

Out of scope for this version — these guidelines cover **wp-admin only**. When a plugin renders public components (e.g. a job board on the client's live site), the governing rule is **accents only over a neutral base**: inherit the client's theme, use the OTM palette solely for small accents (links, focus rings, a primary button), and never impose OTM navy, an OTM logo, or web fonts on the client's site. A dedicated front-end section can be added here when we need it.

---

## 10. Cursor / AI assistant instructions

When using this file as context to generate an OTM WordPress plugin, include this prompt prefix:

```
You are building a WordPress plugin for OTM (Old Town Media), typically for a
client site (management, maintenance, or small features like job boards). Follow
wordpress-plugins/OTM-WORDPRESS-PLUGIN-GUIDELINES.md. Key rules:

- This is wp-admin only. The plugin is a GUEST inside WordPress admin: be light,
  near-native, and add OTM brand as ACCENTS ONLY. No navy app shell, no OTM
  sidebar, no dark surfaces, no OAuth/identity block (that is the platform set,
  not this one).
- Use WordPress-native markup/classes first (.wrap, .button, .button-primary,
  .notice, .form-table, .nav-tab-wrapper, .postbox, WP_List_Table). Layer OTM
  polish on top via otm-wp-admin.css.
- Enqueue otm-wp-admin.css with wp_enqueue_style ONLY on your plugin's screen
  (check the admin_enqueue_scripts hook suffix). Never load it dashboard-wide.
- Wrap your screen in <div class="wrap"><div class="otm-wp"> ... so all custom
  styles stay scoped. Never style bare/global selectors or restyle wp-admin.
- Use the OTM accent palette (navy #1a365d headings/accents, blue #1e4d8c links/
  primary buttons, gold #d4a029 for the single top CTA, teal #1a8a7d for success
  only). Primary buttons are blue; one gold CTA max; NO teal button.
- Use the WordPress admin UI font. Do NOT enqueue Inter or any web font.
- Keep surfaces white/light-gray; navy is an accent, not a background.
- Meet WordPress standards: prefix everything (otm_/OTM_/.otm-), check
  current_user_can(), verify nonces, sanitize on input and escape on output, use
  the Settings API for options, and internationalize strings with a text domain.
- Accessible: labels on fields, keyboard operable, visible focus rings, 4.5:1
  contrast, respect prefers-reduced-motion.
- Never use em dashes in UI copy.
```

---

## 11. Most-missed elements (check these every time)

1. **CSS is scoped to `.otm-wp`** and the stylesheet is enqueued only on the plugin's own screen — nothing leaks into the rest of wp-admin.
2. **Native components used first** (`.button`, `.notice`, `.form-table`, tabs) with OTM accents layered on, not reinvented.
3. **No web font** — the screen uses wp-admin's native UI font, not Inter.
4. **Button colors** are blue/gold only; one gold CTA at most; no teal button.
5. **Security basics** present: capability checks, nonces, sanitize/escape, prefixed handles and option keys.
6. **Light surfaces** — white/gray base with navy used only as an accent, not a background.
