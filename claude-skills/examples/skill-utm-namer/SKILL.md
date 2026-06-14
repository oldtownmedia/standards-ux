---
name: utm-namer
description: >
  Turn a plain-English campaign description into a consistent, correctly tagged
  UTM tracking URL using OTM's naming conventions. Trigger on "build a UTM",
  "tag this URL", "utm for [campaign]", "tracking link for [campaign]", or when
  a user pastes a destination URL and asks for tracking parameters. Hands off to
  the campaign-plan skill for full campaign setup. Does not shorten links, manage
  a UTM spreadsheet, or pull analytics.
---

# UTM Namer

Turn a campaign description into one consistent UTM-tagged URL, so every link the team ships is tagged the same way and reports cleanly.

**Why this skill exists.** Hand-built UTMs drift — `Facebook` vs `facebook` vs `fb`, `spring_sale` vs `spring-sale` — and inconsistent tags fragment reporting so campaigns look smaller than they are. This skill enforces one casing and vocabulary every time.

## When to use
- "build a UTM", "tag this URL", "utm for [campaign]", "tracking link for [campaign]"
- When a user pastes a destination URL and asks for tracking parameters

## Required inputs
Before building the URL, confirm:
1. **Destination URL** (where the link points).
2. **Source** (where it's posted — e.g. newsletter, linkedin, google).
3. **Medium** (the channel type — e.g. email, social, cpc).
4. **Campaign** (the campaign name).

If any of these four is missing, ASK once, then proceed. Never invent a campaign
name or guess the destination.

## Instructions
### Step 1: Gather the four inputs
Collect destination, source, medium, campaign. Optionally `term` and `content`.

### Step 2: Normalize every value
Apply the rules in `references/utm-conventions.md`: lowercase, hyphenate spaces,
and map common synonyms to the canonical token (e.g. `Facebook` → `facebook`,
`e-mail` → `email`). Use the canonical vocabulary list; if a value isn't on it,
keep the lowercased/hyphenated form and note it for review.

### Step 3: Assemble the URL
Append the parameters in fixed order:
`?utm_source=…&utm_medium=…&utm_campaign=…` (then `utm_term`, `utm_content` if given).

### Step 4: Return the link and a one-line breakdown
Give the finished URL plus a small table of each parameter's final value, and flag
any value that wasn't on the canonical list so a human can confirm it.

## Output format
```
https://example.com/landing?utm_source=newsletter&utm_medium=email&utm_campaign=spring-launch

source   → newsletter
medium   → email
campaign → spring-launch
```
