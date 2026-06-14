# OTM Claude Skill Guidelines

How OTM authors, names, versions, and ships **Claude skills** — the reusable instruction packets that make Claude run our repeatable workflows the same way every time. Unlike the [`platform/`](../platform/) and [`wordpress-plugins/`](../wordpress-plugins/) sets (which govern how things *look*), this set governs how a skill is *structured, governed, and distributed*. It is technical/quality standards, not UX.

## What's in here

| File | Purpose |
|------|---------|
| **`OTM-CLAUDE-SKILL-GUIDELINES.md`** | The written spec, in 10 sections: when to build a skill, repo anatomy, the description/trigger contract, writing the body, references/assets, naming + the `claude-skill` topic, versioning & Skill Sync distribution, testing, do's & don'ts, and a starter template. Start here. |
| **`templates/SKILL.md`** | A copy-paste starter `SKILL.md` to fill in. |
| **`examples/skill-utm-namer/`** | A complete minimal worked example (the three required files + a reference) you can read end to end as a model. |

## Quick start

1. Read `OTM-CLAUDE-SKILL-GUIDELINES.md` — especially §3 (the description is the product) and §4 (ask, don't assume).
2. Copy `templates/SKILL.md` into a new `skill-<slug>` repo and fill in every `[bracket]`.
3. Add `skill.json` and `README.md` (see §2), test the six cases in §8, then tag the repo `claude-skill` so Skill Sync (`otm-skills`) can distribute it.

## Most-missed elements (check these every time)

1. **Description earns its triggers** — quoted user phrases, plus what it does *not* do and who it hands off to (§3).
2. **Ask, never fabricate** — missing client context triggers a question, not an invention (§4).
3. **Slug matches everywhere** — repo name = `SKILL.md` `name` = `skill.json` `name` = install folder (§6).
4. **`claude-skill` topic set** — without it the skill is invisible to Skill Sync (§6–§7).
5. **Version bumped + changelog line** on every change; semver in `skill.json` (§7).

## Building with Cursor / Claude

Most of this is non-code. Hand the technical steps (repo creation, topic, version push) to your AI assistant with: "Follow `claude-skills/OTM-CLAUDE-SKILL-GUIDELINES.md`." §10 has a prompt-ready starter.

---

Part of the [OTM Build Standards](../README.md) collection.
