# Prompt Review Checklist

Read this file when performing any review — the full review after section 1.5 of setup, or the mini-reviews after individual areas in setup-areas.md.

---

## How to Use This Checklist

There are two review modes:

- **Mini-review** — run after a single section is collected (voice, style). Only run the checks relevant to that section. The section headings below note which mini-reviews use which check.
- **Full review** — run after all sections are collected. Run every check.

Go through each relevant check below. Be specific — quote the problematic text, explain why it's a problem, and suggest a concrete fix. Don't say "looks good" unless every check genuinely passes.

---

### 1. Contradictions
*Used in: style mini-review, full review*

Look for conflicts *between* sections, not just within them:

- **Voice vs Script Rules:** Does the voice profile specify sentence lengths that conflict with the "max 15–20 words" script rule? If so, flag it and recommend the voice profile take precedence (the script rules are defaults; the voice is personal).
- **Voice vs Style:** Does the voice say "casual, conversational" but the style guide says "never use contractions"?
- **Voice vs Publication:** Does the voice profile match the publication's positioning? A B2B trade publication with a "chatty, irreverent" voice might work — or it might be a mismatch. Flag it for the user to confirm deliberately.
- **Audience vs Jargon rules:** Does the style guide say "no jargon" but the audience profile says "specialist professionals who expect technical language"? The audience knowledge baseline should win — flag and reconcile.
- **Audience vs Context rules:** Does the script rule say "zero context assumed" but the audience is niche specialists? The publication context should calibrate this — make sure it does.
- **Standards vs Mode:** Do any editorial standards conflict with how article-to-script mode works? (e.g., standards that prohibit republishing any third-party content)
- **Style vs Style:** Are there internal contradictions in the style rules? (e.g., "spell out numbers under 10" alongside "use numerals for all statistics")

### 2. Ambiguity
*Used in: style mini-review, full review*

Rules that could be interpreted differently on each run produce inconsistent scripts. Look for:

- Subjective adjectives without anchors: "engaging," "interesting," "appropriate length" — these need numbers or examples
- "Sometimes" / "occasionally" / "when appropriate" — when exactly?
- "Conversational tone" without specifics — conversational like a news anchor or conversational like a group chat?
- Any rule where you could argue both sides and be right

### 3. Gaps
*Used in: full review*

Check whether these are covered somewhere across all sections. They don't need to be — but if they're missing, flag them as optional additions:

- **Publication identity:** Is it clear what kind of publication this is? A script for a local newspaper's social channel needs different energy than a defence industry trade magazine's.
- **Geographic reach:** Is the framing clear? A hyper-local publication should ground stories in place; a national one should frame for broad relevance; an international one should avoid country-specific assumptions. If this isn't specified, flag it — it significantly affects how scripts open and how context is provided.
- **Social media goals:** Is it clear what the social video presence is trying to achieve? This shapes hook strategy, accessibility, and framing. A local paper trying to make stories travel nationally scripts very differently from the same paper deepening engagement with its existing community. If goals aren't specified, the preset will default to generic choices — which may not serve the journalist well.
- **Goal vs audience tension:** If the social goal involves reaching *beyond* the core audience (e.g., a niche publication building brand awareness, or a local paper going national), is there guidance on how to balance insider specificity with accessibility? This is a common tension that needs an explicit decision.
- **Audience knowledge level:** Is the knowledge baseline specific enough? "Industry professionals" is vague. "Commercial airline pilots and MRO engineers who know what an AD is" is actionable.
- **Niche vs general calibration:** For specialist publications: are there enough signals to lean into the niche? For general publications: is it clear what needs explaining?
- **Numbers:** Does the style guide specify number rules (spell out vs. numeral, thresholds)? If not, the default is to preserve source formatting exactly. Flag if no rule exists and the journalist's beat involves numbers prominently (finance, science, statistics).
- **Attribution:** How to credit sources in a spoken script?
- **Quotation handling:** How to signal a direct quote vs. paraphrase when speaking?
- **Self-reference:** Does the journalist refer to themselves? ("I" vs. "we" vs. impersonal)
- **Audience address:** Do they speak to "you"? How directly?
- **Tone variation:** Is there guidance for adjusting tone between serious and lighter stories?
- **Beat-specific risks:** Are the sensitivity warnings calibrated to this journalist's beat? A health reporter needs medical-claim warnings; an aviation reporter needs safety-critical flags. Generic warnings alone aren't enough.

### 4. Redundancy
*Used in: full review*

- Are any rules stated in both the voice profile and the style guide?
- Are any editorial standards already covered by the script rules?
- Is anything said twice in different words?

Remove duplicates. Keep the more specific version.

### 5. Effectiveness Rating
*Used in: full review — this is the gate before generation*

Assign one of three ratings. The setup flow uses this to decide whether to save the preset or loop back.

- **Strong:** Specific enough that the same prompt would produce consistent, voice-matched scripts across different AI models. Covers the key areas. No major gaps. → **Proceed to test drive (or save, if the user skips test drive).**
- **Adequate:** Works but has some vague areas that will produce inconsistent results. Could be improved with 2–3 specific additions. → **Note the weak areas to the user. Ask if they want to strengthen now or proceed.**
- **Needs work:** Too generic, too many gaps, or contains contradictions that will produce unpredictable output. → **Do not proceed. Walk the user back to the problem areas.**

When assigning a rating, explain *why* — don't just say "Adequate." Quote the specific weak areas and what would move it to Strong.

### 6. Voice Profile Stress Test
*Used in: voice mini-review, full review*

Mentally "run" the voice profile against two scenarios relevant to the journalist's actual beat and publication:

1. A hard news story within their beat (e.g., for an aviation trade journalist: an airworthiness directive grounding a fleet; for a local paper: a council vote on housing)
2. A lighter feature within their beat (e.g., for aviation: a new airline livery reveal; for a local paper: a community fundraiser)

Would the profile produce appropriately different scripts for each, while still sounding like the same person *and* appropriate for the publication?

- **If both scenarios would produce identical register** — profile lacks tone variation. Flag it. Ask the user to add notes on how their voice shifts between serious and lighter stories.
- **If the lighter scenario would sound flippant in a way the publication wouldn't tolerate** — the voice profile isn't anchored to the publication. Flag it.
- **If the hard news scenario would sound generic** — the voice profile is too broad. Push for specificity.

### 7. Audience Calibration Check
*Used in: full review*

Read the assembled preset as if you were writing a script about a moderately technical topic in the journalist's beat. Check:

- Would the script over-explain things the audience already knows? (patronising for niche audiences)
- Would it under-explain things the audience might not know? (confusing for general audiences)
- Does the hook strategy match the audience? (insider angles for specialists, broader stakes for general)
- Is there enough in the publication context to consistently calibrate vocabulary and assumed knowledge?
- Does the framing match the geographic reach? (A hyper-local publication that never mentions place in its scripts is missing its biggest asset. An international outlet that assumes UK/US context will alienate half its audience.)
- Does the hook strategy serve the social goals? (If the goal is making local stories travel, hooks need to be accessible to outsiders. If the goal is deepening niche community engagement, hooks should reward insiders. If both, flag the tension and check that the preset addresses it.)

---

## Review Output Format

End every review with an explicit rating and next step:

> **Rating:** Strong / Adequate / Needs work
>
> **Key issues found:** [list, or "none"]
>
> **Recommended next step:** [proceed to test drive / strengthen these areas first / loop back to the problem area]
