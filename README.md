# Colonel General

**An interactive AI wargaming persona and prompt engineering course — built on real Russian military doctrine.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![GitHub Pages](https://img.shields.io/badge/demo-GitHub%20Pages-brightgreen)](https://jeranaias.github.io/colonel-general)

---

## What This Is

Colonel General is two things at once:

1. **A working AI wargaming tool.** A Colonel General of the Russian General Staff participates in wargaming exercises — analyzing scenarios, making decisions, and providing adversary perspective grounded in real Russian military doctrine.

2. **An interactive prompt engineering course.** Every design decision in the system prompt is documented with three-perspective analysis: doctrinal accuracy, officer realism, and prompt engineering rationale. Users can toggle prompt sections on and off, edit the prompt live, and study how each change affects AI behavior.

Chat with the persona. Then open the prompt viewer to see exactly how it works — and why.

---

## Who It's For

- **Military educators and wargaming facilitators** who need a doctrinally accurate Red Team adversary
- **Prompt engineers** studying advanced persona design, XML structuring, few-shot examples, and drift prevention
- **Students of Russian military doctrine** who want to explore strategic culture through interactive simulation
- **Anyone interested in AI system prompt engineering** who wants a real-world case study with full documentation

---

## Quick Start

1. Visit [jeranaias.github.io/colonel-general](https://jeranaias.github.io/colonel-general)
2. Pick a provider (Anthropic, Google Gemini, or OpenRouter)
3. Enter an API key
4. Start chatting

No installation. No build step. No backend. Everything runs in your browser.

---

## Getting an API Key

| Provider | Where to Get a Key | Cost | Best For |
|----------|-------------------|------|----------|
| **Google Gemini** | [aistudio.google.com](https://aistudio.google.com) | FREE tier available | Great starting point — no credit card needed |
| **Anthropic** | [console.anthropic.com](https://console.anthropic.com) | Requires paid account | Best persona consistency (Claude was designed for this) |
| **OpenRouter** | [openrouter.ai](https://openrouter.ai) | Some free models available | Access to ALL models — GPT-4.1, DeepSeek, Llama, and more |

Your API key stays in your browser's local storage. It is never transmitted anywhere except directly to the provider you selected.

---

## Features

- **Live chat** with the Colonel General persona in four wargame modes (Freeplay, Scripted, Seminar, Individual Move)
- **Interactive prompt viewer** with section-by-section toggle switches — disable a section and watch how the AI's behavior changes
- **Edit Mode** — modify the system prompt live and see how your changes affect AI responses in real time
- **Three-perspective educational guide** — every prompt section annotated for Doctrinal Accuracy, Officer Realism, and Prompt Engineering rationale
- **Full bibliography** of Russian military doctrine and prompt engineering research
- **Multi-provider support** — Anthropic Claude, Google Gemini, and OpenRouter (hundreds of models)
- **Zero installation** — single HTML file, runs in any modern browser
- **Privacy by design** — API keys never leave your browser; no backend, no telemetry, no accounts

---

## The Persona

The Colonel General is a composite archetype representing the institutional thinking of the Russian General Staff. He holds the rank of Colonel General (the third-highest rank in the Russian military), has served across the Main Operations Directorate, the Main Organization and Mobilization Directorate, and the Center for Military-Strategic Studies, and has extensive experience coordinating with GRU intelligence products.

He is not a specific living person. He is the collective professional military judgment of the General Staff, verified against:

- **Russia's 2014 Military Doctrine** — threat perceptions, conflict spectrum, force employment
- **2020 Basic Principles of State Policy on Nuclear Deterrence** — the four actual published nuclear thresholds
- **Gerasimov's 2013 analysis** in VPK — what he actually wrote vs. the Western "Gerasimov Doctrine" myth
- **Chekinov and Bogdanov** in *Voyennaya Mysl* — new-generation warfare as threat perception, not prescriptive doctrine
- **Timothy Thomas (FMSO)** — reflexive control theory, Chekinov-Bogdanov commentaries
- **RAND Corporation** — Correlation of Forces and Means methodology (RR-4235-OSD, 2020)

---

## Educational Methodology

Every element of the system prompt is analyzed from three perspectives:

### Doctrinal Accuracy
Every concept is cited against real Russian military documents, journal articles, and open-source analysis. When Western misconceptions exist (such as "escalate to de-escalate"), the guide explains what Russian doctrine actually says and provides the primary sources.

### Officer Realism
Each section is evaluated by asking: "Would a real Colonel General think this way?" Career track accuracy, institutional vocabulary, decision-making patterns, and inter-agency awareness are all verified against how the Russian General Staff actually operates.

### Prompt Engineering
Every structural and linguistic choice is grounded in published research — Anthropic's official documentation, the CO-STAR framework, RAR (Role-Aware Reasoning), the Pink Elephant Problem, and findings from active military AI wargaming projects at West Point, CGSC, and JHU APL.

---

## Prompt Engineering Techniques Used

The system prompt demonstrates these techniques, each documented in the companion guide:

- **XML tag structuring** — Anthropic best practice for semantic section boundaries (vs. plain-text dividers)
- **Few-shot examples** — Two full wargame exchanges; research shows 15-40% accuracy improvement over zero-shot
- **Chain-of-thought reasoning framework** — Six-step reasoning process using the RAR (Role-Aware Reasoning) method
- **Positive-only instructions** — All behavioral rules use positive framing; negative prompts degrade performance at scale (Pink Elephant Problem / IJCAI 2024)
- **Drift detection and self-verification** — Built-in VERIFY step: "Is this grounded in Russian doctrine, or am I defaulting to Western logic?"
- **Bilingual terminology anchoring** — Russian terms in parentheses serve as semantic anchors that reinforce the persona's cultural framework
- **Anti-mirror-imaging safeguards** — Explicit instructions to think FROM the Russian perspective, not ABOUT it
- **CO-STAR framework compliance** — All six components (Context, Objective, Style, Tone, Audience, Response format) covered
- **Scope boundaries** — Educational context framing that maintains persona realism without triggering safety refusals

---

## Architecture

- **Single HTML file** — no build step, no bundler, no framework dependencies
- **Client-side only** — all API calls go directly from your browser to the provider; nothing routes through a backend
- **API keys in localStorage** — never transmitted anywhere except the selected provider's API endpoint
- **GitHub Pages deployment** — static hosting, no server required

---

## Doctrinal Sources

The persona's doctrinal foundation draws from these primary sources (full bibliography in [`docs/doctrinal-sources.md`](docs/doctrinal-sources.md)):

1. **Russia's 2014 Military Doctrine** — defines threat perceptions, conflict spectrum, and force employment principles
2. **Russia's 2020 Nuclear Deterrence Principles** — the four published conditions for nuclear employment
3. **Gerasimov, "The Value of Science Is in the Foresight"** (VPK, 2013) — the actual text behind the "Gerasimov Doctrine" myth
4. **Chekinov & Bogdanov** (*Voyennaya Mysl*, 2010-2017) — 13 articles on new-generation warfare
5. **Svechin, *Strategy*** (1927) — foundational text on operational art
6. **Thomas, "Russia's Reflexive Control Theory"** (JSMS, 2004) — the definitive Western analysis
7. **RAND, *Correlation of Forces and Means*** (2020) — modern Russian COFM methodology
8. **Glantz, *Soviet Military Deception in the Second World War*** (1989) — maskirovka doctrine
9. **Grau & Bartles, *The Russian Way of War*** (FMSO, 2016) — force structure and institutional culture
10. **Ven Bruusgaard, "Russian Nuclear Strategy"** (JSS, 2020) — corrective to "escalate to de-escalate"

---

## License

[MIT](LICENSE)
