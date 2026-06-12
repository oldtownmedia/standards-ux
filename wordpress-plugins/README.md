# OTM WordPress Plugin Guidelines

Brand and UX standards for OTM WordPress plugins (management, maintenance, and small features like job boards). These plugins live **inside wp-admin** and are a guest there: light, near-native, OTM **accents only**. For full internal tools/apps, use the [`platform/`](../platform/) set instead.

## What's in here

| File | Purpose |
|------|---------|
| **`OTM-WORDPRESS-PLUGIN-GUIDELINES.md`** | The written spec: principles, brand constants, typography, layout, components, color usage, WordPress engineering standards, accessibility, and the AI prompt prefix. Start here. |
| **`otm-wp-admin.css`** | The scoped accent layer for wp-admin screens. Everything is namespaced under `.otm-wp` and reuses the OTM accent hex values from `../platform/otm-tokens.css`. |
| **`otm-wp-showcase.html`** | A living reference that renders the components inside a simulated wp-admin page. Open it in any browser. |

## Quick start

1. Wrap your plugin screen so styles stay scoped:
   ```html
   <div class="wrap"><div class="otm-wp"> ...your screen... </div></div>
   ```
2. Enqueue the CSS **only on your screen** (never dashboard-wide):
   ```php
   add_action('admin_enqueue_scripts', function ($hook) {
     if ($hook !== $my_page_hook) return;
     wp_enqueue_style('otm-wp-admin', plugins_url('otm-wp-admin.css', __FILE__), [], '1.0.0');
   });
   ```
3. Build with WordPress-native components first (`.button`, `.notice`, `.form-table`, `.nav-tab-wrapper`, `.postbox`, `WP_List_Table`) and layer OTM polish with the `.otm-*` classes.

## Most-missed elements (check these every time)

1. **CSS scoped to `.otm-wp`** and enqueued only on the plugin's screen — nothing leaks into wp-admin.
2. **Native components used first**, OTM accents layered on (not reinvented).
3. **No web font** — use wp-admin's native UI font, not Inter.
4. **Buttons blue/gold only**, one gold CTA max, no teal button.
5. **Security basics**: capability checks, nonces, sanitize on input + escape on output, prefixed handles/options.

## Using with Cursor / Claude

Paste the prompt prefix in `OTM-WORDPRESS-PLUGIN-GUIDELINES.md` §10 as context so the assistant stays native, scoped, accent-only, and standards-compliant.

---

Part of the [OTM UX Guidelines](../README.md) collection.
