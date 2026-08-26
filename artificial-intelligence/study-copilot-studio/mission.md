---
description: >-
  The learning plan for the Copilot Studio course — mission, sources, and full
  session map.
icon: compass
---

# Mission

## Why this, in my own frame

Anchor: [What Is AI, Really? — Thinking About the Goal of "Human-Like"](https://dyns.ntd.asia/power-dynamics/artificial-intelligence/what-is-ai-really)

That piece argues knowledge alone "makes you a library," not something human-like. Skill is what sits between wanting something and having it, built through repetition, failure, and watching whether something you built actually holds up. It names agentic AI — systems that act, not just answer — as the current attempt at that second half.

This course is built on that premise. It doesn't stop at "the agent can answer questions" (the library). It pushes through to "the agent can act, decide, and coordinate with other agents in a live system" (the skill) — and every session ends with something built and tested, not just explained.

{% hint style="info" %}
**Current level:** some exposure — you've used Copilot-style tools and clicked around Copilot Studio, but haven't built real topics, knowledge, or tools work yet.
{% endhint %}

## Practice scenario

All hands-on exercises build one running example: a customer-facing support agent for a fictional retailer, **Northwind Outfitters** — order status, FAQs, returns and exchanges. It naturally exercises knowledge grounding (FAQs), tools and actions (order lookup), generative answers, autonomous triggers (proactive return follow-ups), and multi-agent handoff (billing vs. product support) — the same shape as the enterprise scenarios in Microsoft's own certification material.

## Primary sources

* Official course skeleton (launches 9/18/2026, Intermediate): [AB-620T00-A course page](https://learn.microsoft.com/en-us/training/courses/ab-620t00)
* Exam skills outline (usable now, same domains as the course): [Study guide for Exam AB-620](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/ab-620)
* Certification overview: [Microsoft Certified: AI Agent Builder Associate](https://learn.microsoft.com/en-us/credentials/certifications/ai-agent-builder-associate/)
* Foundational learning paths filling the beginner gap AB-620 assumes: [Create and publish agents](https://learn.microsoft.com/training/paths/work-power-virtual-agents/) · [Create agents in Copilot Studio](https://learn.microsoft.com/training/paths/create-extend-custom-copilots-microsoft-copilot-studio/) · [Agent in a Day](https://learn.microsoft.com/training/paths/agents-online-workshop/) · [Extend Microsoft 365 Copilot](https://learn.microsoft.com/training/paths/extend-microsoft-365-copilot-studio/)
* Product docs (verified per lesson): [Copilot Studio documentation](https://learn.microsoft.com/microsoft-copilot-studio/)

## Session estimate

**\~20 sessions** to working proficiency, recomputed group by group with a standing Session-Sizing Engine pass before each group starts. Group 2 added one spaced-review session over its original plan (2.4); Group 3 added one grounding-and-citations session over its original plan (3.2). **Group 4 was sized before 4.1 started: 5 sessions, up from the original 4** — connectors (4.1), agent flows (4.2), custom prompts/REST APIs (4.3), and adaptive cards (4.4) each carry their own distinct integration mechanism that doesn't compress safely into a shared session, and a closing review/build session (4.5) was added to match the same spaced-review pattern 2.4 and Group 3 both established. **4.4 is now taught** — every ad hoc and formatting mechanism Group 4 set out to cover (connectors, agent flows, prompts, REST APIs, and now response formatting via Adaptive Cards) is in place, with only 4.5's closing Northwind build left. The running estimate is now closer to **\~25–27 sessions** as this pattern continues — recomputed one group at a time, not projected all at once.

AB-620 itself is a 3-day intermediate course that assumes hands-on agent-building experience already in place. Group 1–2 (about 6 sessions) close that gap. From Group 3 on, sessions map directly onto AB-620's three skill domains — Plan & configure (30–35%), Integrate & extend (40–45%), Test & manage (20–25%) — broken into single-concept lessons small enough to verify and practice rather than compressed into 24 hours of lecture.

## Session map

| Group                                   | #   | Session                                                      | Status   |
| --------------------------------------- | --- | ------------------------------------------------------------ | -------- |
| 1 — Foundations & Orientation           | 1.1 | What Copilot Studio actually is                              | ✅ Taught |
|                                         | 1.2 | How an agent decides                                         | ✅ Taught |
| 2 — Core Building Blocks                | 2.1 | Topics & the authoring canvas                                | ✅ Taught |
|                                         | 2.2 | Entities and variables                                       | ✅ Taught |
|                                         | 2.3 | Generative answers & instructions                            | ✅ Taught |
|                                         | 2.4 | Review & retrieval                                           | ✅ Taught |
| 3 — Knowledge & Grounding (complete)    | 3.1 | Knowledge sources fundamentals (files, SharePoint, websites) | ✅ Taught |
|                                         | 3.2 | Grounding mechanics & citations                              | ✅ Taught |
|                                         | 3.3 | Azure AI Search & custom knowledge sources                   | ✅ Taught |
| 4 — Tools & Actions (sized: 5 sessions) | 4.1 | Connectors & Power Platform actions                          | ✅ Taught |
|                                         | 4.2 | Agent flows: human-in-the-loop & error handling              | ✅ Taught |
|                                         | 4.3 | Prompts and REST APIs: off the connector path                | ✅ Taught |
|                                         | 4.4 | Adaptive cards & response formatting                         | ✅ Taught |
|                                         | 4.5 | Review & build (Northwind tool chain)                        | ⬜ Next   |
| 5 — Agentic Behavior: Autonomous Agents | 5.1 | Designing autonomous agent capabilities                      | ⬜        |
|                                         | 5.2 | Build & deploy an autonomous agent                           | ⬜        |
|                                         | 5.3 | Monitoring and governing autonomy                            | ⬜        |
| 6 — Multi-Agent Orchestration           | 6.1 | Multi-agent design patterns & best practices                 | ⬜        |
|                                         | 6.2 | Adding child agents                                          | ⬜        |
|                                         | 6.3 | Integrating a Foundry agent & MCP tools                      | ⬜        |
|                                         | 6.4 | Agent2Agent (A2A) protocol & Fabric data agents              | ⬜        |
| 7 — Enterprise Integration & Governance | 7.1 | Identity, security & responsible AI strategy                 | ⬜        |
|                                         | 7.2 | ALM: solutions, environment variables, pipelines             | ⬜        |
| 8 — Testing & Capstone                  | 8.1 | Evaluating agents: test sets & evaluation methods            | ⬜        |
|                                         | 8.2 | Capstone: full Northwind Outfitters agent                    | ⬜        |
