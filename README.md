https://justinsteinmetz.github.io/SELFvSELFIE/

# SELF v SELFIE

**An identity instrument for Grades 11–12.**

> The image is real. It is not complete.

The question isn't why you edit. The question is what repeated editing does to the person doing it.

---

## Concept

SELF v SELFIE examines the gap between lived identity and curated identity — not to prove that people are fake, but to investigate how repeated performance reshapes the person doing the performing.

The instrument is built on one core structural insight: both the Feed and the Draft are constructed. The Feed is edited for an audience. The Draft is edited for the self. Neither is more real than the other. The gap between them — what is systematically amplified, concealed, contradicted, and repeated — is where the data lives.

The genuinely unsettling question is not *"why do people curate?"* Most students already know the answer. The question is *"what happens when the edited version becomes the one you trust most?"*

---

## The engine

**The gap mechanic.** Students answer the same six prompts twice — once for The Feed (what they present) and once for The Draft (what doesn't make it). Both answers are required before moving to the next prompt. The gap between the two columns is submitted to the model as the primary evidence.

This is a new engine — distinct from the archive, the diagnostic, and the pressure chamber. Its governing action is **comparison**.

---

## The six prompts

| # | Label | What it forces |
|---|---|---|
| 1 | A specific moment | A real event shared or told — then what was cut |
| 2 | A performance | A specific instance of performing a version of themselves |
| 3 | What you care about | Publicly visible interests vs. private preoccupations |
| 4 | Something you deleted | A concrete thing withheld — and why |
| 5 | The audience | A specific person whose impression shapes the curation |
| 6 | The gap closing | Whether a performed version has started to feel real |

### On specificity

The prompts are built to enforce concrete, situational answers rather than abstract claims. Every prompt anchors to a specific instance: *"a moment from the last two weeks"*, *"a situation in the last month"*, *"something you wrote and deleted."* Sub-prompts reinforce this: *"An actual event. Not 'I usually...' — something specific."*

This is the instrument's most important structural decision. Generic Feed/Draft contrasts (*"I seem confident / I'm actually insecure"*) are real but predictable. The instrument only becomes powerful when the gap contains specific scenes, specific people, specific deleted things.

---

## The reading

After all six prompts, the model reads the gap record as parallel evidence.

**What the model reads for:**
- Patterns across all six prompts — what is *systematically* excluded or amplified, not just occasionally
- Whether the Feed and Draft are suspiciously similar (also data — worth naming)
- Whether answers operate at the level of abstract claim rather than concrete scene
- The student's answer to prompt 6 — whether a performed version has started to feel real — referenced directly

**The specificity flag.** If a student's answers are abstract — generic contrasts rather than specific scenes — the portrait names this directly rather than producing an elegant reading from thin material. *"Your answers operated at the level of claim rather than scene. Here is what that absence might mean."* A reading that names the thinness is more useful than one that papers over it.

**The Draft is not the real self.** The model is explicitly instructed not to treat the Draft as more authentic than the Feed. Both are constructions. The reading is about the structure of the gap, not which version is truer.

**Output:** headline (4–8 words, an observation about the structure of this specific gap), reading (200–270 words), signature (one sentence — the most specific thing the gap reveals about who this student is when there is no audience), three discussion questions derived from this gap record specifically.

---

## Design

The aesthetic lives between Instagram and TikTok — native to the visual world the instrument is examining, but slightly off. Not a parody. Something that looks like it belongs, until it doesn't.

**Palette** — near-white background, minimal. The Instagram/TikTok gradient (orange → pink → purple) used precisely once at full strength on the begin button; elsewhere only as accents on labels and dots.

**Typography** — Plus Jakarta Sans throughout the instrument (contemporary, geometric, platform-adjacent). The result screen shifts entirely to DM Serif Display — the register change is the signal that something different is happening.

**The split** — Feed panel has a subtle card shadow (production value); Draft panel is flat. The gap divider is labelled GAP in faint rotated mono text.

**Result screen** — aged paper background, warm sepia palette, documentary register. Ephemeral self-presentation becomes archival evidence.

**Mobile** — stacks to single column. The GAP divider rotates horizontal.

---

## The critical framing

Two sentences do the most important work in the instrument — both appear on the intro screen before students begin:

*"The question isn't why you edit. The question is what repeated editing does to the person doing it."*

*"The Draft is not the real you. Both versions are constructed. The gap between them is what's interesting."*

Without these, the instrument risks confirming what students already believe: that social media is selective and people hide their feelings. With them, the instrument reframes its own premise before the first prompt loads.

---

## Pedagogical notes

**The main risk is generic data.** Students who understand the mechanic quickly may begin supplying expected contrasts. The concrete prompt design is the primary defence. The specificity flag in the AI prompt is the secondary defence.

**Prompt 6 is the philosophical centre.** The question of whether a performed version has started to feel real is the most unsettling in the instrument. If classroom discussion time is limited, start there.

**The result is private by default.** Students choose what, if anything, leaves the room.

**Discussion entry points** (generic — the instrument generates three specific ones per student):
- "Which prompt was hardest to fill in the Draft column? Why that one?"
- "Were your two columns more similar or more different than you expected?"
- "If the Feed version kept appearing in your life, would you eventually start to believe it? Is that already happening?"
- "The reading named something about the structure of your gap. Is it accurate — and if it's wrong, why might it be wrong in that specific way?"

---

## Abitur Themenfeld relevance

| Themenfeld | Angle |
|---|---|
| The Individual & Society | Identity and performance, authenticity, self-presentation, the construction of the social self |
| Science & Technology | Social media and identity formation; algorithmic visibility; the psychological effects of constant curation |

---

## Technical architecture

Uses the same Cloudflare Worker proxy as the rest of the suite.

```javascript
const PROXY = "https://anthropic-proxy.justin-steinmetz.workers.dev";
```

One API call per session — the gap reading at the end. See the *Who Are You, Really* README for full Worker deployment instructions.

### Deployment

Single HTML file. No dependencies, no build step. Rename `self-v-selfie.html` to `index.html` and push to a GitHub Pages repository.
