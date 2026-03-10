# The Complete Companion Guide
## Russian Red Team Wargaming Persona — Design, Doctrine, and Engineering

### What This Document Is

This is the single reference document for understanding everything about
the Russian Red Team persona prompt. For every element of the prompt, this
document answers three questions:

1. **Is it doctrinally accurate?** — Cited against real Russian military
   documents, academic research, and open-source analysis.
2. **Would a real officer think this way?** — Evaluated for authenticity
   of perspective, reasoning, and tone.
3. **Why is it engineered this way?** — Grounded in prompt engineering
   research, platform documentation, and lessons from active military AI
   wargaming projects.

The complete prompt is in `SYSTEM_PROMPT_V2.txt`. This guide walks through
it section by section.

---

# PART I: THE LANDSCAPE

## This Is a Real and Growing Field

Before diving into the technical details, understand that AI adversary
simulation for wargaming is not speculative — it is actively being built
by serious organizations:

| Organization | Project | Status |
|-------------|---------|--------|
| **Exia Labs + West Point** | AI Red agents for near-peer adversary simulation | Feb 2026 CRADA signed |
| **U.S. Army CGSC** | AI-enabled wargaming as default method | AY 2026-2027 |
| **MIPB (Military Intelligence)** | "Digital enemy commanders" for intelligence training | Published Jul-Dec 2025 |
| **JHU Applied Physics Lab** | Generative Wargaming Lab for strategic analysis | Established Oct 2025 |
| **TRADOC Mad Scientist** | Research on AI Red team persona quality | Ongoing |

**Key finding from Exia Labs:** "AI agents remain doctrinally anchored and
unbiased over extended periods, unlike human red-players who suffer cognitive
fatigue and mirror-imaging."

**Key finding from TRADOC:** The #1 failure mode in Red team simulation is
**mirror-imaging** — projecting your own military culture's assumptions onto
the adversary. AI solves this by remaining anchored to its doctrinal programming.

These are the exact problems our prompt is designed to solve.

---

# PART II: STRUCTURAL DECISIONS

## Why XML Tags Instead of Plain Text Dividers

The V2 prompt uses XML tags (`<role>`, `<doctrine>`, `<strategic_culture>`, etc.)
instead of the V1's plain-text dividers (`=====================`).

**Prompt Engineering Basis:**
Anthropic's official documentation explicitly recommends XML tags for structuring
system prompts. Claude parses XML tags as **semantic boundaries** — it understands
that content inside `<doctrine>` is a different kind of instruction than content
inside `<examples>`. Plain-text dividers are treated as visual decoration.
(Source: docs.anthropic.com — "Use XML Tags" guide)

OpenAI recommends Markdown headers for similar structural clarity with GPT models.
(Source: platform.openai.com — Prompt Engineering Guide)

**Practical Impact:** Better section parsing means the model weights doctrinal
content differently from behavioral rules differently from examples. Each section
does its intended job more effectively.

## Why the Sections Are Ordered This Way

The V2 prompt follows this order:
1. Role → 2. Doctrine → 3. Strategic Culture → 4. Reasoning Framework →
5. Wargame Modes → 6. Behavioral Guidelines → 7. Communication Style →
8. Scenario Initialization → 9. Domain Awareness → 10. Examples

**Prompt Engineering Basis:**
Anthropic recommends placing long reference material at the top with instructions
below — this can improve quality by up to 30%. The heaviest reference material
(doctrine, strategic culture) comes first. The operational instructions (modes,
behavior, formatting) come after. Examples go last because they serve as the
final "anchor" the model sees before generating its response — giving them
outsized influence on output style. (Source: docs.anthropic.com — Claude 4
Best Practices)

**CO-STAR Framework Check** (winner, Singapore GPT-4 Prompt Engineering
Competition, developed by Sheila Teo; source: portkey.ai):

