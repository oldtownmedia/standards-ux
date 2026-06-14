# UTM Conventions

The canonical rules the `utm-namer` skill applies in Step 2. Kept here, not in
`SKILL.md`, so the instructions stay short and these rules can be edited on their own.

## Casing rules

- **Lowercase everything.** `Facebook` → `facebook`, `Spring` → `spring`.
- **Hyphenate spaces.** `spring launch` → `spring-launch`. Never use spaces or underscores.
- **No punctuation** other than hyphens.

## Canonical vocabulary

Map common synonyms to the one approved token. If a value isn't listed, keep the
lowercased/hyphenated form and flag it for human review.

### `utm_medium` (the channel type)

| Use | Not |
|-----|-----|
| `email` | e-mail, mail, newsletter-email |
| `social` | social-media, smm |
| `cpc` | ppc, paid-search, adwords |
| `display` | banner, banners |
| `referral` | ref, partner |
| `organic` | seo, search |

### `utm_source` (the specific place)

| Use | Not |
|-----|-----|
| `linkedin` | LinkedIn, li |
| `facebook` | Facebook, fb, meta |
| `instagram` | Instagram, ig |
| `google` | Google, googleads |
| `newsletter` | email-blast, mailchimp |

## Parameter order

Always assemble in this fixed order so links are visually consistent:

```
utm_source → utm_medium → utm_campaign → utm_term → utm_content
```

`utm_term` and `utm_content` are optional; include them only when provided.
