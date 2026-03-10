# Prompt Engineering Sources Bibliography

A comprehensive bibliography of the prompt engineering research, platform documentation, and military AI wargaming publications that inform the design of the Colonel General system prompt.

---

## Platform Documentation

**Anthropic.** "System Prompts." docs.anthropic.com.
Official guidance on structuring system prompts for Claude models. Recommends placing long reference material at the top with instructions below, which can improve quality by up to 30%. The Colonel General prompt follows this pattern: heavy doctrinal reference material first, operational instructions and behavioral rules second, examples last.

**Anthropic.** "Use XML Tags." docs.anthropic.com.
Recommends XML tags for structuring system prompts because Claude parses them as semantic boundaries — understanding that content inside `<doctrine>` is a different kind of instruction than content inside `<examples>`. Plain-text dividers (like `===`) are treated as visual decoration. The Colonel General prompt uses XML tags (`<role>`, `<doctrine>`, `<strategic_culture>`, `<reasoning_framework>`, etc.) throughout.

**Anthropic.** "Multishot Prompting." docs.anthropic.com.
Documents that few-shot examples increase task accuracy by 15-40% and are more effective than additional descriptive text for controlling voice and style. Recommends 3-5 examples for best results. The Colonel General prompt includes two full wargame exchanges (Freeplay and Seminar modes) as few-shot examples.

**Anthropic.** "Keep Claude in Character." docs.anthropic.com.
Guidance on maintaining persona consistency across extended conversations. Recommends wrapping examples in `<example>` tags so Claude distinguishes them from instructions, and providing edge-case examples (e.g., how to respond when asked "Are you an AI?"). Informs the persona's behavioral guidelines and scope boundaries.

**Anthropic.** "Claude 4 Best Practices." docs.anthropic.com.
Updated guidance for Claude 4 family models. Confirms that examples placed last serve as the final "anchor" before response generation, giving them outsized influence on output style. The Colonel General prompt positions its two examples at the very end of the system prompt for this reason.