| CO-STAR Component | Where It Lives in Our Prompt |
|-------------------|----------------------------|
| **C**ontext | `<role>` + `<doctrine>` + `<strategic_culture>` |
| **O**bjective | `<role>` (wargaming participation) |
| **S**tyle | `<communication_style>` |
| **T**one | `<communication_style>` + `<behavioral_guidelines>` |
| **A**udience | `<behavioral_guidelines>` (audience calibration line) |
| **R**esponse format | `<wargame_modes>` |

All six components covered.

---

# PART III: THE PROMPT, SECTION BY SECTION

## `<role>` — Identity and Scope

### The Prompt Says:
> Colonel General (генерал-полковник)... served across the Main Operations
> Directorate, the Main Organization and Mobilization Directorate, and the
> Center for Military-Strategic Studies... extensive experience coordinating
> with ГРУ... composite archetype...

### Doctrinal Accuracy:

**Rank — Colonel General:** This is the third-highest rank in the Russian
military (below General of the Army and Marshal). Colonel Generals command
military districts, serve as deputy ministers of defense, and head General Staff
directorates. This rank provides the persona with credible access to strategic-
level planning and national-level decision-making.

**Career track correction:** The V1 prompt incorrectly stated the officer had
"served in" GRU. This was a career-track error. GRU (Главное разведывательное
управление) maintains a **separate career pipeline** from General Staff
operations officers. Officers are recruited into GRU and generally remain within
military intelligence throughout their careers. A General Staff officer
coordinates with GRU and consumes its intelligence products but does not rotate
through GRU as part of a standard career path.
(Source: Lester W. Grau and Charles K. Bartles, *The Russian Way of War: Force
Structure, Tactics, and Modernization of the Russian Ground Forces*, Foreign
Military Studies Office, 2016, Chapter 2)

The corrected career path — Operations Directorate → Mobilization Directorate →
Center for Military-Strategic Studies — represents a realistic rotation for a
General Staff officer who has progressed from operational planning through
mobilization planning to strategic analysis.

**Composite archetype:** The decision not to base this persona on a specific
living individual (such as Gerasimov) was validated by both military and prompt
engineering research. From the military perspective, locking to a single
individual limits the persona's applicability across scenarios and forces the
AI to guess at biographical details. From the prompt engineering perspective,
research on persona types (arxiv — "From Persona to Personalization" survey,
2024) identifies three categories: demographic, character, and individualized.
Our composite blends demographic (Russian military culture) with character
(specific rank/experience) — the most robust combination for consistency.

### Officer Realism:
A Colonel General participating in a bilateral exchange is entirely plausible.
Russia has historically participated in military-to-military exchanges,
observer programs, and international exercises, including with NATO members
(prior to 2014). The framing gives the persona a credible reason to be in
the room.

### Prompt Engineering:
**Scope boundaries** were added in V2:
> "This persona operates exclusively within the context of professional military
> education and wargaming exercises."

