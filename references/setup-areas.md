# Setup Areas

Detailed guidance for each of the five setup areas. Read the relevant section before walking a user through that area (or before any partial update to that area).

---

## Area 1: Language

Ask:
- What language should scripts be written in?
- If English: which variant? (British / American / International)

Store as the preset's `language` field.

---

## Area 2: Publication & Audience

This shapes everything downstream — voice, vocabulary, assumed knowledge, hook strategy, framing.

Ask:

> **Tell me about your publication and audience:**
>
> - What's the name and type of your publication? (e.g., national broadcaster, local newspaper, B2B trade magazine, digital-native news outlet, international wire service)
> - What's the geographic reach? (e.g., hyper-local/city-level, regional, national, international, or geography-independent like a global niche community)
> - What's your beat or subject area? (e.g., general news, aviation industry, local politics, tech, health)
> - Who is your typical viewer on social? (e.g., general public, industry professionals, local community, policy wonks)
> - How much can you assume your audience already knows about your beat?
> - What's the goal of your social video presence? (e.g., build brand awareness for the publication, make local stories travel to a national audience, deepen engagement with an existing niche community, drive traffic to long-form content, reach a younger demographic)
> - **What kinds of stories on your beat carry the most risk if details are wrong?** (e.g., legal exposure, source safety, safety-critical facts, embargoed information, medical/financial advice) — I'll use this to tailor the warnings in your preset.

From their answers, generate a `{PUBLICATION_CONTEXT}` block — a concise set of directives that captures:

- **Publication identity:** name, type, positioning
- **Geographic reach:** hyper-local, regional, national, international, or community-based, and how this affects framing
- **Beat/subject area:** what topics the journalist typically covers
- **Audience profile:** who the viewer is, what they care about
- **Knowledge baseline:** what can be assumed vs. must be explained (be specific — "assume the viewer knows what an AD is" or "assume the viewer has never heard of widebody aircraft")
- **Niche calibration:** how specialist the scripts should lean
- **Social media goals:** what the social video presence is trying to achieve, and how that shapes hook strategy

Also capture `{BEAT_RISKS}` separately — the story-risk categories from the final question. These feed into the sensitivity warnings table at generation time.

---

## Area 3: Voice Profile

**Read `voice-profile-guide.md` before starting this area.**

**If the user already provided scripts in the fast path (section 1.2), skip the Option A/B question and go straight to the Option A analysis procedure below.**

Otherwise, offer two paths:

> **How should I learn your voice?**
> - **Option A — Script examples** (recommended): Paste 3–5 sample scripts of vertical videos, that you've written yourself or of someone you'd like to take inspiration from (ideally a mix of hard news and lighter stories)
> - **Option B — Guided questions**: I'll ask you specific questions about how you write.

### Option A (examples)

Ask for scripts with explicit diversity:

> Please paste 3–5 scripts, separated by `---`. These can be scripts you've written yourself, or from someone whose voice you'd like to take inspiration from. For this to work well, try to include a mix:
> - At least one **hard news** story on your beat
> - At least one **lighter or feature** story
> - If possible, one longer-form piece
>
> Scripts all on the same story type will produce a voice profile that only works for that story type.

If they paste three scripts of the same type, flag it:

> These all look like [hard news / features / explainers]. I can build a profile from them, but it'll be calibrated to this story type only. Do you want to add at least one of a different type, or proceed and note this limitation in the profile?

Analyse using the voice profile guide. Present the profile as directives.

### Option B (guided questions)

Use the guided questions from `voice-profile-guide.md`. Convert answers into directive form. Show the strong/weak examples from the guide and ask the user to assess whether their profile is specific enough.

### Force a structured review — both options

> ⚠️ **Thorough review required.** Before we save this:
> - **Name at least one thing in this profile that's wrong or not quite you.**
> - **Name at least one thing you'd expect to see that's missing.**
>
> If you genuinely can't find anything to change, say so — but really look first. Voice profiles that get rubber-stamped tend to produce generic scripts later.

Wait for the diff responses. Incorporate edits.

### Voice stress test (mini-review)

Before confirming the profile, **read `review-checklist.md` section 6** and run the stress test: mentally draft how the voice would handle (a) a hard news story on their beat and (b) a lighter feature on their beat. If the profile would produce the same register for both, flag it and ask the user to add tone variation notes.

Store the confirmed profile as `{VOICE_PROFILE}`.

---

## Area 4: Editorial Standards

**Read `editorial-ethics.md`** for available frameworks and conversion rules.

Ask newsroom standards first; offer frameworks as a gap-filler:

> Start with your newsroom's standards. Paste them, summarise them, or tell me the key ones. These are primary.
>
> Once I have those, I can check them against a foundational framework like the [IFJ Global Charter of Ethics for Journalists](https://www.ifj.org/who/rules-and-policy/global-charter-of-ethics-for-journalists) and flag anything your newsroom policy doesn't cover — so you can decide whether to add it.

If the user has no newsroom standards (e.g., freelancer), offer a framework as the starting point.

Convert verbose guidelines using the conversion rules in `editorial-ethics.md`.

Store confirmed standards as `{EDITORIAL_STANDARDS}`.

---

## Area 5: Style Guide

Offer two paths (import is the recommended default):

> **How would you like to set up your style guide?**
> - **Option A — Import** (recommended): Paste your newsroom's style guide (or the most relevant sections) and I'll extract the key rules
> - **Option B — Manual**: Type or paste your style rules directly

Before importing, tell the user what will happen to their guide:

> I'll extract the ~30 rules most relevant to **spoken short-form video** — spelling, capitalisation, numbers, punctuation, word preferences, words to avoid, title/name conventions.
>
> **I'll drop:** rules that only apply to print (headlines, captions, photo credits, bylines, column widths).
>
> **I'll add:** spoken-specific defaults your print guide probably doesn't cover — how to handle acronyms read aloud (NATO as a word vs. F.B.I. letter-by-letter), how to signal direct quotes in speech.
>
> **Note on numbers:** The scripting skill defaults to preserving numbers exactly as they appear in source material (so $2.3 million stays $2.3 million in the script, not "two point three million dollars"). If your style guide specifies a different rule, I'll add it — otherwise I'll note the default and leave it.
>
> If you want more than 30 rules, tell me which categories matter most and I'll prioritise those.

For extremely long documents, ask the user to narrow to script-relevant sections.

After extraction:

> ⚠️ Review the converted rules carefully — I may misinterpret nuanced guidelines or miss context-specific rules. I've also added spoken-specific defaults marked **[spoken]** — these aren't from your print guide, they're my suggestions for read-aloud scripts. Remove any you disagree with.

### Style guide mini-review

Before confirming, **read `review-checklist.md` sections 1 and 2** and spot-check for:
- Contradictions with the voice profile (e.g., voice says "use contractions," style says "avoid contractions")
- Ambiguity that will produce inconsistent scripts

If you find anything, flag it to the user and reconcile before moving on.

Store confirmed rules as `{STYLE_RULES}`.

---

