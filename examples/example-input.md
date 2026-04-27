# Example interview — `podcast-show-notes`

A worked example of an architect interview. The user wants to build a skill that turns podcast transcripts into publishable show notes in their voice.

The architect's questions appear in **bold**. The user's answers follow.

---

**User trigger:** *"start a new skill — I want to architect something for my podcast"*

---

**Q1. What are you trying to achieve?**

> I run a weekly podcast on AI tooling. After every recording, writing the show notes for the publishing platform takes me 90 minutes — pulling out the timestamps, summarising segments, listing the tools and links mentioned, drafting an episode summary that sounds like me. I want a skill that takes a transcript file and produces show notes I can publish without editing. Voice should match my prior episodes.

> *Architect captures verbatim.*

---

**Q2. Who should this skill *sound* like?**
> A. A demanding expert with strong opinions, willing to push back
> **B. A pragmatic engineer making trade-offs explicit**
> C. A friendly coach walking someone through their first attempt
> D. A specialist analyst producing a structured artefact
> E. Other → describe in one line

User picks **B**.

---

**Q3. When does the skill fire?**
> A. Live — running with a person on screen, conversational
> B. Async — operates over text or files, no human in loop
> **C. Command-triggered — fires on /foo or specific phrases**
> D. Pipeline step — part of a longer orchestration
> E. Mixed → which is primary?

User picks **C** — *"will paste a transcript and run /show-notes"*.

---

**Q4. What does it produce?**
> **A. A structured document (record, report, spec, plan)**
> B. A live walkthrough (Q&A, conversational guidance)
> C. An action in the world (file written, message sent, code changed)
> D. A multi-modal artefact (slides, diagrams, formatted document)
> E. Multiple → which is primary?

User picks **A**.

---

**Q5. Ship-as-is — one line.**

> If I read it once and would publish it without editing.

---

*(Architect now classifies. Q1 mentions: voice-matching from prior episodes (research), tacit voice knowledge (reference), structured artefact output (Probe H fires), command trigger (Probe E re: file paths), no recommendations (Probe I will be N/A or G).)*

---

**Probe A — Research scope.** Does the build agent need to do research before writing this skill?
> A. No — general knowledge is enough
> **B. Yes — I have sources (one line)**
> C. Yes — agent should find sources for: [topic]
> D. Some — I'll flag specific things

User: **B** — *"my last 10 published show notes; I'll point at the folder."*

---

**Probe B — Reference layer.** Does this skill need a reference layer?
> A. No — fits in a single SKILL.md
> **B. Yes — schemas, examples, case studies, anti-pattern cards (one line)**
> C. Yes — knowledge that grows over time
> D. Maybe — propose one if it would help

User: **B** — *"voice profile distilled from the 10 examples; section structure template."*

---

**Probe C — Tools/scripts.** Does the skill need helper scripts?
> A. No — pure prompt-driven
> **B. Yes — list them (one line)**
> C. Maybe — propose if markdown-instruction would be unreliable

User: **B** — *"a transcript chunker so long episodes don't blow context."*

---

**Probe D — Modes.** Does this skill have multiple modes?
> **A. Single mode**
> B. Multi-mode → list them
> C. Phase-based

User: **A**. *(D-followup skipped.)*

---

**Probe E — Setup/config.** What setup or config does this skill need?
> A. None — pure conversational
> B. Auth/keys
> **C. Local files or paths (one line)**
> D. Multiple — describe

User: **C** — *"path to the show-notes-archive folder, configurable per podcast."*

---

**Probe F — Pushback triggers.** When should the skill refuse, contradict, or push back?
> **A. When the user's request would produce shallow / generic output**
> B. When the user is asking the skill to do work the user should be doing
> C. When the request violates the skill's stated voice or optimise targets
> **D. When information is missing and the skill should ask before guessing**
> E. Other

User picks **A** and **D** — *"if the transcript is too short to fill the section structure, push back rather than padding."*

---

**Probe G — AI-slop defaults to refuse.**
> **A. Generic templates / "standard advice" instead of specific judgement**
> **B. Hedging language**
> **C. Long, comprehensive responses when terse is sharper**
> **D. Sycophantic acknowledgements**
> E. Default fonts / colors
> F. Option-menus when one strong recommendation is the right move
> G. Other → describe

User picks **A, B, C, D**.

---

**Probe H — Response contract.** List 2–4 things every output **must** include.

User:
> Always:
> - Episode title and number
> - One-paragraph summary in my voice
> - Section breakdown with timestamps
> - Tools / links mentioned
>
> When relevant:
> - Guest bio (only if a guest appeared)
> - Quote pulls (only if there's a memorable line)

---

**Probe I — Reasoning discipline.**
> A. Rationale
> B. Risk
> C. Measure
> D. Trade-off
> E. Confidence level
> F. Other
> **G. None — outputs are descriptive, not recommendation-driven**

User picks **G**.

---

*Architect synthesises. Then proposes 10x options.*

---

**Stage 3 — 10x feedback.**

> Here are 4 specific 10x possibilities derived from your answers. For each, pick: bake into v1 / park / decline.
>
> **1.** Given Probe B (voice profile from prior episodes), the skill could **periodically re-distil the voice profile from the most recent N episodes** so it tracks your voice as it evolves. Bake / park / decline?
>
> **2.** Given the structured response contract (Probe H), the skill could **emit a JSON sidecar** alongside the markdown — same content, structured for direct upload to your podcast platform's API. Bake / park / decline?
>
> **3.** Given Probe C (transcript chunker) and Probe F (push back on too-short transcripts), the skill could **detect non-content sections** (intros, ads, sign-offs) automatically and exclude them from chunking, rather than the user pre-cleaning. Bake / park / decline?
>
> **4.** Given Q1's voice-matching priority, the skill could **flag any sentence in the draft that drifts more than X% from your voice profile** (using simple lexical overlap or a small embedding score) so you can spot AI-slop before it ships. Bake / park / decline?

User picks:
1. **Park** — *"good but not v1; needs a stable voice profile first."*
2. **Park** — *"useful for v2 once I have a few episodes through it."*
3. **Bake into v1** — *"yes, this is what makes it ship-as-is."*
4. **Decline** — *"adds another quality bar I'd have to tune; the voice profile + my read should be enough for v1."*

---

**Step 6 — Confirm.**

*Architect displays compact summary and asks: "Anything to change before I write the spec?"*

User: *"Looks right."*

---

**Step 7 — Write.**

Architect writes `podcast-show-notes-spec.md`.
*See [`example-spec-output.md`](./example-spec-output.md) for the produced spec.*
