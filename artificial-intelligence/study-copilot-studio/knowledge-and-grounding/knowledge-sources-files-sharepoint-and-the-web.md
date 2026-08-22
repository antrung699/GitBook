---
description: >-
  Session 3.1 of 3 — Group 3: Knowledge & Grounding. Knowledge source
  fundamentals: files, SharePoint, and public websites.
icon: folder-open
---

# Knowledge Sources: Files, SharePoint, and the Web

2.3 let the agent read from "whatever's configured" without asking what that meant. This is where you configure it — three different ways to hand an agent real content, and the specific rules each one plays by once it's live.

{% hint style="info" %}
**Where this sits:** the first session of Group 3 — Knowledge & Grounding, sized at three sessions this pass. Genuinely new territory, not a Group 2 continuation: 3.1 covers what a knowledge source is and the three fundamental types; 3.2 goes into how grounding and citations actually work at answer time; 3.3 covers Azure AI Search and custom knowledge APIs.
{% endhint %}

## What a knowledge source actually is

A knowledge source is content the agent can search and quote from when it builds a generative answer — SharePoint sites, uploaded files, public websites, Dataverse tables, and a handful of other connectors. You attach them in two different places, and where you attach one changes its reach.

**Agent level.** Add knowledge from the agent's Overview or Knowledge page and it becomes available everywhere the agent answers generatively — by default that means Copilot Studio quietly wires it into the generative answers node inside the Conversational boosting system topic, the fallback that fires when no authored topic matches.

**Topic level.** Add knowledge from inside a specific generative answers node's properties instead, and it's scoped to that one node. Turn on **Search only selected sources** there and the node stops inheriting the agent's full knowledge list — it searches only what you explicitly picked, even overriding trigger conditions that would normally limit when a source applies.

One rule holds for every source you add, at either level: it needs a unique name and a real description, not a placeholder. That description isn't documentation for future-you — generative orchestration reads it to decide when this particular source is even worth searching, so a vague one quietly makes the agent worse at knowing when to reach for it.

## Three fundamentals, side by side

Copilot Studio supports a longer list than this — Dataverse, Azure AI Search, connector-based enterprise data — but three types cover most of what a new agent needs on day one, and they're different enough from each other to be worth learning as a set.

<table><thead><tr><th width="157.88671875">Type</th><th width="194.8359375">Where the content lives</th><th>Who can see what</th><th width="159.70703125">Limit in generative mode</th></tr></thead><tbody><tr><td>Public website</td><td>External — the live internet</td><td>No authentication; whatever Bing can index</td><td>25 websites</td></tr><tr><td>Uploaded files</td><td>Copied into Dataverse at upload time</td><td>No authentication — visible to anyone chatting with the agent</td><td>All uploaded documents</td></tr><tr><td>SharePoint</td><td>Stays in SharePoint; queried live via Microsoft Graph</td><td>The signed-in user's own Microsoft Entra ID permissions</td><td>25 URLs</td></tr></tbody></table>

That middle column is the one to sit with. Public websites and uploaded files don't check who's asking — a website is public by definition, and an uploaded file's contents are available to everyone the agent talks to, "regardless of file permissions or access controls," in Microsoft's own words. SharePoint is the odd one out: it re-checks the actual signed-in user's access on every query. That single difference is usually what decides which type you reach for.

## Public websites — the rules that catch people out

Adding one is simple: open Add knowledge, choose Public websites, paste a URL, optionally edit the name and description, and add it. What trips people up is what Copilot Studio will and won't actually crawl once that URL is live.

**Depth and domain rules**

* A URL can go two levels deep at most. `fabrikam.com/engines/rotary` works; `fabrikam.com/engines/rotary/dual-shaft` doesn't — you'd need to register that deeper path as its own source.
* Registering a URL pulls in its subpaths automatically, but not unrelated sections of the same domain — pointing at `/engines/rotary` doesn't also cover `/tools`.
* The `www.` prefix matters. Register `www.fabrikam.com` and content on `news.fabrikam.com` is out of scope, because `news.` is a subdomain the registered URL never mentioned. Register the bare `fabrikam.com` instead, and both `www.` and other subdomains are in scope.
* If a URL redirects to a different top-level site, neither the original nor the redirect target gets used.

**What's simply not eligible**

Anything that requires sign-in is out — Microsoft's own examples are a wiki and a SharePoint site, both rejected for exactly that reason. Search engine URLs like `bing.com` are excluded outright, since they don't return anything a customer could act on. Forums and social networks are technically allowed but flagged as a real risk: open, unmoderated community content is more likely to produce answers Copilot Studio's own safety checks then reject.

