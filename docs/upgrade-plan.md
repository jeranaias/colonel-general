# Colonel General: Full Upgrade & Commercialization Plan

*Prepared March 2026 — Synthesized from competitive intelligence, funding landscape analysis, and technical state-of-the-art research.*

---

## Executive Summary

The AI wargaming space is exploding. The Pentagon allocated $13.4B for AI/autonomy in FY2026. CGSC made AI wargaming the default methodology. West Point, JHU APL, Scale AI, and Palantir are all building tools. But every competitor is building **closed, enterprise-grade, classified-track products**. Nobody is building the **open-source, educationally transparent, doctrinally-grounded** tool — and that's the lane with the most publishable novelty and the clearest path to institutional adoption.

The research reveals **6 gaps in the published literature** that no one has addressed. Colonel General, upgraded correctly, can fill 3-4 of them simultaneously and produce a genuinely novel contribution to both the AI and defense research communities.

---

## Part 1: The Competitive Landscape (Who You're Not Competing With)

### Enterprise / Classified Track (Not Your Lane)
| Player | What They're Building | Funding | Status |
|---|---|---|---|
| **JHU APL** | GenWar (TTX + Sim + SAGE), integrates with AFSIM, building TS/SCI versions | Institutional (APL is a UARC) | Dedicated lab opening 2026 |
| **Scale AI / Thunderforge** | Theater-level AI planning, deployed to INDOPACOM/EUCOM | DIU contract | In production |
| **Palantir** | NATO Maven AI + Hadean wargaming for UK MoD | GBP 20M MoD contract | Deployed |
| **DARPA SCEPTER** | 10K-100K faster-than-real-time, 10K agents | $39M program | Charles River Analytics, BAE |
| **Air Force WarMatrix** | Cloud-based AI sandbox, Unclass through TS/SCI/SAP | RFI stage (Jan 2026) | Pre-solicitation |

### Direct Competitor
| Player | What They're Building | Funding | Gap vs. Colonel General |
|---|---|---|---|
| **Exia Labs** | AI Red Agents for wargaming, West Point CRADA | $2.5M pre-seed, 4 people | Proprietary, no educational layer, no evaluation framework published |

### Adjacent / Academic
| Player | What They're Building | Gap |
|---|---|---|
| **IQT Labs Snow Globe** | Open-source multi-agent wargaming | No doctrinal grounding, no educational design |
| **CGSC Vantage Agent** | OAG+RAG with 128K context, doctrinal constraints | Exercise-specific, not generalizable, not published as framework |
| **King's College London** | LLM nuclear crisis simulations | Research study, not a tool; found 95% nuclear escalation |

### Your Lane: Open, Educational, Doctrinally-Grounded
Nobody occupies the intersection of:
1. Open-source tool anyone can use with a free API key
2. Doctrinally-grounded adversary personas (not just "play the enemy")
3. Educational transparency (see HOW and WHY the AI reasons)
4. Published evaluation framework for doctrinal fidelity
5. Designed for PME classrooms, not classified war rooms

---

## Part 2: The 6 Publishable Gaps

Research across 50+ sources (arxiv, defense journals, conference proceedings) identified these gaps where **no published work exists**:

### Gap 1: Adversary Persona Evaluation Framework ⭐ PRIMARY TARGET
No standardized rubric or benchmark exists for measuring whether an AI adversary persona is doctrinally accurate. The NeurIPS 2025 persona consistency metrics (prompt-to-line, line-to-line, Q&A consistency) have never been adapted for military doctrine. Exia Labs hasn't published their evaluation methodology.

**What to build:** A formal evaluation rubric with:
- Doctrinal fidelity scoring (does the response reference correct doctrine?)
- Mirror-imaging detection (does the response default to Western assumptions?)
- Decision consistency (does the persona maintain coherent strategic logic across turns?)
- Expert validation protocol (how SMEs rate outputs)

### Gap 2: Mirror-Imaging Technical Mitigation ⭐ HIGH IMPACT
Cross-cultural LLM bias is well-documented (PNAS Nexus 2024: all GPT models exhibit Western/Protestant cultural values). The MACD framework (Multi-Agent Cultural Debate, Jan 2026) is the most promising approach. But nobody has applied it to adversary military modeling specifically.

**What to build:** A structured anti-mirror-imaging pipeline:
- Detect Western assumptions in AI outputs (automated classifier)
- RAG retrieval from adversary-specific doctrine corpus
- VERIFY step with explicit doctrinal citation requirement
- Comparative analysis showing improvement over naive prompting