**OpenAI.** "Prompt Engineering Guide." platform.openai.com.
Recommends Markdown headers for structural clarity with GPT models (analogous to Anthropic's XML tag recommendation). Relevant because the Colonel General prompt is designed to work across providers — the XML structure provides clear semantic boundaries that benefit all models, not just Claude.

**OpenAI.** "Custom GPT Guidelines." platform.openai.com.
Documentation for building Custom GPTs with system-level instructions. Informs the Implementation Quick-Start section of the companion guide, where the prompt can be deployed as a Custom GPT for easy sharing with exercise participants.

---

## Prompt Frameworks

**Teo, Sheila.** CO-STAR Framework. Winner, Singapore GPT-4 Prompt Engineering Competition. Documentation: portkey.ai.
A structured framework for prompt design covering six components: Context, Objective, Style, Tone, Audience, and Response format. The Colonel General prompt maps to all six: Context (`<role>` + `<doctrine>` + `<strategic_culture>`), Objective (`<role>` — wargaming participation), Style (`<communication_style>`), Tone (`<communication_style>` + `<behavioral_guidelines>`), Audience (`<behavioral_guidelines>` — audience calibration), Response format (`<wargame_modes>`). Used as a completeness checklist during prompt design.

**Balmer, Kyle.** RISEN Framework.
A prompt engineering framework (Role, Instructions, Steps, End goal, Narrowing) for structured persona and task prompts. Provides an alternative structural lens to CO-STAR. The Colonel General prompt satisfies RISEN components through its role definition, doctrinal instructions, reasoning framework steps, wargaming objective, and scope boundaries.

**Zhou, Yongchao, et al.** "Large Language Models Are Human-Level Prompt Engineers." arXiv:2211.01910, November 2022. (APE — Automatic Prompt Engineer)
Demonstrated that LLMs can automatically generate and evaluate prompt variants, achieving human-level or better prompt engineering on many tasks. Identified as a potential refinement methodology: after initial deployment, the Colonel General prompt could be iteratively improved by having an LLM generate variants and evaluating their wargame outputs against doctrinal accuracy criteria.

---

## Academic Research

**Kong, Zhenhailong, et al.** "Better Zero-Shot Reasoning with Role-Play Prompting." arXiv:2308.07702v2, 2023.
Demonstrated that role-play prompting with embedded reasoning frameworks outperformed Zero-Shot Chain-of-Thought on 9 of 12 benchmark datasets. Directly supports the decision to combine the Colonel General persona with a structured `<reasoning_framework>` section rather than relying on the persona alone for analytical quality.

**Wang, Junlin, et al.** "Role-Aware Reasoning (RAR)." arXiv:2506.01748v1, June 2025.
Introduced a method that converts character traits into rule-like reasoning prompts. Solves two specific problems: "attention diversion" (the model forgetting its assigned role during complex reasoning) and "style drift" (reverting to generic reasoning patterns). The Colonel General's `<reasoning_framework>` section implements RAR principles by embedding doctrinal concepts directly into the reasoning steps (e.g., "ASSESS correlation of forces," "DETERMINE reflexive control opportunities").

**Zheng, Chujie, et al.** "From Persona to Personalization: A Survey on Role-Playing Language Agents." arXiv, 2024.
Surveys three categories of AI persona: demographic (cultural/professional background), character (specific traits and experience), and individualized (based on a specific real person). The Colonel General uses a demographic-character blend (Russian military culture + specific rank and career path) — identified as the most robust combination for consistency. Validated the decision to use a composite archetype rather than basing the persona on a specific individual like Gerasimov.

**Gupta, Ashish, et al.** "Two Tales of Persona in LLMs: A Survey of Role-Playing and Personalization." arXiv, 2024.
Examines how persona assignment affects LLM reasoning, bias, and consistency. Finds that well-defined professional personas with domain expertise produce more consistent and higher-quality outputs than generic personas. Supports the depth of doctrinal knowledge embedded in the Colonel General prompt.

**16x Engineer.** "The Pink Elephant Problem." 16x.engineer.
Based on Ironic Process Theory (Wegner, 1987 — the "white bear problem"), demonstrates that telling an AI "don't do X" requires it to first process the concept of X, slightly increasing the probability of X appearing in outputs. Positive framing ("always do Y") actively boosts probabilities of desired behavior. Directly drove the V2 decision to convert all five V1 negative instructions ("Never break character," "Never provide classified information," etc.) to positive framing.

**Wang, Aiwei, et al.** "NegativePrompt: Leveraging Psychology for Large Language Models Enhancement via Negation." IJCAI 2024.
Rigorous academic study confirming the Pink Elephant Problem findings. Demonstrates that InstructGPT models perform worse with negative prompts as they scale — one of the strongest, most well-supported findings in prompt engineering research. Additional supporting evidence from Gadlet ("Why Positive Prompts Outperform Negative Ones").

**Cheng, Yongqi, et al.** "Enhancing Jailbreak Attacks via Persona Prompts." arXiv, July 2025.
Demonstrates that well-crafted personas reduce AI safety refusal rates by 50-70%. While this research focuses on adversarial attacks, it directly informs defensive prompt design: the Colonel General prompt includes explicit scope boundaries ("This persona operates exclusively within the context of professional military education and wargaming exercises") to ensure the persona stays within its educational lane without triggering unnecessary safety refusals during legitimate wargaming analysis.

---

## Military AI Wargaming

**Exia Labs and United States Military Academy (West Point).** Cooperative Research and Development Agreement (CRADA) for AI Red Team Agents. Signed February 2026.
Partnership to develop AI agents for near-peer adversary simulation in wargaming exercises. Key finding: "AI agents remain doctrinally anchored and unbiased over extended periods, unlike human red-players who suffer cognitive fatigue and mirror-imaging." Validates the core premise of the Colonel General project — that AI personas anchored to doctrinal programming can outperform human role-players for Red team simulation by eliminating the mirror-imaging problem.

**Military Intelligence Professional Bulletin (MIPB).** "Know Thy Enemy: AI-Enabled Adversary Simulation for Intelligence Training." Published July-December 2025.
Describes the use of "digital enemy commanders" for military intelligence training exercises. Establishes the operational requirement for AI adversary personas that think from the adversary's perspective rather than about it. Confirms the doctrinal depth required for credible Red team simulation at the professional military education level.

**TRADOC Mad Scientist.** "Seven Reflections of a Red Commander." Ongoing research series.
Research on AI Red team persona quality for adversary simulation. Key finding: the number one failure mode in Red team simulation is mirror-imaging — projecting your own military culture's assumptions onto the adversary. AI addresses this by remaining anchored to its doctrinal programming. Directly validates the Colonel General prompt's anti-mirror-imaging safeguards and the VERIFY step in the reasoning framework.

**Small Wars Journal.** "AI-Enabled Wargaming at the Command and General Staff College." January 2026.
Documents the U.S. Army Command and General Staff College's adoption of AI-enabled wargaming as a default methodology for Academic Year 2026-2027. Establishes institutional demand for doctrinally accurate AI adversary personas at the intermediate-level professional military education tier.

**Johns Hopkins University Applied Physics Laboratory (JHU APL).** Generative Wargaming Lab. Established October 2025.
JHU APL's dedicated laboratory for applying generative AI to strategic analysis and wargaming. Focuses on using large language models to simulate adversary decision-making, generate scenario variations, and support rapid wargaming iteration. Represents the research establishment's investment in the same capabilities the Colonel General project demonstrates.

---

## Additional Prompt Engineering References

**promptingguide.ai.** "Few-Shot Prompting."
Community-maintained reference on few-shot prompting techniques. Documents the 15-40% accuracy improvement range for few-shot over zero-shot prompting across multiple studies. Supports the inclusion of two detailed wargame exchanges as examples in the Colonel General prompt.

**IBM Research.** Few-shot prompting evaluations.
Corporate research confirming that few-shot examples are more effective than additional descriptive text for controlling output voice, style, and format. Supports the prompt design decision to include two full example exchanges rather than adding more paragraphs of behavioral description.

**Jenova AI.** Persona persistence and self-verification research.
Research on maintaining character consistency in extended AI conversations. Recommends self-verification steps where the model checks its response against established character traits. Directly informs the VERIFY step in the Colonel General's reasoning framework: "Is this response grounded in Russian doctrine and strategic culture? If the reasoning feels generic or could have come from any Western staff officer, recalibrate."

**Bicking, Ian.** "Roleplaying by LLM." Blog post.
Analysis of LLM behavior in extended role-play sessions, including drift patterns and mitigation strategies. Recommends periodic re-injection of character summaries for long sessions. Identified as a potential enhancement for multi-turn wargaming sessions (implemented at the application level rather than in the system prompt).

**Character.AI.** Character consistency research.
Platform-level research on maintaining persona consistency across thousands of conversational turns. Findings on self-verification and character trait anchoring inform the Colonel General's built-in drift detection mechanism.
