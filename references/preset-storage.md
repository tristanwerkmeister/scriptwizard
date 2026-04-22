# Preset Storage

How to generate the scripting skill file, and how to read, write, list, rename, and delete preset records. Read this before any filesystem operation on presets.

---

## Generating the scripting skill file

This is the primary output of a setup or update session. At the end of section 1.7 (and after any management operation that changes preset content), fill `references/scripting-skill-template.md` and deliver the result to the user.

### Placeholder mapping for the scripting skill template

| Placeholder | Source |
|---|---|
| `{PRESET_NAME}` | The user-chosen preset name (e.g., "Aviation Beat") |
| `{PRESET_SLUG}` | Derived from `{PRESET_NAME}`: lowercase, spaces to hyphens, strip special characters |
| `{LANGUAGE}` | Area 1 of setup-areas.md |
| `{PUBLICATION_CONTEXT}` | The directive block from Area 2 |
| `{VOICE_PROFILE}` | The confirmed voice profile from Area 3 |
| `{EDITORIAL_STANDARDS}` | The converted newsroom standards from Area 4 |
| `{STYLE_RULES}` | The extracted/converted style rules from Area 5 |
| `{BEAT_SPECIFIC_WARNINGS}` | Table rows built from beat risks named in Area 2 (see below) |
| `{LENGTH_DEFAULTS}` | A markdown table of default word counts by structure type, built from preferences captured in Area 2. Sensible defaults if the journalist didn't specify: News ~140 words (~56s), Explainer ~170 words (~68s), Narrative ~200 words (~80s). |
| `{HARD_STOPS}` | Bulleted list of hard-stop topics from Area 4. Format: `- **[Topic]:** [One-line reason]`. If none designated, use: `_No hard stops configured. All topics proceed to the sensitivity check._` |
| `{PRESET_NOTES}` | If the preset rated Adequate: include the intro line followed by a bulleted list — `"Areas flagged as weak during setup review, for attention at next partial update:\n\n- [weak area 1]\n- [weak area 2]"`. If Strong: empty string — the NOTES section body remains completely blank. |

### Building `{BEAT_SPECIFIC_WARNINGS}`

Same rules as in `references/preset-template.md`. Convert each beat risk the journalist named in Area 2 into a `| Scenario | Warning |` table row. If they named none, leave `{BEAT_SPECIFIC_WARNINGS}` empty.

### Self-check before delivering

After filling all placeholders, scan the file for any remaining `{CURLY_BRACES}`. If any remain, fill them or (if genuinely not applicable) delete the line they're on.

### Scripting section — copy verbatim

The `## SCRIPTING` section and everything under it must be copied from the template exactly as written. Do not adapt, compress, or rewrite any of the scripting logic based on the preset content — customisation happens through the preset sections above it, not by modifying the scripting defaults. The only lines that change in the scripting section are the preset name references (e.g., "update my {PRESET_NAME} preset") which are filled like any other placeholder.

### Delivering the file

Present the completed scripting skill file to the user as a downloadable file, named `script-wizard-{slug}.md`. Then give the installation instructions from section 1.7 of SKILL.md.

---

## Where presets live

Presets are markdown files in the `presets/` folder inside this skill. Each file is named `{slug}.md` (e.g., `aviation-beat.md`).

**Always use `${CLAUDE_SKILL_DIR}` to reference the skill's own directory.** This variable resolves to the absolute path of the folder containing `SKILL.md`, regardless of where the skill is installed or what the current working directory is. All file operations in this document use it.

Full preset path: `${CLAUDE_SKILL_DIR}/presets/{slug}.md`

---

## Detecting writeability

Before the first write in a setup session, check whether presets can be saved persistently. Two things must both be true: the write must succeed, and the path must be on a real persistent filesystem — not ephemeral VM storage.

**Step 1 — Check the skill path.**

Inspect `${CLAUDE_SKILL_DIR}`. If it starts with `/mnt/` (e.g., `/mnt/skills/user/script-wizard/`), you are running inside Claude Desktop's VM. Writes to this path will not survive the session. Treat as **read-only immediately** — skip the write test and go to the read-only path.

**Step 2 — If the path looks persistent, try a write.**

Try with the Write tool first:
- Path: `${CLAUDE_SKILL_DIR}/presets/.writetest`
- Content: `test`