### Gap 3: Educational Transparency in AI Wargaming ⭐ YOUR UNIQUE ANGLE
Every existing tool treats the AI adversary as a black box. CGSC mentions "prompt transparency logs" but hasn't published a framework. Making the adversary's cognitive process an explicit teaching tool is completely unexplored.

**What to build:** The "glass-box adversary" — every response shows:
- Which doctrinal concepts were activated and why
- The reasoning chain mapped to the structured framework
- Alternative courses of action that were considered and rejected
- Confidence levels with doctrinal citation

### Gap 4: RL/DPO for Doctrinal Persona Fidelity
Persona consistency via reinforcement learning works (NeurIPS 2025: 55% drift reduction). But it's only been applied to chatbot personalities. Using expert-rated doctrinal accuracy as a reward signal for DPO/RLHF has never been attempted.

**What to build (Phase 2/grant-funded):** Fine-tuned model variant where:
- SME panel rates doctrinal accuracy of outputs
- Ratings become training signal for DPO alignment
- Resulting model compared against prompt-only baseline

### Gap 5: Structured Wargaming Decision Schema
No standard output format exists for AI adversary decisions that maps to wargaming constructs (force dispositions, phasing, decision points, branches/sequels).

**What to build:** A JSON/structured schema for adversary decisions:
- Course of action with doctrinal basis
- Force allocation by domain
- Phasing with decision points
- Risk assessment per Russian COFM methodology
- Integration hooks for existing M&S tools

### Gap 6: Longitudinal Doctrinal Drift
Nobody has measured whether AI personas degrade across multiple independent sessions. This matters for PME programs running the same adversary across dozens of student cohorts.

**What to build:** Measurement study across 50+ independent sessions tracking:
- Doctrinal reference frequency over time
- Response diversity (does it get repetitive?)
- Mirror-imaging rate per session
- Publish findings with dataset

---

## Part 3: The Product Upgrade Roadmap

### Phase 0: Current State (Colonel General v1 — DONE)
- Single Russian General Staff persona
- Multi-provider API (Gemini, OpenRouter, Anthropic)
- Editable system prompt with persistence
- 6 pre-built scenarios
- Educational learn panel (Guide, Sources tabs)
- Pure prompt engineering, no RAG

### Phase 1: Research Platform (3-6 months, self-funded or small grant)
**Goal:** Transform from demo into publishable research tool.

