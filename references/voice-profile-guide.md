# Voice Profile Guide

Read this when creating or updating a voice profile — during Option A (analysing pasted scripts) or Option B (guided questions).

---

## What a voice profile should cover

A voice profile is directive, not descriptive. "Sentences average 12 words, never over 25" is directive. "The journalist writes concisely" is descriptive and useless. When extracting from scripts or guided answers, always convert observations into instructions.

Cover these categories. Not every category will apply to every journalist — skip the ones that genuinely aren't distinctive, but don't skip a category just because it's hard to pin down.

### 1. Sentence shape
- Typical and maximum length (e.g., "6–14 words, never over 20")
- Sentence rhythm patterns (e.g., "alternates short punches with longer setups")
- Fragment use (e.g., "uses sentence fragments at emphasis points — 'And it worked.'")
- Compound vs simple (e.g., "avoids multi-clause sentences; breaks them into two")

### 2. Word choice
- Register (formal / professional / conversational / informal)
- Contractions (always / never / context-dependent)
- Preferred vs avoided verbs (e.g., "says" over "states", "got" over "obtained")
- Jargon handling (explain immediately / assume audience knows / flag as jargon)
- Characteristic words or phrases the journalist reaches for
- Words or phrases they never use

### 3. Structural habits
- Hook style (event-first / question / contradiction / statistic / scene)
- Where the "why it matters" sits (immediately after hook / near the end / woven throughout)
- Length of the setup before the main fact lands
- Callback patterns (does the ending mirror the opening?)

### 4. Voice stance
- Direct address to viewer ("you") — how often, how casually
- Self-reference ("I", "we", neither) — and which one
- Distance from subject (reporter-as-observer vs reporter-as-participant)
- Opinion — never stated / clearly signalled as opinion / implicit in framing
- Humour — present / absent / only in lighter stories

### 5. Tone variation across story types
- How the voice shifts between hard news and features (this is the most common gap in auto-generated profiles)
- What stays constant regardless of topic (the signature elements)
- Red lines — tones that are never appropriate even for the lightest story

### 6. Audience relationship
- How much context is assumed
- How much is explained
- Whether the journalist addresses the viewer as insider or outsider

---

## Strong vs weak examples

Show these when asking the user to assess whether their profile is specific enough.

### Weak (vague, unactionable)

> The journalist writes in a conversational tone, using clear, engaging language. Sentences are short and punchy. The voice is authoritative but accessible, avoiding jargon where possible. Stories are well-structured and end strongly.

This is a description, not a profile. "Conversational," "engaging," "well-structured" could mean anything. Another AI given this profile will produce generic scripts.

### Strong (directive, specific)

> Sentences average 8–12 words; never exceed 18. Opens with the event, not the context — the viewer learns *what happened* before *why it matters*. Uses sentence fragments at emphasis points ("And nobody noticed. For six weeks."). Addresses viewer as "you" once per script, usually near the end. Never uses "folks", "guys", or "listen" — the register is direct but not chummy. For hard news, opinion is absent; for features, mild dry humour is allowed but never punching down. Ends on a specific detail, not a summary.

This is actionable. A different AI given this profile would produce scripts that recognisably match the journalist's style.

---

## Guided questions (Option B)

Ask these in rounds — one round at a time, converting answers into directive form before moving to the next. Don't ask all questions in a single message.

### Round 1: Sentences and words
1. Read out loud one of your recent scripts. How long do your sentences feel — short and punchy, medium, or long and flowing?
2. Do you use sentence fragments? Give me an example if so.
3. Do you use contractions ("don't", "it's", "we're")? Always, never, or depends?
4. What's a word or phrase you reach for a lot? What's one you'd never use, even if it fit?

### Round 2: Structure and hooks
5. Where does your hook usually sit — do you start with an event, a question, a contradiction, a statistic, or a scene?
6. Where in the script does the "why it matters" land — right after the hook, at the end, or woven throughout?
7. How do you end a script? Is there a pattern?
8. When you mention a technical term your audience might not know, do you define it, skip it, or gloss over it quickly?
9. When you attribute a claim in the spoken script, how do you typically do it — "we found", "according to [source]", "[name] told us"? Do you name sources by name, or describe them ("a senior official")? How do you handle it when the source is your own organisation vs. external?

### Round 3: Voice and stance
10. Do you use "I" or "we" in your scripts, or neither?
11. Do you speak directly to the viewer as "you"? How often?
12. Is your opinion ever present in your scripts, or are you strictly reportorial?
13. Is there humour in your voice? In what kinds of stories?

### Round 4: Tone and audience
14. When you're writing a hard news story — say, a fatal accident or a serious policy decision — how does your voice shift compared to a lighter piece?
15. Is there any tone you'd never use, even for the lightest story on your beat?
16. Do you imagine your viewer as someone who knows your beat, or someone encountering it for the first time?
17. How much context do you give before getting to the main point?

---

## Analysis procedure for Option A (pasted scripts)

1. Read all scripts through once without taking notes.
2. On second pass, mark:
   - Average and max sentence length
   - Fragments (and where they appear)
   - Characteristic vocabulary (words that appear across multiple scripts but aren't generic)
   - Hook pattern (event / question / contradiction / stat / scene)
   - Ending pattern
   - Instances of direct address
   - Contractions (always / never / sometimes)
3. Check whether the scripts span hard news and lighter stories. If they don't, flag this to the user.
4. Draft the profile using the categories above — but only include categories where the scripts show a distinctive pattern. Don't invent patterns to fill categories.
5. Convert every observation into an instruction. "Tends to" becomes "default to". "Often" becomes "usually" with an anchor.
