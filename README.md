# Script Wizard

A Claude skill that helps journalists build personalised vertical video script presets — and then use them to draft, review, and iterate on social media scripts.

---

## How it works

Script Wizard is two skills in one package:

1. **Script Wizard Setup** (`SKILL.md` — this skill): walks you through a one-time setup conversation to capture your voice, editorial standards, style guide, and publication context. At the end it generates a personalised scripting skill file for you to install.

2. **Your scripting skill** (generated): a self-contained skill file with your preset baked in. Install it once, then use it in any future conversation to draft scripts, convert articles, or review drafts.

---

## Installation

### Claude Desktop

1. Download or clone this repo.
2. In Claude Desktop: **Add skill → select this folder** (the folder containing `SKILL.md`).
3. Start a conversation and say **"set up Script Wizard"** to begin.

At the end of setup, Script Wizard generates your personal scripting skill file (`script-wizard-{your-preset-name}.md`). To install it:

1. Create a new folder anywhere on your computer.
2. Move the downloaded file into that folder and rename it to `SKILL.md`.
3. In Claude Desktop: **Add skill → select that folder**.

### claude.ai Projects

1. In your Claude Project, open the knowledge base and upload `SKILL.md` and the entire `references/` folder.
2. Start a conversation in the Project and say **"set up Script Wizard"**.
3. At the end of setup, upload the generated scripting skill file to the same Project's knowledge base.

---

## What setup collects

Setup walks through five areas:

1. **Language** — which language and variant your scripts are in
2. **Publication & audience** — who you work for, your beat, your audience, your social goals
3. **Voice profile** — how you write (extracted from sample scripts, or built through guided questions)
4. **Editorial standards** — your newsroom's non-negotiable rules
5. **Style guide** — spelling, vocabulary, formatting conventions

Structure, length, and hook type are set per-story at scripting time — they depend on the story, not the preset.

---

## Using your scripting skill

Once your scripting skill is installed, in any conversation:

- **"Script this: [paste your notes]"** — drafts from newsgathering material
- **"Convert this article to a script: [paste article]"** — extracts the best angle for your audience
- **"Review this draft: [paste script]"** — critiques against your voice and standards
- **"Shorter" / "punchier" / "different hook"** — iterates immediately

---

## Updating a preset

Come back to this Setup skill and say **"update the [voice / standards / style / publication context] in my [preset name] preset"**. Setup walks through just that section and generates an updated scripting skill file to reinstall.

---

## File structure

```
SKILL.md                          ← The setup skill (install this)
references/
  scripting-skill-template.md    ← Template for generated scripting skills
  setup-areas.md                 ← Guidance for each setup area
  voice-profile-guide.md         ← Voice analysis and guided questions
  editorial-ethics.md            ← Foundational ethics frameworks
  review-checklist.md            ← Full and mini-review procedures
  preset-storage.md              ← Preset record management
  preset-template.md             ← Preset record template
```

---

## Privacy

Presets are plain markdown files — nothing is encrypted or sent anywhere beyond your normal Claude usage. Don't put anything sensitive in a preset (source contact details, unpublished embargoed material). These are config files, not a secure store.

Generated scripting skills are portable: share them with a colleague by sending the file, or move between machines by copying it.