**1a. Doctrinal RAG Engine**
- Build a document corpus: Russian military doctrine (2014 Military Doctrine, 2015 National Security Strategy, 2020 Nuclear Principles, Gerasimov 2013, Chekinov-Bogdanov series, Svechin, Triandafillov, Isserson)
- Implement client-side RAG using embeddings (run in browser via transformers.js or use provider's embedding API)
- Every response cites specific doctrinal passages from the corpus
- Fallback to prompt-only mode when RAG unavailable

**1b. Glass-Box Reasoning (Educational Transparency)**
- Add "Show Reasoning" toggle on each assistant message
- Structured chain: ASSESS → IDENTIFY → DETERMINE → EVALUATE → SELECT → VERIFY
- Each step shows which doctrinal concept was invoked and why
- Alternative COAs shown with rejection rationale
- This is the **novel contribution** — nobody else does this

**1c. Evaluation Dashboard**
- Built-in doctrinal fidelity scoring
- Mirror-imaging detection (flag responses that don't reference Russian-specific concepts)
- Session consistency tracking (drift detection over conversation)
- Export evaluation data as JSON for research use
- SME rating interface (1-5 scale per response on doctrinal accuracy, cultural authenticity, strategic coherence)

**1d. Multi-Persona Architecture**
- Refactor prompt system to support multiple adversary personas
- Add PLA Senior Colonel (Chinese military doctrine)
- Add IRGC Brigadier General (Iranian military doctrine)
- Each persona has its own doctrinal corpus, reasoning framework, and scenarios
- Persona selection in UI alongside provider selection

**1e. Structured Output Mode**
- Toggle between narrative response and structured decision format
- JSON schema: COA, doctrinal basis, force allocation by domain, phasing, decision points, risk assessment
- Export-friendly for integration with other tools

### Phase 2: Validated Research Tool (6-18 months, grant-funded)
**Goal:** Produce peer-reviewed publications and institutional partnerships.

**2a. PME Validation Study**
- Partner with a war college or staff college (CGSC, NWC, AWC, Marine Corps University)
- Run controlled experiment: students using Colonel General vs. traditional Red team methods
- Measure: learning outcomes, mirror-imaging reduction, doctrinal comprehension
- Publish results

**2b. Doctrinal Fidelity Benchmark**
- Assemble SME panel (retired military officers, regional specialists, doctrine scholars)
- Rate 500+ AI-generated responses across all personas
- Publish benchmark dataset and evaluation rubric
- This becomes the **standard** others measure against

**2c. Multi-Agent Wargaming**
- Red team AI vs. Blue team AI vs. White cell (umpire) AI
- Each agent uses persona-specific doctrine and reasoning
- Human players can take over any role at any point
- Session replay with reasoning chains visible for all agents

**2d. RL/DPO for Doctrinal Alignment (if compute available)**
- Use SME ratings from 2b as training signal
- Fine-tune open model (Llama, Mistral) with DPO for doctrinal consistency
- Compare against prompt-only and RAG baselines
- Publish results — first application of RL persona consistency to military doctrine

### Phase 3: Platform (18-36 months, SBIR Phase II or venture)
**Goal:** Deployable product for PME institutions.

- Multi-classification hosting (IL2/IL4/IL5)
- Map/geospatial integration
- Campaign management (multi-session scenarios with state persistence)
- LMS integration (Canvas, Blackboard) for classroom deployment
- API for integration with existing M&S frameworks (AFSIM, JICM)
- Institutional licensing model

---

## Part 4: Funding Strategy

### Immediate Actions (March-April 2026)

| Action | Deadline | Amount | Fit |
|---|---|---|---|
| **DARPA CLARA proposal** | April 10, 2026 | Up to $2M | Explainable, verifiable AI — directly applicable to glass-box reasoning |
| **Connections 2026 presentation** | Call open now, conference June 23-25 at NPS Monterey | Travel costs | Maximum visibility to wargaming community |
| **Smith Richardson Foundation concept paper** | Rolling (no deadline) | ~$50-400K | International security + adversary analysis framing |

### Near-Term (2026)

| Action | Deadline | Amount | Fit |
|---|---|---|---|
| **NSF CISE Future CoRe** | September 10, 2026 | Up to $1M/4yr | "Explainable AI personas for strategic education" |
| **DARPA I2O Office-Wide BAA** | Abstracts Nov 1, 2026 | $500K-$5M | "Trustworthy AI for information domain" |
| **NATO SPS Programme** | 2026 call published | EUR 250-400K | Allied adversary simulation for NATO PME |
| **Carnegie Corporation** | Rolling | ~$400-500K | AI governance + conflict prevention angle |

### When SBIR Reauthorizes (Expected 2026)

| Target | Amount | Approach |
|---|---|---|
| **AFWERX (Air Force)** | $1.25M (Direct-to-Phase-II precedent: AMESA) | AI wargaming for Air University PME |
| **Army SBIR** | $250K Phase I | Context-aware adversary decision support for CGSC |
| **Navy SBIR** | $250K Phase I | "Knowing the True Adversary: Acculturating Behavior Models" (past topic, likely to recur) |

### Publication Strategy

**Paper 1 (Conference, Summer 2026):** "Colonel General: An Open-Source Framework for Doctrinally-Grounded Adversary Simulation with Educational Transparency"
- Venue: Connections 2026 (NPS Monterey, June) or MORS 94th Symposium (Colorado Springs, June)
- Content: Framework description, doctrinal grounding methodology, glass-box reasoning approach, preliminary evaluation

**Paper 2 (Journal, Fall 2026):** "Evaluating Doctrinal Fidelity in LLM-Based Adversary Personas: A Framework and Benchmark"
- Venue: Journal of Defense Modeling and Simulation (had an AI+Wargaming special issue Jan 2025)
- Content: Evaluation rubric, SME validation protocol, benchmark results, comparison with ungrounded baselines

**Paper 3 (AI Conference, 2027):** "Reducing Mirror-Imaging in AI Adversary Simulation through Doctrinal RAG and Structured Reasoning"
- Venue: AAAI, AAMAS, or NeurIPS workshop
- Content: Technical approach to anti-mirror-imaging, quantitative comparison, cross-cultural reasoning results

**Paper 4 (Education, 2027):** "Glass-Box Adversaries: Educational Transparency in AI Wargaming for Professional Military Education"
- Venue: I/ITSEC or Military Operations Research journal
- Content: PME validation study results, learning outcome measurements

---

## Part 5: What Makes This Win

### The Heilmeier Catechism (How DARPA Evaluates)

**1. What are you trying to do?**
Build an open-source AI adversary simulation tool where the adversary's reasoning is transparent, doctrinally grounded, and educationally useful — not a black box.

**2. How is it done today, and what are the limits?**
Human Red teamers suffer mirror-imaging and cognitive fatigue. Existing AI tools (GenWar, Thunderforge, Exia Labs) are closed-source, enterprise-grade, and treat the AI as a black box. No tool makes the adversary's reasoning process a teaching instrument.

**3. What is new in your approach?**
Three things no one else does: (a) doctrinal RAG grounding with citation, (b) glass-box reasoning chains that students can inspect and learn from, (c) a published evaluation framework for measuring doctrinal fidelity.

**4. Who cares?**
Every PME institution in the US and NATO. CGSC just made AI wargaming mandatory. War colleges need tools their instructors can actually use without procurement cycles and ATOs.

**5. What difference will it make?**
Students learn adversary thinking by seeing it happen, not just hearing about it. Instructors get a Red team that never mirror-images and can run 24/7. The evaluation framework gives the community a standard to measure all adversary AI tools against.

**6. What are the risks?**
LLMs may still exhibit Western bias despite doctrinal grounding. Escalation bias (95% nuclear use in King's College study) may persist. Mitigation: RAG grounding, structured reasoning, and the evaluation framework itself detects these failures.

**7. How much will it cost?**
Phase 1 (research platform): $250K-$500K. Phase 2 (validated tool): $1-2M. Phase 3 (deployable platform): $3-5M.

**8. What are the mid-term and final exams?**
Mid-term: Published evaluation framework, SME-validated benchmark, conference presentation. Final: Controlled PME study showing measurable improvement in student understanding of adversary decision-making.

---

## Part 6: Key Differentiators (Why You, Not Them)

| Factor | Exia Labs | JHU APL GenWar | Scale AI Thunderforge | **Colonel General** |
|---|---|---|---|---|
| Open source | No | No | No | **Yes** |
| Zero infrastructure | No | No | No | **Yes (browser + API key)** |
| Educational transparency | No | No | No | **Yes (glass-box reasoning)** |
| Published eval framework | No | No | No | **Target** |
| Doctrinal RAG | Unknown | Yes (OAG) | Unknown | **Phase 1 target** |
| Multi-persona | Unknown | Yes | Yes | **Phase 1 target** |
| Classification ready | Pursuing | TS/SCI | IL5 | **No (and that's fine for PME)** |
| Cost to try | Enterprise sales | UARC relationship | DIU contract | **Free (Gemini free tier)** |

The pitch: **"The adversary AI that teaches you how it thinks."**

---

## Appendix: Key Sources

### Competitive Intelligence
- Exia Labs West Point CRADA (Feb 2026): blog.exialabs.com
- JHU APL GenWar Lab (Oct 2025): jhuapl.edu
- Scale AI Thunderforge / DIU (Mar 2025): breakingdefense.com
- Palantir NATO Maven (Apr 2025): breakingdefense.com
- Air Force WarMatrix RFI (Nov 2025): defensescoop.com
- DARPA SCEPTER ($39M): darpa.mil
- AMESA $1.25M SBIR for AI wargaming (Dec 2025): amesa.com
- CSIS "Democratize Wargaming Using GenAI" (Dec 2024): csis.org
- RAND "Should I Use AI in My Wargame?" (Apr 2025): rand.org

### Technical State of the Art
- King's College London nuclear crisis study — 95% escalation (Feb 2026): arxiv 2602.14740
- NeurIPS 2025 persona consistency via RL — 55% drift reduction: arxiv 2511.00222
- MACD multi-agent cultural debate (Jan 2026): arxiv 2601.12091
- CoALA cognitive architecture for language agents: arxiv 2309.02427
- IQT Labs Snow Globe multi-agent wargaming (Apr 2024): arxiv 2404.11446
- CGSC AI-enabled wargaming (Jan 2026): smallwarsjournal.com
- Korean Navy ontology+ECA+LLM wargaming (2026): SIMULATION journal

### Funding
- DARPA CLARA — proposals due April 10, 2026: darpa.mil
- NSF CISE Future CoRe — deadline September 10, 2026: nsf.gov
- DARPA I2O BAA — abstracts November 1, 2026: darpa.mil
- NATO SPS 2026 call: nato.int
- Smith Richardson Foundation: srf.org
- Carnegie Corporation: carnegie.org
- SBIR reauthorization status: ebhoward.com
- Pentagon FY2026 AI budget ($13.4B): cdomagazine.tech

### Publication Venues
- Journal of Defense Modeling and Simulation (AI+Wargaming special issue Jan 2025)
- Connections 2026 at NPS Monterey (June 23-25, call open)
- MORS 94th Symposium (June 8-11, Colorado Springs)
- I/ITSEC 2026 (December, Orlando)
- AAAI-26, AAMAS 2026, NeurIPS 2026
