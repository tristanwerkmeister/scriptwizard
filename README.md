# Script Wizard

A vertical social media video script assistant for journalists. Captures your voice, editorial standards, style guide, and publication context — then uses them to draft, review, and iterate on scripts.

There are two versions depending on what AI tools you use:

| | Standalone system prompt | Claude skill |
|---|---|---|
| **Works with** | Any AI (ChatGPT, Gemini, Claude, etc.) | Claude Desktop or claude.ai Projects only |
| **Setup** | Copy one file, paste as system prompt | Install skill folder, run setup conversation |
| **Preset storage** | You copy and save a text block | Skill manages files automatically |
| **File** | `standalone-system-prompt.md` | `SKILL.md` + `references/` |

---

## Option 1: Standalone system prompt

For anyone using ChatGPT, Gemini, Claude, or any other AI assistant with a system prompt or custom instructions field.

### Install

1. Open [`standalone-system-prompt.md`](standalone-system-prompt.md).
2. Copy everything from `=== BEGIN SYSTEM PROMPT ===` to the end of the file.
3. Paste it into your AI tool's system prompt or custom instructions field:
   - **ChatGPT:** Settings → Personalization → Custom instructions
   - **Claude.ai Projects:** Project settings → Project instructions
   - **Gemini:** System instructions (in Advanced settings)

### First session

Say: **"set up Script Wizard"**

You'll be walked through a 10–30 minute setup. At the end, the AI outputs a **preset block** — a block of text to copy and save somewhere (a note, a text file, anywhere).

### Every subsequent session

1. Paste your saved preset block at the start of the chat.
2. Say: **"Script this: [your material]"**

### Updating your preset

Start a new chat, paste your preset block, and say: **"Update the [voice / standards / style / publication] in my preset."** You'll be walked through just that section and get an updated preset block to save.

---

## Option 2: Claude skill

For journalists using Claude Desktop or claude.ai Projects. The skill manages your preset files automatically and integrates directly into Claude conversations.

Script Wizard is two skills in one package:

1. **Script Wizard Setup** (`SKILL.md`): a one-time setup conversation that captures your voice, editorial standards, style guide, and publication context. At the end it generates a personalised scripting skill file for you to install.

2. **Your scripting skill** (generated): a self-contained skill file with your preset baked in. Install it once, then use it in any future conversation.

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

## What setup collects (both versions)

Setup walks through five areas:

1. **Language** — which language and variant your scripts are in
2. **Publication & audience** — who you work for, your beat, your audience, your social goals
3. **Voice profile** — how you write (extracted from sample scripts, or built through guided questions)
4. **Editorial standards** — your newsroom's non-negotiable rules
5. **Style guide** — spelling, vocabulary, formatting conventions

Structure, length, and hook type are set per-story at scripting time — they depend on the story, not the preset.

---

## Using your scripting skill (both versions)

- **"Script this: [paste your notes]"** — drafts from newsgathering material
- **"Convert this article to a script: [paste article]"** — extracts the best angle for your audience
- **"Review this draft: [paste script]"** — critiques against your voice and standards
- **"Shorter" / "punchier" / "different hook"** — iterates immediately

---

## File structure

```
standalone-system-prompt.md       ← Standalone version (any AI tool)
SKILL.md                          ← Claude skill: setup and preset management
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

Presets are plain markdown files — nothing is encrypted or sent anywhere beyond your normal AI usage. Don't put anything sensitive in a preset (source contact details, unpublished embargoed material). These are config files, not a secure store.

Generated scripting skills and preset blocks are portable: share them with a colleague by sending the file or copying the text.