If the write succeeds, delete the file and mark the session as **writeable**.

If the Write tool isn't available or fails, try with bash:

```bash
mkdir -p "${CLAUDE_SKILL_DIR}/presets" && touch "${CLAUDE_SKILL_DIR}/presets/.writetest" && rm "${CLAUDE_SKILL_DIR}/presets/.writetest"
```

If this succeeds, mark the session as **writeable**.

**Step 3 — If both fail:**

Mark the session as **read-only**. Follow the read-only path below.

**Important:** A missing `presets/` directory is not the same as read-only — create it as part of the first save rather than treating its absence as a failure. The write test above handles this with `mkdir -p`.

**Cache the result for the session.** Once you know the mode, don't re-test — it won't change within a conversation.

---

## Preset record — placeholder mapping

The preset record (`references/preset-template.md`) is a lightweight management file saved to `presets/`. It lets this Setup skill list, update, duplicate, and rename presets. It is **not** what the journalist installs — the scripting skill (see above) is.

Before saving a preset record, fill every placeholder in `preset-template.md`:

| Placeholder | Source |
|---|---|
| `{PRESET_NAME}` | Section 1.4 of SKILL.md — what the user named the preset (e.g., "Aviation Beat") |
| `{PRESET_SLUG}` | Derived from `{PRESET_NAME}`: lowercase, spaces to hyphens, strip special characters (e.g., "Aviation Beat" → `aviation-beat`). If stripping produces a slug that already exists (e.g., "BBC/Health" and "BBC-Health" both become `bbc-health`), append `-2` or ask the user to choose a different name. |
| `{LANGUAGE}` | Area 1 of setup-areas.md (e.g., "English (UK)") |
| `{NEWSROOM_OR_NONE}` | From Area 2 — the publication name if given, or `none` if freelancer/unspecified |
| `{BEAT_OR_NONE}` | From Area 2 — the beat/subject area if given, or `none` |
| `{PUBLICATION_CONTEXT}` | The directive block assembled in Area 2, covering identity, reach, audience, knowledge baseline, niche calibration, and social goals |
| `{VOICE_PROFILE}` | The confirmed directive voice profile from Area 3 |
| `{EDITORIAL_STANDARDS}` | The converted newsroom standards from Area 4 |
| `{STYLE_RULES}` | The extracted/converted style rules from Area 5 |
| `{CREATION_DATE}` | Today's date in ISO format (YYYY-MM-DD). Use the same value for both `created` and `updated` on first save. On partial updates, only change `updated`. |
| `{BEAT_SPECIFIC_WARNINGS}` | Table rows built from `{BEAT_RISKS}` captured in Area 2 — see below |
| `{LENGTH_DEFAULTS}` | Same as the scripting skill — markdown table of per-structure defaults from Area 2. |
| `{HARD_STOPS}` | Same as the scripting skill — bulleted list from Area 4, or the "none configured" line. |
| `## NOTES` | Not a placeholder — if the preset rated Adequate, insert the line `"Areas flagged as weak during setup review, for attention at next partial update:"` followed by a bulleted list. If Strong, leave the section body completely empty (keep the header and markers). |

### Building `{BEAT_SPECIFIC_WARNINGS}`

`{BEAT_RISKS}` is the list of story-risk categories the journalist named in Area 2. Convert each into a sensitivity warnings table row in the same `| Scenario | Warning |` format as the defaults.

Examples:

- Health reporter named "medical advice, vulnerable patients":
  ```
  | Medical claims / dosages | AI hallucinates numbers and drug names. Verify every dose, side effect, and study citation against primary sources. |
  ```
- Business reporter named "embargoes, market-moving facts":
  ```
  | Embargoed material | AI may not respect embargo dates. Double-check nothing in the draft references embargoed information. |
  | Market-moving facts | Wrong numbers on market-moving stories can move markets. Verify every figure against primary source before posting. |
  ```
- Aviation/safety reporter named "safety-critical technical claims":
  ```
  | Safety-critical technical claims | Technical specs and procedural details are high-risk. Verify against manufacturer documentation or regulatory source. |
  ```

Generate equivalent rows for whatever risks the journalist named. If they named none, leave `{BEAT_SPECIFIC_WARNINGS}` empty (no rows added).

### Self-check before writing

