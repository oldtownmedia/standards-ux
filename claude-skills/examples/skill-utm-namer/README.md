# UTM Namer

A minimal OTM Claude skill that turns a campaign description into one consistently tagged UTM tracking URL. Included in the [OTM Claude Skill Guidelines](../../OTM-CLAUDE-SKILL-GUIDELINES.md) as a complete worked example.

## What it does

Ask it to "build a UTM" (or paste a destination URL) and it collects the four required values — destination, source, medium, campaign — normalizes them to OTM's canonical casing and vocabulary, and returns a finished tracking URL plus a breakdown of each parameter.

## When to use

"build a UTM", "tag this URL", "utm for [campaign]", "tracking link for [campaign]", or when you paste a destination URL and ask for tracking parameters.

## What it needs

Nothing connected — it's self-contained (`requires` is empty). It uses the conventions in `references/utm-conventions.md`.

## What it does NOT do

It does not shorten links, maintain a UTM spreadsheet, or pull analytics. For full campaign setup it hands off to the campaign-plan skill.

## Anatomy (what to copy)

| File | Role |
|------|------|
| `SKILL.md` | Instructions Claude reads — note the description's trigger phrases + boundary line, and the "ask, don't fabricate" rule in Required inputs. |
| `skill.json` | Metadata for SkillSync — slug matches `SKILL.md`, semver version, `scope: org`. |
| `references/utm-conventions.md` | The canonical vocabulary the skill reads at run time, kept out of `SKILL.md` to stay lean. |
