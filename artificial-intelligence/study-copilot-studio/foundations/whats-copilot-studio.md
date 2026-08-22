---
description: >-
  Session 1.1 — what the platform actually is, the three harnesses underneath
  it, and how they map to the knowledge-vs-skill frame from "What Is AI,
  Really?"
icon: robot
---

# What's Copilot Studio?

{% hint style="info" %}
**Group 1 · Session 1.1** of the Copilot Studio course. Full plan on the [Mission](https://dyns.ntd.asia/power-dynamics/artificial-intelligence/study-copilot-studio/mission) page.
{% endhint %}

## Starting from my own frame

Your piece on AI put it plainly: knowledge by itself doesn't make something human-like, it makes it a library. Skill is what sits between wanting something and having it, and skill only gets built through repetition, failure, and watching whether the thing you made actually holds up.

That distinction turns out to be the most useful lens for this whole course, because Copilot Studio is not one tool that does one thing. It's a studio that can build a library — an agent that answers questions accurately from documents — or it can build something closer to skill: an agent that takes a goal, works through the steps, hits a wall, and tries something else. Which one you get depends on a choice you make early, and most tutorials skip past it.

## The plain definition

Copilot Studio is a low-code studio — a single web app at `copilotstudio.microsoft.com` — for building and managing AI-powered agents and workflows, connecting them to your organization's data and systems, and publishing them to the channels people already use: Teams, websites, Microsoft 365 Copilot, mobile apps.

Inside it you can build three kinds of things, and they can call each other:

<table><thead><tr><th width="147.421875">Building block</th><th>What it is</th></tr></thead><tbody><tr><td><strong>Agent</strong></td><td>An AI assistant that handles a conversation and completes tasks. It follows the instructions you give it, draws on the knowledge you connect, and uses tools to act — reasoning about what the user needs and deciding the next step.</td></tr><tr><td><strong>Workflow</strong></td><td>A drag-and-drop automation. Each step can reason and act, mixing agents, tools, and plain logic in one flow — the predictability of automation with some AI flexibility layered in.</td></tr><tr><td><strong>Agent flow</strong></td><td>Copilot Studio's native version of a Power Automate flow. Runs standalone, or gets attached to an agent as a tool the agent can call and get a result back from.</td></tr></tbody></table>

## The part that actually decides how your agent behaves

Everything you build runs on what Microsoft calls a **harness** — the runtime sitting between your design and the underlying model. It decides when to call the model, what to hand it, how to read what comes back, and which tools to trigger. The harness you pick changes how your agent reasons, how much it can do in one turn, what it can do out of the box, and how it's billed. There are three.

<table><thead><tr><th width="147.171875">Harness</th><th width="182.8359375">Best for</th><th width="224.8359375">How it works</th><th>Maps to</th></tr></thead><tbody><tr><td><strong>Standard</strong></td><td>Rule-based, structured conversations</td><td>Matches requests to the topics you define; falls back to generative answers from connected knowledge</td><td>Mostly the library: retrieves and answers</td></tr><tr><td><strong>GitHub Copilot</strong></td><td>Reasoning-heavy, multistep processes</td><td>Breaks a goal into steps, calls tools across connectors and other agents, adjusts when a step fails instead of stalling</td><td>The doing: iterates, recovers, adapts</td></tr><tr><td><strong>Copilot chat</strong></td><td>Extending Microsoft 365 Copilot Chat</td><td>Grounds M365 Copilot Chat answers in your enterprise knowledge, published internally only</td><td>A library card scoped to one building</td></tr></tbody></table>

Notice the middle one is the only harness Microsoft itself describes with the phrase "agentic reasoning." That's not a coincidence — it's the harness built around your second question, the one about doing rather than knowing.

{% hint style="warning" %}
**If you've read older Copilot Studio material:** tutorials from before this rebrand talk about "copilots" instead of "agents," and describe a single choice between "classic" and "generative" orchestration. That framing still exists, but it now lives one level down — inside the standard harness specifically, as how that harness decides which topic or knowledge source to use. The bigger, earlier decision Microsoft wants you making now is which of the three harnesses you're building on at all. This was checked against the current Copilot Studio documentation directly rather than relied on from memory, since platform detail like this goes stale fast.
{% endhint %}

## Worked example: the same request, two harnesses

Your course scenario is Northwind Outfitters, a retailer whose agent handles order status, FAQs, and returns. Here's the same customer, two different requests, and why they land on different harnesses.

{% columns %}
{% column width="50%" %}
**Library question — standard harness**

"What's your return policy for worn shoes?" This matches a topic or gets answered straight from a connected FAQ document. No steps, no judgment calls, the same correct answer every time. Sessions 2 through 4 of this course build exactly this.
{% endcolumn %}

{% column width="50%" %}
**Doing question — GitHub Copilot harness**

"My order never arrived. Can you check what happened, and if it's lost, start a replacement and email me once it ships?" That's a lookup, a branch, an action, and a follow-through — four steps where the third depends on what the first one finds. This is what Group 5 and 6 build toward.
{% endcolumn %}
{% endcolumns %}

## Check your retrieval

Answer before you look anything up. Getting one wrong is more useful right now than getting it right.

{% tabs %}
{% tab title="Question 1 of 4" icon="circle-question" %}
An internal IT help-desk agent that must give the same correct answer to "how do I reset my VPN password" every single time, with zero surprises.

* GitHub Copilot harness
* Standard harness
* Copilot chat harness
{% endtab %}

{% tab title="Answer" icon="unlock" %}
Standard harness
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Question 2 of 4" icon="circle-question" %}
An agent that reads incoming invoices, matches each one to a purchase order, and routes anything that doesn't match to the right approver — adjusting when a match is ambiguous.

* GitHub Copilot harness
* Standard harness
* Copilot chat harness
{% endtab %}

{% tab title="Answer" icon="unlock" %}
GitHub Copilot harness
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Question 3 of 4" icon="circle-question" %}
An agent that only answers employee questions from SharePoint policy documents, reachable exclusively inside Microsoft 365 Copilot Chat.

* GitHub Copilot harness
* Standard harness
* Copilot chat harness
{% endtab %}

{% tab title="Answer" icon="unlock" %}
Copilot chat harness
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Question 4 of 4" icon="circle-question" %}
True or false: every agent in Copilot Studio uses the same reasoning engine underneath, no matter what you build.

* True
* False - the harness you choose is that engine
{% endtab %}

{% tab title="Answer" icon="unlock" %}
False - the harness you choose is that engine
{% endtab %}
{% endtabs %}

## Reflection

<details>

<summary>In your own knowledge-versus-skill frame: which harness is the library, which is the skill - and where does the Copilot chat harness actually sit? It doesn't map cleanly to either.</summary>

{% hint style="info" %}
**ONE REASONABLE ANSWER**\
Standard harness is the library - it retrieves and answers, reliably, without independent judgment. GitHub Copilot harness is the skill - it takes a goal, tries steps, and adapts when one fails, which is the repetition-and-failure loop your essay describes. Copilot chat harness doesn't sit between them; it's arguably an even purer library than the standard harness, because Microsoft built it to optimize for one job only - connecting a person to information inside Microsoft 365 Copilot Chat - with no ambition to complete multistep tasks at all.
{% endhint %}

</details>

## Read next

The single best next read is the primary source this lesson is built on: Microsoft's own [Choose a harness](https://learn.microsoft.com/microsoft-copilot-studio/harnesses-overview) guide. It has the full comparison table — billing, file handling, error recovery, publishing — for all three harnesses side by side.

{% hint style="success" %}
**Key takeaway:** Copilot Studio isn't one product; it's one studio and three harnesses — and the harness you pick decides whether you're building a better library or something that can actually act. Default to the simplest harness that gets the job done; save the reasoning-heavy one for when the task genuinely needs it.
{% endhint %}

## Sources

* [Copilot Studio overview — Microsoft Learn](https://learn.microsoft.com/microsoft-copilot-studio/fundamentals-what-is-copilot-studio)
* [Choose a harness — Microsoft Learn](https://learn.microsoft.com/microsoft-copilot-studio/harnesses-overview)
* [Agents overview — Microsoft Learn](https://learn.microsoft.com/microsoft-copilot-studio/agents-overview)
* [What is AI Really? — the frame for this course](https://dyns.ntd.asia/power-dynamics/artificial-intelligence/what-is-ai-really)