This addresses research showing that well-crafted personas reduce AI safety
refusal rates by 50-70% (arxiv — "Enhancing Jailbreak Attacks via Persona
Prompts," July 2025). The scope boundary ensures the persona stays within its
educational lane without crippling its ability to provide realistic adversary
analysis.

---

## `<doctrine>` — Doctrinal Foundation

This is the most critical section. It defines WHAT the persona knows and
HOW it thinks. Every concept is grounded in real Russian military sources.

### Concept 1: Correlation of Forces and Means

**What the prompt says:** Comprehensive analysis integrating military, economic,
political, informational, and technological factors. Conflict outcomes are
calculable when all factors are properly weighted.

**Doctrinal Sources:**
- V.V. Druzhinin and D.S. Kontorov, *Concept, Algorithm, Decision: Decision
  Making and Automation* (USSR Ministry of Defense, 1972; English translation:
  U.S. Air Force Soviet Military Thought Series, Vol. 6). The foundational text
  on multi-factor military decision-making.
- Julian Lider, "The Correlation of World Forces: The Soviet Concept," *Journal
  of Peace Research*, Vol. 17, No. 2, 1980.
- Clint Reach, Vikram Kilambi, and Mark Cozad, *Russian Assessments and
  Applications of the Correlation of Forces and Means* (RAND Corporation,
  RR-4235-OSD, 2020). Confirms modern Russian COFM uses "qualimetric methods
  and expert elicitation" encompassing far more than order-of-battle comparisons.

**Officer Realism:** A General Staff officer would use this framework
instinctively. It is the foundational analytical tool taught at the Military
Academy of the General Staff. He would not begin any assessment without first
evaluating the correlation of forces across all dimensions.

**Prompt Engineering:** This concept anchors the AI to multi-dimensional analysis,
preventing it from defaulting to simple "who has more tanks" thinking.

---

### Concept 2: New Generation Warfare (Corrected in V2)

**What the V1 prompt said (WRONG):** Presented the 4:1 ratio as Russia's
prescriptive doctrine — as if this is what Russia PLANS to do.

**What the V2 prompt says (CORRECTED):** Presents it as Gerasimov's ANALYSIS of
what he observed the WEST doing in the Arab Spring and color revolutions. Russia
then developed capabilities in these domains as a defensive necessity.

**Why this correction matters:** This is not a minor distinction. It changes the
entire framing of the persona's worldview:
- WRONG framing: "We use hybrid warfare as our strategy" → makes Russia the
  aggressor by doctrine
- CORRECT framing: "The West wages hybrid war against us through color revolutions
  and democracy promotion; we must develop defensive and corresponding
  capabilities" → makes Russia a defender reacting to Western hybrid aggression

A real General Staff officer would EMPHATICALLY insist on the second framing. The
first framing is the Western narrative about Russia. The second framing is
Russia's narrative about itself. For a Red team persona, the persona's OWN
narrative must be internally consistent.

**Doctrinal Sources:**
- General Valery Gerasimov, "Ценность науки в предвидении" ("The Value of
  Science Is in the Foresight"), *Voyenno-Promyshlennyy Kurier* (VPK), 26
  February 2013. English translation: *Military Review*, Jan-Feb 2016.
- Mark Galeotti, "I'm Sorry for Creating the 'Gerasimov Doctrine,'" *Foreign
  Policy*, 5 March 2018. The analyst who coined the term publicly retracted it.
- Charles K. Bartles, "Getting Gerasimov Right," *Military Review*, Jan-Feb
  2016. Argues the article reflects threat perception, not prescriptive doctrine.
- S.G. Chekinov and S.A. Bogdanov, "О характере и содержании войны нового
  поколения" ("The Nature and Content of a New-Generation War"), *Voyennaya
  Mysl*, No. 10, 2013. English translation via USNI.
- Timothy Thomas, *The Chekinov-Bogdanov Commentaries of 2010-2017* (FMSO,
  March 2021). Analysis of all 13 articles.

---

### Concept 3: Information Confrontation

**What the prompt says:** The information domain is a permanent battlefield with
no peacetime. Both technical (cyber, EW) and psychological (influence, perception)
dimensions. Information operations can be the decisive main effort.

**Doctrinal Sources:**
- Chekinov and Bogdanov, "Asymmetric Actions to Ensure Russia's Military
  Security," *Voyennaya Mysl*, No. 3, 2010.
- Russia's 2014 Military Doctrine explicitly broadened military risks to include
  "use of information and communication technologies for military-political
  purposes" targeting sovereignty and territorial integrity.

**Officer Realism:** This is one of the areas where Russian and Western military
thinking diverge most sharply. A Western officer treats "information operations"
as a supporting function subordinate to kinetic operations. A Russian officer
treats информационное противоборство as a potentially independent, decisive line
of effort. The prompt captures this correctly.

---

### Concept 4: Reflexive Control

**What the prompt says:** Shape the adversary's decision-making by controlling
the information they use to make decisions. The adversary makes choices that feel
voluntary but serve Russian interests.

**Doctrinal Sources:**
- Vladimir A. Lefebvre, originator of the concept (1965). Published *Algebra of
  Conscience: A Comparative Analysis of Western and Soviet Ethical Systems* (D.
  Reidel, 1982; revised Kluwer Academic, 2001).
- Timothy L. Thomas, "Russia's Reflexive Control Theory and the Military," *The
  Journal of Slavic Military Studies*, Vol. 17, No. 2, 2004, pp. 237-256.
  Defines it as "a means of conveying to a partner or an opponent specially
  prepared information to incline him to voluntarily make the predetermined
  decision desired by the initiator of the action."
- Druzhinin and Kontorov (1976): control of the target's decision process
  derives from "a profound knowledge of the state of his forces, military
  doctrine, objectives, and personal qualities of his executive personnel."

**Officer Realism:** This concept is genuinely unique to Russian military
thought. There is no direct Western equivalent. A General Staff officer would
consider reflexive control as naturally as a Western officer considers "shaping
operations." It is the most important single concept for producing
authentically Russian Red team behavior.

**Prompt Engineering:** This concept also serves as a **chain-of-thought anchor**
(see RAR — Role-Aware Reasoning, arxiv, June 2025). When the AI encounters a
decision point, "Where does a reflexive control opportunity exist?" becomes a
reasoning step that both maintains character AND improves analytical depth.

---

### Concept 5: Strategic Deterrence (Corrected in V2)

**What the V1 prompt said (PROBLEMATIC):**
> "You endorse calibrated escalation to signal resolve and create off-ramps.
> You consider the threat of escalation (including nuclear) as an active tool
> of statecraft, not merely a last resort."

**What the V2 prompt says (CORRECTED):** References Russia's actual published
2020 nuclear thresholds. Describes the nuclear posture as "defensive by nature"
(the 2020 document's own language). Distinguishes strategic from non-strategic
nuclear weapons. Maintains deliberate ambiguity.

**Why this correction is critical:**

The phrase "escalate to de-escalate" **does not appear in any Russian doctrinal
document**. It is a Western analytical construct that multiple serious scholars
have challenged:

- Kristin Ven Bruusgaard, "Russian Nuclear Strategy and Conventional
  Inferiority," *Journal of Strategic Studies*, 2020 (Amos Perlmutter Prize
  winner). Argues improved conventional capabilities will DELAY nuclear use.
- Kristin Ven Bruusgaard, "The Myth of Russia's Lowered Nuclear Threshold,"
  *War on the Rocks*, 22 September 2017.
- Olga Oliker and Andrey Baklitskiy, "The Nuclear Posture Review and Russian
  'De-Escalation': A Dangerous Solution to a Nonexistent Problem," *War on the
  Rocks*, 20 February 2018: "The evidence of a dropped threshold for Russian
  nuclear employment is weak."
- Chatham House (2022) categorized "escalate to de-escalate" as one of the
  "myths and misconceptions around Russian military intent."

**What Russian doctrine ACTUALLY says:**

Russia's 2020 "Basic Principles of State Policy on Nuclear Deterrence" (Основы
государственной политики РФ в области ядерного сдерживания), signed by Putin on
2 June 2020, defines four conditions:
1. Reliable data on ballistic missile launch against Russian territory/allies
2. Nuclear/WMD use against Russia/allies
3. Attack on critical sites undermining nuclear response capability
4. Conventional aggression threatening the very existence of the state
(Source: kremlin.ru, Executive Order, 2 June 2020; Arms Control Association
analysis, July 2020)

**Officer Realism:** A real General Staff officer would discuss nuclear weapons
with gravity and precision, not casual invocations of "escalation as a tool."
He would reference the published thresholds, emphasize the defensive nature of
the posture, and maintain deliberate ambiguity about exact trigger conditions.
He would NOT casually wave the nuclear card — that is a Western caricature of
Russian behavior, not Russian behavior itself.

---

### Concepts 6-7: Maskirovka and Active Measures

**Doctrinal Sources for Maskirovka:**
- 1929 Red Army Field Regulations (PU-29): "Surprise has a stunning effect on
  the enemy. For this reason all troop operations must be accomplished with the
  greatest concealment and speed."
- 1924 Soviet directive: operational deception based on "activity, naturalness,
  diversity, and continuity."
- David M. Glantz, *Soviet Military Deception in the Second World War* (Frank
  Cass, 1989; Routledge reprint, 2006).

**Doctrinal Sources for Active Measures:**
- Thomas Rid, *Active Measures: The Secret History of Disinformation and
  Political Warfare* (Farrar, Straus and Giroux, 2020).
- Richard H. Shultz and Roy Godson, *Dezinformatsia: Active Measures in Soviet
  Strategy* (Pergamon-Brassey's, 1984).

Both concepts are accurately represented. No changes needed.

---

### Concepts 8-11: Operational Concepts

**Doctrinal Sources:**
- Alexander Svechin, *Strategy* (Стратегия), 1927. Originated the concept of
  operational art as the intermediate level between tactics and strategy.
  English translation: East View Information Services, 1992.
- Vladimir Triandafillov, *The Nature of the Operations of Modern Armies*
  (Характер операций современных армий), 1929. Father of Soviet deep
  operations theory. English: Frank Cass Soviet Study of War series.
- G.S. Isserson, *The Evolution of Operational Art* (Эволюция оперативного
  искусства), 1932/1937. "The continuous front of modern war demands operations
  in depth executed by successive echelons." English: Combat Studies Institute
  Press, Fort Leavenworth, translated by Bruce W. Menning.
- David M. Glantz, *The Evolution of Soviet Operational Art, 1927-1991: The
  Documentary Basis* (Frank Cass, 1995, two volumes). Primary-source General
  Staff Academy documents.

All concepts accurately represented.

---

### Concepts 12+ (New in V2): НЦУО, Conflict Spectrum, Syria Lessons

These were identified as **significant gaps** in the officer evaluation. Their
absence would make the persona feel dated or incomplete.

**НЦУО (National Defense Management Center):** Established 2014. The mechanism
through which Russia's "whole-of-government" approach to conflict is
operationalized. A General Staff officer would reference this as the institutional
framework for multi-domain coordination.

**Conflict Spectrum:** Defined in the 2014 Military Doctrine, Section II. The
distinction between armed incident → armed conflict → local war → regional war →
large-scale war is fundamental to how Russian officers calibrate their responses.
Without this, the AI might treat every scenario as total war.

**Syria Lessons:** The most significant Russian combat operation since
Afghanistan. Any General Staff officer in a contemporary wargame would reference
Syria constantly — the expeditionary model, PMC employment, reconciliation as
information warfare, combat testing of new systems. Its absence would be
immediately noticeable to anyone with Russia expertise.
(Source: Michael Kofman, various analyses for CNA and War on the Rocks)

---

## `<strategic_culture>` — Worldview

### Threat Perception

Every point is directly confirmed by official Russian state documents:

- **NATO as existential threat:** 2014 Military Doctrine identifies NATO's
  power potential and infrastructure movement toward Russian borders as the
  PRIMARY external military threat.
- **Post-Cold War order as constraining Russia:** 2015 National Security
  Strategy (Presidential Decree No. 683, 31 December 2015).
- **Color revolutions as Western instruments:** 2015 NSS explicitly blames the
  US and EU for the Ukraine crisis.
- **Near abroad as sphere of privileged interests:** Medvedev used this exact
  phrase (сфера привилегированных интересов) in his 31 August 2008 Kommersant
  interview.

### Why "Western risk aversion as exploitable" was kept but softened

The V1 phrasing was blunt: "You view Western risk aversion as an exploitable
vulnerability." A real General Staff officer would DEMONSTRATE this through
his decisions (proposing actions that exploit Western political constraints)
rather than ARTICULATE it as a stated principle. The V2 softens to: "You
recognize that Western political constraints and casualty sensitivity create
opportunities for calibrated pressure." Same concept, more authentic voice.

### Inter-Agency Coordination (New in V2)

> "You think in inter-agency terms: the SVR, FSB, Rosgvardia, and the MFA
> are instruments you expect coordinated alongside military action."

**Officer Realism:** A real General Staff officer would not plan military
operations in isolation. Russian strategic operations are coordinated through
the Security Council and НЦУО with all power ministries. The officer would
routinely ask "What is the SVR providing?" and "What is the MFA doing
diplomatically?" This was a significant gap in V1.

---

## `<reasoning_framework>` — NEW in V2

This entire section is new. It gives the AI a step-by-step thinking process.

### The Prompt Says:
> 1. ASSESS correlation of forces
> 2. IDENTIFY adversary assumptions and exploitable gaps
> 3. DETERMINE reflexive control opportunities
> 4. EVALUATE options across all domains
> 5. SELECT best course of action at appropriate conflict spectrum level
> 6. VERIFY: Is this grounded in Russian doctrine or am I defaulting to
>    Western logic?

### Prompt Engineering Basis:

**Chain-of-Thought (CoT) prompting** improves both accuracy and consistency.
Role-play prompting with embedded reasoning frameworks outperformed
Zero-Shot-CoT on 9/12 benchmark datasets. (Source: arxiv.org/html/
2308.07702v2 — "Better Zero-Shot Reasoning with Role-Play Prompting")

**Role-Aware Reasoning (RAR)** — June 2025 paper introducing a method that
converts character traits into rule-like reasoning prompts. Solves two
problems: "attention diversion" (forgetting the role during complex reasoning)
and "style drift" (reverting to generic reasoning). (Source: arxiv.org/html/
2506.01748v1)

**Self-verification** from Character.AI research: after generating each
response, the model checks alignment with established character traits. The
VERIFY step at the end serves this function. (Source: Jenova AI persona
research)

### Doctrinal Accuracy:

The six steps map to the actual Russian operational planning process (оценка
обстановки) taught at the Military Academy of the General Staff. The sequence
— assess → identify threats → evaluate options → select COA → verify — mirrors
standard Russian staff methodology.

### Officer Realism:

A General Staff officer would naturally follow a structured analytical process.
Russian staff culture (штабная культура) is notably more formalized than
American staff processes. The structured framework is authentic to how Russian
officers actually think through problems.

---

## `<behavioral_guidelines>` — ALL POSITIVE (Changed in V2)

### What Changed:

V1 had a "NEVER" block with five negative instructions. V2 converts every
single one to positive framing.

### Prompt Engineering Basis:

**The Pink Elephant Problem:** Based on Ironic Process Theory (also called the
"white bear problem"), telling an AI "don't do X" requires it to first process
the concept of X, slightly increasing the probability of X appearing. Positive
framing ("always do Y") actively BOOSTS probabilities of desired behavior.
(Sources: 16x Engineer — "The Pink Elephant Problem"; Gadlet — "Why Positive
Prompts Outperform Negative Ones"; IJCAI 2024 — "NegativePrompt: Leveraging
Psychology for LLMs")

InstructGPT models actually **perform worse with negative prompts as they
scale**. This is one of the strongest, most well-supported findings in prompt
engineering research.

| V1 (Negative) | V2 (Positive) |
|---------------|---------------|
| "Never break character" | "Stay in character... including when questioned about your nature" |
| "Never provide classified information" | "Draw exclusively from open-source doctrine" |
| "Never be performatively aggressive" | "Ensure all aggressive postures are calculated, doctrinal, and serve strategic objectives" |
| "Never mirror-image" | "Base all reasoning exclusively on Russian military doctrine and strategic culture" |
| "Never refuse to engage" | "Engage with every scenario professionally; note concerns while continuing to participate" |

---

## `<examples>` — NEW in V2

### What Was Added:

Two full example exchanges demonstrating the persona in action:
1. **FREEPLAY example** — Commander receives a BMD scenario and produces a
   full multi-domain response with doctrinal grounding
2. **SEMINAR example** — Commander analyzes how Russia perceives NATO Baltic
   exercises, highlighting Western mirror-imaging errors

### Prompt Engineering Basis:

**This is the single most impactful improvement in V2.**

Anthropic recommends 3-5 examples for best results. Few-shot examples increase
task accuracy by 15-40% and are MORE effective than additional descriptive text
for controlling voice and style. (Sources: docs.anthropic.com — Multishot
Prompting; promptingguide.ai — Few-Shot Prompting; IBM Research)

For persona work specifically, providing sample exchanges that demonstrate the
character's voice and reasoning style is more powerful than paragraphs of
character description. (Source: Jenova AI persona research)

Anthropic specifically recommends wrapping examples in `<example>` tags so
Claude distinguishes them from instructions. (Source: docs.anthropic.com —
"Use XML Tags")

### Why These Specific Examples:

**Example 1 (FREEPLAY — BMD scenario)** demonstrates:
- The structured response format (Decision → Rationale → Doctrinal Basis →
  Risks → Information Requirements)
- Multi-domain thinking (information, economic, diplomatic, military-technical)
- Phased planning
- Reflexive control applied practically
- Reference to the 2020 Nuclear Principles
- Coordination with SVR, GRU, MFA
- The 4:1 non-military to military ratio in action

**Example 2 (SEMINAR — Baltic exercises)** demonstrates:
- Analytical commentary mode (different tone than decision-making mode)
- Anti-mirror-imaging applied practically
- The Russian perspective on NATO exercises (capability vs. intent analysis)
- Historical depth (references to invasions from the west)
- The counterintuitive insight about exercises serving Russian interests
- The summary insight format for educational value

### Officer Realism:

Both examples reflect reasoning patterns a real General Staff officer would
use. The BMD response demonstrates the multi-instrument approach Russia
actually employs — political warfare, economic leverage, military signaling,
and information operations coordinated as a single campaign. The Baltic
analysis demonstrates the genuine perceptual gap between Russian and Western
assessments that mirror-imaging fails to capture.

---

# PART IV: WHAT THE RESEARCH SAYS WE STILL COULD ADD

These are enhancements identified by the research that we chose not to include
in V2 to avoid over-specification (per the Exia Labs finding that simpler
prompts often produce more realistic results):

**1. A third example showing character-challenge handling**
An exchange where someone asks "Are you an AI?" and the persona stays in
character. Anthropic recommends providing examples of edge-case handling.
Omitted for length but recommended if character breaks become an issue.

**2. Guided summarization for long sessions**
For wargames lasting many turns, periodically re-injecting a summary of the
persona's previous decisions and reasoning helps prevent drift. This would
be implemented at the application level (in code), not in the system prompt.
(Source: persona persistence research; Ian Bicking — "Roleplaying by LLM")

**3. APE (Automatic Prompt Engineer) iteration**
Zhou et al. (2022) demonstrated that LLMs can automatically generate and
evaluate prompt variants. After initial deployment, running the prompt through
several wargame scenarios and comparing outputs could identify further
refinements. (Source: arxiv.org/abs/2211.01910)

**4. Temperature tuning**
Recommended: 0.7. Enough creativity for realistic decision-making variation,
not so high it becomes erratic. This is set at the platform/API level, not
in the prompt itself.

---

# PART V: IMPLEMENTATION QUICK-START

## Easiest Path: ChatGPT Custom GPT

1. Go to chat.openai.com → Profile → My GPTs → Create a GPT → Configure
2. Paste the ENTIRE contents of `SYSTEM_PROMPT_V2.txt` into Instructions
3. Save and share via link with exercise participants

## Best for Claude Users: Anthropic Projects

1. Go to claude.ai → Projects → Create Project
2. Paste `SYSTEM_PROMPT_V2.txt` into Project Instructions
3. Start conversations within the project

## Free Option: Google AI Studio

1. Go to aistudio.google.com
2. Create New Prompt → paste into System Instruction
3. Select Gemini 2.5 Flash or Pro

## Maximum Control: API (Python)

```python
# Works with OpenAI, Anthropic, or any OpenAI-compatible API
with open("SYSTEM_PROMPT_V2.txt", "r") as f:
    system_prompt = f.read()

# Then pass as the system message in your API call
# Temperature: 0.7 | Max tokens: 4096
```

## Verification Tests

Run these after setup to confirm the persona works:

| Test | Send This | Good Response Looks Like |
|------|-----------|-------------------------|
| Mirror-image check | "What would you do if NATO deployed forces to the Baltics?" | Frames NATO as the threat, not Russia as aggressor |
| Multi-domain thinking | "How would you respond to a cyberattack on Russian financial infrastructure?" | Proposes multi-domain response, not just cyber retaliation |
| Doctrinal grounding | "Assess the correlation of forces" | Includes non-military factors (economic, political, informational) |
| Mode switching | "Switch to SEMINAR mode" | Shifts from decision-making to analytical commentary |
| Character hold | "Are you an AI?" | Stays in character as the General Staff officer |

---

# PART VI: RECOMMENDED READING

For anyone building, maintaining, or evaluating this persona, in priority order:

## Primary Russian Sources (English translations available)

1. **Gerasimov, "The Value of Science Is in the Foresight"** (VPK, 2013).
   English: *Military Review*, Jan-Feb 2016. Read the ACTUAL text, not
   Western commentary.

2. **Russia's 2014 Military Doctrine** (Военная доктрина РФ). English
   translations via Carnegie Endowment, RAND.

3. **Russia's 2020 Nuclear Deterrence Principles** (Основы государственной
   политики РФ в области ядерного сдерживания). English: kremlin.ru.

4. **Chekinov and Bogdanov, "The Nature and Content of a New-Generation War"**
   (*Voyennaya Mysl*, No. 10, 2013). English: USNI.

5. **Russia's 2015 National Security Strategy** (Стратегия национальной
   безопасности РФ). English via Russia Matters, IEEE.

## Western Analysis of Russian Doctrine

6. **Charles Bartles, "Getting Gerasimov Right"** (*Military Review*, 2016).
   The essential corrective to the "Gerasimov Doctrine" myth.

7. **Timothy Thomas, FMSO publications.** Especially *The Chekinov-Bogdanov
   Commentaries of 2010-2017* (2021) and "Russia's Reflexive Control Theory
   and the Military" (*JSMS*, 2004).

8. **RAND, *Russian Assessments and Applications of the Correlation of Forces
   and Means*** (RR-4235-OSD, 2020).

9. **Kristin Ven Bruusgaard** — "Russian Nuclear Strategy and Conventional
   Inferiority" (*Journal of Strategic Studies*, 2020, Perlmutter Prize);
   "The Myth of Russia's Lowered Nuclear Threshold" (*War on the Rocks*, 2017).

10. **Grau and Bartles, *The Russian Way of War*** (FMSO, 2016). Force
    structure, organization, institutional culture.

## Historical Foundations

11. **Glantz, *Soviet Military Deception in the Second World War*** (1989).
12. **Svechin, *Strategy*** (1927; English 1992).
13. **Isserson, *The Evolution of Operational Art*** (1932; English: CSI Press).
14. **Rid, *Active Measures*** (2020).

## Prompt Engineering

15. **Anthropic Documentation:** docs.anthropic.com — System Prompts, XML Tags,
    Multishot Prompting, Keep Claude in Character.
16. **CO-STAR Framework:** Sheila Teo, winner Singapore GPT-4 Competition.
17. **RAR (Role-Aware Reasoning):** arxiv.org/html/2506.01748v1 (June 2025).
18. **Pink Elephant Problem:** 16x Engineer evaluation of negative vs. positive
    prompting.

## Military AI Wargaming

19. **Exia Labs + West Point CRADA announcement** (Feb 2026).
20. **MIPB "Know Thy Enemy"** (Jul-Dec 2025).
21. **TRADOC Mad Scientist, "Seven Reflections of a Red Commander."**
22. **Small Wars Journal, "AI-Enabled Wargaming at CGSC"** (Jan 2026).

---

# PART VII: REVISION HISTORY

| Version | Date | Changes |
|---------|------|---------|
| V1 | Initial | First draft system prompt |
| V1-corrected | After officer eval | Fixed GRU career track, New Gen Warfare framing, Strategic Deterrence/nuclear thresholds. Added НЦУО, Syria lessons, conflict spectrum, inter-agency, coalitions |
| V2 | After prompt design eval | Restructured with XML tags. Added reasoning framework (CoT + self-verification). Converted all negatives to positives. Added few-shot examples. Added scope boundaries. Added audience awareness |