You can also swap a static URL for a variable and let it resolve at runtime — useful for scoping a single knowledge source to a product line or a locale based on something the conversation already knows, rather than building a separate source for every variant.

## SharePoint — two options wearing the same name

Open Add knowledge and you'll see "SharePoint" twice — once in the file-upload section, once as its own featured option. They solve related but genuinely different problems, and the difference is worth being precise about before you build anything on top of either.

**SharePoint under file upload** copies specific files or folders into Dataverse and keeps them synchronized — edit the source file in SharePoint and the agent's copy updates automatically, unlike a plain uploaded file, which stays frozen until someone re-uploads it. It supports Word, PowerPoint, PDF, and Excel, up to 512 MB, and PDFs added this way get page-level citations so a user can jump straight to the cited page. It does check the user's SharePoint credentials before responding — but document libraries currently aren't supported through this path.

**Full SharePoint integration** is the featured "SharePoint" option — a live connection to a site or list URL via Microsoft Graph, not a copy. It searches only the registered URL and its subpaths, respects sensitivity labels for permission trimming, and if the signed-in user lacks even Read access, the agent returns **"no response"** rather than an error or a hint that the content exists at all. One real limitation: it can't extract or ground on encrypted content — Double Key Encryption, sensitivity-label encryption, and password-protected files all show as "Ready" in the UI but silently return no response regardless of the user's actual permissions.

Use the file-upload version when you want specific documents kept current with minimal setup. Use the full integration when the source is an entire site or list, access needs to track real SharePoint permissions per user, or you need query filters — Copilot Studio supports scoping a SharePoint source by title, author, or modified date, which is the closest thing to a search query you can hand it without leaving the no-code surface.

## Uploaded files — what's supported, and the one warning worth repeating

Individual document upload is the fastest way to get an agent answering from real content: drag a file into Add knowledge, name it, describe it, done. Supported formats cover the obvious office types — Word, Excel, PowerPoint, PDF — plus plain text, Markdown, HTML, CSV, XML, JSON, YAML, RTF, EPUB, LaTeX, OpenDocument, and Apple's iWork formats. Even annotated images embedded inside a PDF are searchable, through the image's alt-text description.

**Limits and exclusions**

* 512 MB per file, up to 500 files per agent.
* Standalone images, video, audio, and executables aren't supported — only images embedded in a PDF.
* Encrypted or password-protected files aren't supported at all.
* Uploading requires Dataverse search to be turned on for the environment — if the option is missing, that's usually why.

The warning worth repeating: an uploaded file's content is available to _anyone_ chatting with the agent, with no permission check of any kind. That's fine for a public FAQ. It's the wrong tool the moment the document contains anything you wouldn't want an anonymous user to see — that content belongs in SharePoint's full integration, not in an upload.

## Worked example: knowledge for Northwind Outfitters

Three real questions a Northwind customer-support agent needs to answer, and which source type actually fits each one.

<table><thead><tr><th width="255.453125">Content</th><th width="166.078125">Source type</th><th>Why</th></tr></thead><tbody><tr><td>Public shipping &#x26; returns FAQ, already live on northwindoutfitters.com</td><td>Public website</td><td>Already public, already indexed — registering the URL is faster than duplicating it as a file, and it stays current automatically.</td></tr><tr><td>A one-off "Holiday Returns 2026" policy PDF, not yet published anywhere</td><td>Uploaded file</td><td>Nothing sensitive in it, no existing URL to point at — a straight upload is the least setup for a document this disposable.</td></tr><tr><td>Internal product spec sheets, used later by the product-support subagent</td><td>SharePoint (full integration)</td><td>Internal-only content — needs the per-user permission check that only the full SharePoint option provides, not an upload that anyone chatting with the agent could read.</td></tr></tbody></table>

Notice what didn't change: none of these three needs Azure AI Search or a custom API. That's 3.3's territory — for genuinely large document collections or knowledge that lives outside Microsoft's ecosystem entirely, not for "we have a PDF and a SharePoint site," which is most agents most of the time.

## Check your retrieval

{% tabs %}
{% tab title="Question 1 of 4" icon="circle-question" %}
You register `www.fabrikam.com/engines/rotary` as a public website knowledge source. Which of these is in scope for the agent to use?

a) `www.fabrikam.com/tools`&#x20;

