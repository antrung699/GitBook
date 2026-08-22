---
description: >-
  Session 1.2 — classic vs. generative orchestration, the three control layers
  for agent autonomy, and why the GitHub Copilot harness skips the toggle
  entirely.
icon: brain
---

# How an Agent Decides

{% hint style="info" %}
**Group 1 · Session 1.2** of the Copilot Studio course. Full plan on the [Mission](https://dyns.ntd.asia/power-dynamics/artificial-intelligence/study-copilot-studio/mission) page. Follows [What's Copilot Studio?](https://dyns.ntd.asia/power-dynamics/artificial-intelligence/study-copilot-studio/foundations/whats-copilot-studio).
{% endhint %}

Session 1.1 sorted your agent into a harness. This session opens the box: what actually happens between a user's message and the agent's response — and who's allowed to decide what.

## Two different decision-makers

The standard harness makes you choose, per agent, between two ways of deciding how to respond. It's a real toggle on the agent's Settings page, not a conceptual distinction — you'll flip it yourself in Session 2. The GitHub Copilot harness doesn't give you that toggle at all, and that absence is the more interesting fact, covered at the end of this lesson.

## Classic orchestration: match and script

Classic is the older, fully scripted model. The agent compares the user's message against the trigger phrases you wrote for each topic, picks the closest match, and runs that topic's steps exactly as you built them: question nodes to ask for input, message nodes to reply. If nothing matches, it falls back to knowledge search, and if that fails too, it escalates. Nothing here is generated on the fly — you authored every sentence the agent can say.

## Generative orchestration: plan and compose

Generative is the default for every newly created standard-harness agent. Instead of matching phrases, an LLM-driven planner reads the topic, tool, knowledge source, and connected-agent _descriptions_ you wrote, decides which are relevant to the request, and can call several of them in one turn. Ask a Northwind agent "what's your return window, and can you check on order 4471" and it doesn't pick one topic — it runs the return-policy topic and the order-status tool in the same turn, then writes one combined reply itself.

| Behavior              | Generative orchestration                                 | Classic orchestration                      |
| --------------------- | -------------------------------------------------------- | ------------------------------------------ |
| Picks a topic by      | Matching its description to the request                  | Matching trigger phrases                   |
| Can combine sources   | Yes — topics, tools, knowledge, other agents in one turn | No — one topic, knowledge only as fallback |
| Asks for missing info | Generates the question itself                            | You author a question node                 |
| Writes the reply      | Generates it from whatever it gathered                   | You author a message node                  |

The cost of that flexibility is that descriptions, not trigger phrases, are now the thing you're actually authoring. A vaguely named tool ("Flow1", description "does the thing") is invisible to the planner in exactly the way a topic with no trigger phrases was invisible under classic — just for a different reason. Session 2 is largely about writing descriptions well.

## What's underneath the planner

Microsoft's own architecture guidance names five moving parts, and it's worth knowing them by name before you start building, since you'll be authoring four of them directly over the next several sessions.

| Component                | Role                                                    | You build this in                               |
| ------------------------ | ------------------------------------------------------- | ----------------------------------------------- |
| Orchestrator (planner)   | Turns a message or event into an ordered plan of steps  | Configured by your instructions, not hand-built |
| Knowledge layer          | Read-only retrieval — documents, sites, databases       | Group 3                                         |
| Tools and connectors     | Actions the agent can call, with defined inputs/outputs | Group 4                                         |
| Topics and inline agents | Reusable conversation logic, invoked by description     | Group 2                                         |
| Event triggers           | Start a plan without a user message at all              | Group 5 — this is autonomy                      |

## Deciding how much the agent gets to decide

This is the part of the architecture that connects straight back to my own essay. Giving an agent generative orchestration doesn't mean giving it unlimited judgment — Microsoft's guidance is explicit that production agents split decisions across three layers, and picking the right layer per action is a design decision you make, not something the platform infers for you.

{% hint style="info" %}
**Deterministic layer** — rule-based, scripted, no AI interpretation. For anything mission-critical or irreversible — processing a payment, deleting a record — you wrap it in a strictly authored flow the planner can't improvise around.
{% endhint %}

{% hint style="warning" %}
**Hybrid (intercept) layer** — the agent can draft or act, but a checkpoint exists: a manager reviews before it sends, or the agent must escalate past a set value. Medium-risk work — let the AI do the labor, keep a human at the gate.
{% endhint %}

{% hint style="success" %}
**AI orchestrator layer** — fully generative, within policy. Most Q\&A and simple multistep lookups live here — low-risk enough that the agent can decide and act without asking permission every time.
{% endhint %}

Put in my terms: this is Copilot Studio building in a gate between "the agent tried something" and "the agent is trusted to have tried it unsupervised." A library doesn't need this — a library can't do damage by being wrong out loud. The moment an agent can act, I inherit the same judgment call my essay makes about skill: repetition and failure are how competence gets proven, and you don't hand over the consequential decisions until it's been proven, watched, and bounded.

### Hook points, if you need to intervene mid-plan

Three triggers exist specifically for generative orchestration, letting you step into the planner's process rather than just configuring it upfront:

| Trigger                | Fires                                              | Typical use                                             |
| ---------------------- | -------------------------------------------------- | ------------------------------------------------------- |
| `OnKnowledgeRequested` | Right before a knowledge search runs               | Route the query to your own search index instead        |
| AI Response Generated  | After the draft reply is written, before it's sent | Fix formatting, swap in tracked links, redact something |
| On Plan Complete       | After every step finished and the answer went out  | Trigger a survey or an end-of-chat topic                |

## And the GitHub Copilot harness just doesn't ask

Here's the fact worth sitting with from Session 1.1: on the standard harness, generative vs. classic is a setting you control. On the GitHub Copilot harness, there's no such setting. Microsoft's own documentation states it plainly — that harness "uses this enhanced orchestration model for all agents," full stop. You don't author topics or branching logic there at all; you describe the agent in natural language and the reasoning runtime figures out the plan every time, with a fixed lifecycle of Create → Build → Test (Preview and Evaluate tabs) → Publish → Monitor.

{% hint style="success" %}
**Confirms a prediction from 1.1:** Session 1.1 guessed the GitHub Copilot harness has "no configurable orchestration mode — it's fixed to the enhanced reasoning runtime." Microsoft's docs confirm that directly. Worth noticing when a guess and the primary source line up, not just when they don't — it means the mental model from last session is holding.
{% endhint %}

## Worked example: same Northwind agent, one setting flipped

Picture the Northwind support agent with a return-policy topic, an order-status tool, and a live-agent-transfer tool.

{% columns %}
{% column width="50%" %}
**Classic orchestration**

A customer types "am I too late to return these boots" and it either matches your "Return Window" trigger phrases exactly, or it doesn't and falls back to knowledge, or it doesn't and asks the customer to rephrase.
{% endcolumn %}

{% column width="50%" %}
**Generative orchestration**

The same message gets read for intent. If the customer then adds "also, where's my other order," the planner runs both the return topic and the order-status tool in one turn and writes a single reply covering both — something classic orchestration structurally cannot do without you hand-authoring that combination in advance.
{% endcolumn %}
{% endcolumns %}

## Check your retrieval

Answer before you expand each one.

{% tabs %}
{% tab title="Question 1 of 4" icon="circle-question" %}
True or false: a brand-new standard-harness agent defaults to classic orchestration.

* True
* False — generative is the default for new agents
{% endtab %}

{% tab title="Answer" icon="unlock" %}
**False — generative is the default for new agents**
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Question 2 of 4" icon="circle-question" %}
Under classic orchestration, what decides which topic runs?

* The topic's description
* Matching the user's words to trigger phrases
* A vote among all available tools
{% endtab %}

{% tab title="Answer" icon="unlock" %}
**Matching the user's words to trigger phrases**
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Question 3 of 4" icon="circle-question" %}
A user asks two things in one message. Which orchestration mode can act on both without you pre-scripting that exact combination?

* Generative orchestration
* Classic orchestration
* Neither — always requires a dedicated top
{% endtab %}

{% tab title="Answer" icon="unlock" %}
**Generative orchestration**
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Question 4 of 4" icon="circle-question" %}
True or false: you can switch an agent built on the GitHub Copilot harness to classic orchestration if you prefer more predictability.

* True — it's the same Settings toggle as standard harness
* False — that harness has no orchestration toggle at all
{% endtab %}

{% tab title="Answer" icon="unlock" %}
**False — that harness has no orchestration toggle at all**
{% endtab %}
{% endtabs %}

### Match to a control layer

For each Northwind Outfitters action, which control layer should own the decision?\
Now, let's explore three sample cases:

<table><thead><tr><th width="439.60003662109375">Action</th><th>Suggested Layer</th></tr></thead><tbody><tr><td>"What's your return window for shoes?"</td><td>Al orchestrator layer</td></tr><tr><td>Issue a $640 refund to a customer's card</td><td>Hybrid (intercept) layer</td></tr><tr><td>Permanently delete a customer's account on request</td><td>Deterministic layer</td></tr></tbody></table>

## Reflection

<details>

<summary>My essay says skill is proven through repetition, failure, and watching whether something holds up. Why might an agent still belong in the hybrid layer for a task even after months of getting it right every time — what would have to be true before you'd move it to the fully AI orchestrator layer?</summary>

{% hint style="info" %}
**ONE REASONABLE ANSWER**\
Getting it right every time you've watched isn't the same guarantee as getting it right every\
time, full stop — the hybrid layer exists precisely because failure modes for high-consequence\
actions (a wrong refund, a wrongful deletion) are often rare and expensive rather than\
frequent and cheap, so a good track record doesn't retire the risk. Moving something to the\
fully Al orchestrator layer isn't really about the agent's skill improving further; it's about the\
cost of a rare failure dropping low enough — through smaller blast radius, reversibility, or a\
cap on the action's size — that unsupervised judgment becomes acceptable rather than about\
trusting the model more.
{% endhint %}

</details>

## Read next

The natural next primary source, since you're about to start authoring descriptions in Session 2: [Configure high-quality instructions for generative orchestration](https://learn.microsoft.com/microsoft-copilot-studio/guidance/generative-mode-guidance). It's the practical companion to the architecture covered here.

{% hint style="success" %}
**Key takeaway:** Orchestration is really two separate questions stacked on top of each other: how does the agent pick what to do (classic scripting vs. generative planning), and how much is it trusted to do without a human checkpoint (deterministic, hybrid, or fully AI). Session 2 starts on the first question; the second one you'll be answering for every action you ever give an agent.
{% endhint %}

## Sources

* [Orchestrate agent behavior with generative AI — Microsoft Learn](https://learn.microsoft.com/microsoft-copilot-studio/advanced-generative-actions)
* [Apply generative orchestration capabilities — Microsoft Learn](https://learn.microsoft.com/microsoft-copilot-studio/guidance/generative-orchestration)
* [Agents powered by GitHub Copilot Harness overview — Microsoft Learn](https://learn.microsoft.com/microsoft-copilot-studio/agents-experience/overview)
* [AI-based agent authoring overview — Microsoft Learn](https://learn.microsoft.com/microsoft-copilot-studio/nlu-gpt-overview)
* [What is AI Really? — my essay, the frame for this course](https://dyns.ntd.asia/power-dynamics/artificial-intelligence/what-is-ai-really)