After filling placeholders, scan the file for any remaining `{CURLY_BRACES}` — if there are any, the save is incomplete. Fill them or (if genuinely not applicable) delete the line they're on.

---

## Saving the preset record

The preset record is saved to `presets/` for management housekeeping only. The scripting skill (the journalist's main deliverable) is always presented for download regardless of whether the record saves successfully.

### Writeable case — save directly

When the filesystem is writeable:

1. Fill `preset-template.md` with the journalist's confirmed content.
2. Create `${CLAUDE_SKILL_DIR}/presets/` if it doesn't exist.
3. Write the completed file to `${CLAUDE_SKILL_DIR}/presets/{slug}.md`.

If a preset record with that slug already exists, ask before overwriting.

Then proceed to generate and deliver the scripting skill file (see "Generating the scripting skill file" above).

### Read-only case — skip the record, deliver the scripting skill

When the filesystem is read-only, the preset record can't be saved. This is fine — the journalist's scripting skill doesn't depend on the record. Management operations (list, update, rename) will require the journalist to paste in their current scripting skill file instead of reading from `presets/`.

Do not present this as an error. Simply proceed to generate and deliver the scripting skill file.

---

## Listing presets

When the user says "list my presets" or similar:

1. Read the `${CLAUDE_SKILL_DIR}/presets/` folder.
   - If it doesn't exist or is empty: tell the user no preset records are saved here (their scripting skills are installed separately in Claude). Offer to set up a new one.
2. For each `.md` file in `presets/`:
   - Read the frontmatter (`name`, `language`, and `newsroom` / `beat` fields).
   - Get the file's last-modified date if available.
3. Display as a compact list:

```
Your script presets:
- **Aviation Beat** — Aviation Weekly, English (UK), updated 3 Apr
- **Local Politics** — Westside Gazette, English (US), updated 12 Mar
- **Reuters Health** — Reuters, English (International), updated 1 Feb

Use them via your Script Wizard — [name] skills installed in Claude.
```

---

## Renaming a preset

1. Confirm old name and new name with the user.
2. Validate the new name is unique among existing presets.
3. If the preset record exists: rename the file from `${CLAUDE_SKILL_DIR}/presets/{old-slug}.md` to `${CLAUDE_SKILL_DIR}/presets/{new-slug}.md`. Update the frontmatter `name:` field and the H1 title inside.
4. Generate an updated scripting skill file with the new name and slug.
5. Confirm: "✅ Renamed **{old-name}** → **{new-name}**." Instruct the user to install the new scripting skill file in Claude and remove the old one.

---

## Deleting a preset

1. Confirm explicitly: "Delete the **{preset-name}** preset? This can't be undone."
2. Only proceed on explicit confirmation (yes / confirmed / delete it).
3. If the preset record exists: delete `${CLAUDE_SKILL_DIR}/presets/{slug}.md`.
4. Confirm: "Deleted **{preset-name}**." Remind the user to also remove the `script-wizard-{slug}` skill from Claude.

---

## Duplicating a preset

1. Ask for the source preset name and the new name.
2. Validate the new name is unique.
3. If the preset record exists: copy `${CLAUDE_SKILL_DIR}/presets/{source-slug}.md` to `${CLAUDE_SKILL_DIR}/presets/{new-slug}.md`. Update the copy's frontmatter `name:` and H1 title to the new name.
4. Ask which areas the user wants to change, and walk through only those (using `references/setup-areas.md` for the relevant area guidance).
5. Run the mini-reviews for any areas that changed, then the full review.
6. Save the updated preset record and generate a new scripting skill file for the duplicate.
7. Instruct the user to install the new scripting skill file alongside the original.

This is the fast path when a journalist wants a second preset that's mostly the same as an existing one (e.g., same voice, different newsroom standards).

---

## A note on privacy and portability

Scripting skill files are plain markdown. A journalist can:

- Share their scripting skill with a colleague by sending them the `script-wizard-{slug}.md` file.
- Back up their skills by copying the `.md` files.
- Move skills between machines by copying the files and re-installing.
- Edit a scripting skill directly in a text editor — the section markers make this safe for anyone comfortable with markdown.

Nothing in a scripting skill file is encrypted or obfuscated. Don't suggest saving anything sensitive (passwords, source contact details, unpublished embargoed material) in a preset — these are config files, not a secure store.