b) `www.fabrikam.com/engines/rotary/dual-shaft`&#x20;

c) `news.fabrikam.com`&#x20;

d) None of the above
{% endtab %}

{% tab title="Answer" icon="unlock" %}
**b.** A registered URL automatically covers its own subpaths, and one level deeper than the registered path is within the two-level depth limit. `/tools` is a sibling path, not a subpath of `/engines/rotary`, so it's excluded — and `news.fabrikam.com` is a different subdomain than the registered `www.` one.
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Question 2 of 4" icon="circle-question" %}
A customer without SharePoint access asks a question that would be answered by a full-integration SharePoint knowledge source. What does the agent do?

a) Returns an error explaining the permission problem&#x20;

b) Answers anyway, using the model's general knowledge&#x20;

c) Responds as though it found no information at all
{% endtab %}

{% tab title="Answer" icon="unlock" %}
**c.** The agent surfaces "no response" — it doesn't confirm or deny that matching content exists, and it doesn't explain why. This is deliberate: revealing "there's an answer here, you're just not allowed to see it" would itself leak information.
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Question 3 of 4" icon="circle-question" %}
You have an internal salary-band PDF. Which knowledge source type should it never go into, given what you now know about permissions?

a) Uploaded file&#x20;

b) SharePoint (full integration)
{% endtab %}

{% tab title="Answer" icon="unlock" %}
**a.** Uploaded file content has no permission check — it's visible to anyone chatting with the agent, per Microsoft's own documentation. Anything that shouldn't be universally visible belongs in the full SharePoint integration, where per-user access is actually enforced.
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Question 4 of 4" icon="circle-question" %}
You add a knowledge source directly inside a generative answers node's properties and turn on "Search only selected sources." What happens to the agent's other, agent-level knowledge sources for that node?

a) They're still searched, alongside the node-level one&#x20;

b) They're not searched by this node — the node-level selection replaces them entirely
{% endtab %}

{% tab title="Answer" icon="unlock" %}
**b.** "Search only selected sources" replaces the agent's full set for that node rather than adding to it — and it doesn't fall back to the agent-level sources if the selected ones come up empty.
{% endtab %}
{% endtabs %}

## Reflection

<details>

<summary>Reflection: why "no response" instead of an honest permission error, for SharePoint content a user can't access?</summary>

{% hint style="info" %}
**ONE REASONABLE ANSWER**&#x20;

A permission error that names the blocked content ("you don't have access to the Q3 salary review") confirms the content exists and roughly what it's about — that's a real information leak even without revealing the content itself. Answering "no response" the same way the agent would for a genuinely empty search keeps the two cases indistinguishable from the outside. The cost is a worse debugging experience for the agent's maker, who now has to check permissions manually rather than trusting an error message — a trade nearly every enterprise system with row-level security makes the same way.
{% endhint %}

</details>

{% hint style="success" %}
**Key takeaway:** every knowledge source type carries its own access model, not just its own setup screen — picking one is a security decision wearing a UI decision's clothes.
{% endhint %}

## Read next

The single best next read: [Knowledge sources summary](https://learn.microsoft.com/microsoft-copilot-studio/knowledge-copilot-studio). It's the hub page this session drew its comparison table from, and it's also where 3.2 picks up — the same article covers citations, official sources, and the allow-ungrounded-responses setting this session deliberately left for next time.

## Primary sources verified this session

1. [Knowledge sources summary](https://learn.microsoft.com/microsoft-copilot-studio/knowledge-copilot-studio)
2. [Add a public website as a knowledge source](https://learn.microsoft.com/microsoft-copilot-studio/knowledge-add-public-website)
3. [Add SharePoint as a knowledge source](https://learn.microsoft.com/microsoft-copilot-studio/knowledge-add-sharepoint)
4. [Upload files as a knowledge source](https://learn.microsoft.com/microsoft-copilot-studio/knowledge-add-file-upload)
5. [Add knowledge to an agent](https://learn.microsoft.com/microsoft-copilot-studio/knowledge-add-existing-copilot)
6. [Unstructured data as a knowledge source](https://learn.microsoft.com/microsoft-copilot-studio/knowledge-unstructured-data) (FAQ: the two SharePoint options)

The "anyone chatting with the agent can see uploaded file content" warning is stated explicitly on the page for uploading files inside a generative answers node, and consistently (if less bluntly) on the agent-level upload page used for this lesson — both describe the same underlying, no-permission-check behavior, not two different products.
