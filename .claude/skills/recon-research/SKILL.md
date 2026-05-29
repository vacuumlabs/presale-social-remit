---
name: recon-research
version: "2.4"
description: "Multi-agent research orchestrator with scout-first design, composable modes, provenance/review metadata, and research-folder governance. The research manager scouts the landscape personally, designs a plan mixing Web Research, Deep Knowledge, and Dialectic, then closes the run with README metadata and promotion targets. Use for research that needs depth: multiple sources, synthesis, perspective, or strategic reasoning. NOT for quick lookups."
argument-hint: <research question or topic>
---

# /recon-research — Multi-Agent Research Orchestrator

One skill, three composable building blocks, one research manager who scouts before planning.

## Building Blocks

These are not separate modes — they are building blocks the research manager combines in a single plan.

| Block | What it does | When to use it |
|-------|-------------|----------------|
| **Web Research** | Agents search the web, follow links, gather current data | Facts, markets, trends, products, recent events, social listening |
| **Deep Knowledge** | Agents write from LLM training knowledge with scholarly citations | Philosophy, theology, established science, intellectual history, topics where books > websites |
| **Dialectic** | A single agent inhabits 2-4 perspectives and stages a structured debate | Strategic tensions, tradeoffs, assumption stress-testing, values questions, anything with no factual "right answer" |

A research plan can use any combination. Examples:
- **Market decision:** 2 Web Research agents (market landscape + competitor deep-dive) → 1 Dialectic agent arguing build-vs-buy using those facts
- **Theological question:** 2 Deep Knowledge agents (patristic tradition + phenomenological lens) → 1 Dialectic with 3 voices debating the lived implications
- **Product strategy:** 1 Web Research agent (social listening + user complaints) + 1 Deep Knowledge agent (relevant theory) → Dialectic on strategic direction → Navigator reviews the whole thing

The research manager designs the plan. The building blocks are tools, not pipelines.

---

## Phase 0: Problem Space Check

Before anything else, understand what the user actually needs. This prevents the most common research failure: well-researched answers to the wrong question.

Ask one question at a time:

1. **"What decision will this research inform?"** — Research without a decision context produces interesting-but-useless output.
2. **"What do you already believe about this space, and what would change your mind?"** — Surfaces assumptions to test, not confirm.
3. **"Who will read this and what do they care about?"** — A client deck needs different evidence than an internal memo.

Only proceed once you understand the decision context.

---

## Phase 0.5: Scout

The research manager does a personal reconnaissance before designing the plan. No agents, no files — just 3-5 searches and a quick read of key sources to form a mental model of the landscape.

**Protocol:**
1. Do 3-5 web searches (or draw on training knowledge if the topic suits it)
2. Skim 2-3 of the most promising sources
3. Check the user's existing knowledge base — are there relevant notes, docs, or prior work?
4. Form a preliminary picture: what's the shape of this space? Where is the depth? Where are the gaps? Where would a dialectic add value?

**Share the scout findings with the user:**

```
## Scout Report

**What I found in my quick scan:**
- [2-3 key observations about the landscape]
- [Where the depth seems to be]
- [What's surprisingly thin or contested]

**Existing knowledge:** [relevant notes, or "nothing directly on this"]

**My initial read:** [1-2 sentences on what kind of research plan this needs — which building blocks, why]
```

This is what makes the research design evidence-based rather than pattern-matching. It also lets the user course-correct before agents burn tokens.

---

## Phase 1: Research Design

Based on the scout AND Phase 0 answers, the research manager designs a composite plan. This is the strategic heart of the skill.

### 1.0 Build a context brief for agents

Research agents start cold. Build a short context brief that gets injected into every agent prompt.

**What to include (only what's relevant):**
1. **From user context** — which initiative or project does this serve? What's the deadline?
2. **From prior conversations or project docs** — stakeholders, constraints, what's already decided
3. **From existing knowledge base** — relevant notes or documents the user already has (so agents build on existing thinking)
4. **From Phase 0** — decision context, assumptions to test, audience
5. **From the scout** — what the manager already learned, so agents don't duplicate the scouting work

Keep it under 300 words.

### 1.1 Design the workstreams

**Principles for composing a good research plan:**

- **Match the building block to the question type.** Factual unknowns need Web Research or Deep Knowledge. Strategic tensions need Dialectic. Most real questions have both — plan accordingly.
- **Sequence matters.** Factual research before dialectic is usually better — the dialectic is richer when grounded in evidence. But sometimes a dialectic-first approach surfaces the right questions to research.
- **One agent per distinct knowledge domain.** Don't mix market analysis with technical architecture in one agent.
- **Always include the human dimension.** Technology research without people context is useless. At least one workstream should cover organizational, user, or cultural factors.
- **Push toward unlikely sources.** If all agents would search the first page of Google, the plan isn't good enough. Direct at least one agent toward non-obvious sources (see Unlikely Places section below).
- **Dialectic is a layer, not an alternative.** Consider adding a dialectic workstream to any research where there's genuine strategic uncertainty — it's not just for "philosophical" questions.

Each workstream needs:
- A clear, non-overlapping scope
- Which building block it uses (Web Research / Deep Knowledge / Dialectic)
- Which **model tier** to use (see below)
- 3-6 specific sections to write
- What it depends on (e.g., "runs after Agent 1 and 2 complete, uses their findings")

### 1.1.1 Model routing

Not every workstream needs the strongest model. Assign a tier to each workstream based on the cognitive demand of the task:

| Tier | Task type | Current example | When to use |
|------|-----------|----------------|-------------|
| **Tier 1: Search & Extract** | Web Research agents doing search-and-summarize, social listening, data gathering | haiku | Factual workstreams where the task is "find and write," not "analyze and connect" |
| **Tier 2: Analyze & Synthesize** | Deep Knowledge, Dialectic, Navigator | sonnet | Workstreams requiring cross-source reasoning, perspective-taking, gap detection |
| **Tier 3: Integrate & Judge** | Final synthesis, complex dialectics with many input files | opus | Only when the task requires integrating all workstream outputs and making judgment calls across the full evidence base |

**Principles:**
- Default to Tier 1 for Web Research agents. Upgrade to Tier 2 only if the workstream requires genuine analysis, not just search-and-write.
- Navigator and Dialectic are almost always Tier 2 — they need reasoning, not just retrieval.
- Tier 3 is reserved for final synthesis or when the research manager does integration work in the main thread.
- The model examples (haiku, sonnet, opus) are current as of the skill version. Update them as models evolve — the tiers are the durable concept.
- When presenting the research plan, include the model tier and example for each workstream so the user can see the cost/quality tradeoff.

### 1.2 Present the plan

```
## Research Plan: [Topic]

**Decision this informs:** [from Phase 0]
**Key assumptions to test:** [from Phase 0]
**Audience:** [from Phase 0]
**Output directory:** [path]

### Workstream 1: [Name] — Web Research
**Scope:** [1-2 sentences]
**Model:** Tier 1 (haiku)
**Sections:** [list]
**Output file:** [path]

### Workstream 2: [Name] — Deep Knowledge
**Scope:** [1-2 sentences]
**Model:** Tier 2 (sonnet)
**Sections:** [list]
**Output file:** [path]
**Depends on:** nothing (runs in parallel with Workstream 1)

### Workstream 3: [Name] — Dialectic
**Scope:** [the tension to debate]
**Perspectives:** [2-4 named perspectives]
**Model:** Tier 2 (sonnet)
**Output file:** [path]
**Depends on:** Workstreams 1-2 (uses their findings)

### Navigator
**Runs after:** all workstreams complete
**Purpose:** gap analysis, contradiction detection, follow-up dispatch

### Synthesis
**Runs after:** navigator review
**Output file:** [path]/synthesis.md

### Research folder README
**Created/updated:** at the start and close of the run
**Output file:** [path]/README.md
```

### 1.3 Wait for user approval before launching

---

## Phase 2: Launch & Monitor

Before launching agents, create or update `[output directory]/README.md` with the research title, decision context, status `Active`, planned outputs, and blank promotion sections. This keeps the research folder navigable even if the run is interrupted.

The README must include provenance metadata near the top:

```markdown
> Provenance: AI/agent-generated research artifact.
> Authority: raw material.
> Review status: unreviewed.
```

### Web tool availability check

Before launching, test whether WebSearch/WebFetch are available with a single search. If denied:
1. Tell the user immediately
2. Switch web-dependent agents to Deep Knowledge mode
3. Hold social listening agents — ask the user whether to grant permissions or skip

### Agent prompts

Launch research agents in parallel using the current runtime's equivalent of background subagents. In Claude Code this is `Agent` with `run_in_background: true`, `subagent_type: "general-purpose"`, and the `model` parameter set to the tier assigned in the research plan. In Codex or another runtime, preserve the workstream scope, model tier, file-writing contract, and monitoring cadence using the available agent/delegation tools. If background agents are unavailable, tell Rudolf and either run the work locally or propose a lighter plan. Each prompt MUST include:

1. The **context brief** from Phase 1.0
2. The **source mode declaration** (see below)
3. Their specific scope and section list
4. The **research protocol** (see below)
5. The **provenance header requirement** (see below)
6. The exact file path to write to (use `~` paths)
7. For Dialectic agents: the **dialectic protocol** (see below)

### Monitoring

Check progress proactively:

| Timing | Action |
|--------|--------|
| ~2 min | Verify agents started writing (flag empty files) |
| ~5 min | Report section progress and line counts |
| ~8 min | Flag stuck agents (no progress between checks) |
| Every 5 min after | Continue until all complete |

Use `wc -l` for quick checks. If an agent shows no progress between two consecutive checks, it's stuck — stop it, read its output, relaunch a new agent that picks up where it left off.

---

## Phase 3: Navigator Review

The navigator is the quality layer. Launch a single navigator agent (foreground) once all research agents complete.

Its job is NOT to summarize — it's to think at a higher level about what was found and what's missing:

1. **Gaps** — unanswered questions, low-confidence sections, claims with only one source, Phase 0 assumptions that were confirmed rather than tested
2. **Contradictions** — where agents disagree (this is gold, not a problem). Flag with quotes, don't resolve.
3. **Blind spots** — missing perspectives (only vendor view? only tech view? no end-user voice?). Were unlikely sources actually searched?
4. **One-sidedness** — sections that read like marketing rather than analysis. Scan for clusters of `[vendor source]` or `[single source]` flags — these indicate areas where the evidence base is thin.
5. **Cross-workstream citation deduplication** — flag claims that appear in multiple workstreams citing the same original source. This creates an illusion of independent confirmation when there is none.
6. **Follow-up dispatch** — 0-3 targeted follow-up tasks, each a specific answerable question with a reason why it matters

After navigator completes: present follow-ups to the user, launch approved ones, monitor them.

---

## Phase 4: Synthesis

Launch the synthesis agent (foreground). It reads ALL outputs and produces a single document organized by insight, not by agent:

- **Executive summary** — 3-5 bullets, each with a "so what" implication
- **Key findings by theme** — cross-cutting, not per-workstream
- **Contradictions and open tensions** — presented honestly
- **Confidence map** — well-supported vs. single-sourced vs. speculation
- **Assumptions tested** — what Phase 0 assumptions got right and wrong
- **Recommended next steps** — framed as "given what we found"

Report completion to the user with a brief summary.

---

## Phase 4.5: Research Folder Close-out

Before reporting the run as complete, update `[output directory]/README.md`. Research folders are the lab bench, not the permanent knowledge home.

The README must include:

1. **Decision this informed** — the question or decision that triggered the research
2. **Provenance and authority** — default `AI/agent-generated research artifact` + `raw material`
3. **Review status** — unreviewed / reviewed_by_rudolf / agreed_with_team / client_ready
4. **Status** — Active / Complete / Paused / Superseded
5. **Key outputs** — links to synthesis, navigator review, dialectics, and agent files
6. **Durable insights promoted** — links to notes, skills, or backlog entries where the lasting insight now lives
7. **Still unpromoted** — checklist of insights that should become Knowledge Garden notes, Active Project updates, Practices, Library notes, or Operations improvements
8. **Review date** — concrete date or event trigger

Promotion rules:

- **Concepts and frameworks** -> `03_Knowledge_garden/`
- **Project-specific implications** -> `05_Active_projects/`
- **Reusable habits or practices** -> `06_Practices/`
- **External-source summaries** -> `08_Library/`
- **Operational lessons for Klara or agents** -> `11_Operations/ideas-backlog.md` or the relevant skill

Do not silently promote insights into the contemplative vault unless Rudolf explicitly asked for that. If promotion is warranted, list the proposed destinations and ask for confirmation.

When promoting into a project repo, use repo frontmatter provenance:

```yaml
provenance: agent_generated
review_status: unreviewed
```

When promoting into the personal vault, use visible provenance blockquotes and ask what part has become Rudolf's own thought before using `Rudolf insight, AI-shaped synthesis`.

---

## Dialectic Protocol

When a workstream uses the Dialectic building block, use this protocol. A single agent inhabits multiple perspectives sequentially — NOT parallel agents to a shared file.

### Step 1: Frame the debate

Define before launching:
- **The central question** — restated as a debatable proposition
- **2-4 perspectives** — each with a name, tradition, and core stance. Not just pro/con — can be complementary lenses, different traditions, or different stakeholders. Three often beats two (breaks binary thinking).
- **Ground rules** — what all perspectives agree on
- **What would change the user's mind** — from Phase 0

Get approval if running as a standalone research. If dialectic is part of a larger plan already approved, proceed.

### Step 2: Opening arguments (400-700 words each)

Each voice must:
- State its core claim clearly
- Present its 3 strongest reasons
- Describe what the answer looks like in practice from this perspective
- Acknowledge the strongest point the other perspectives are likely to make

### Step 3: Rebuttals (300-500 words each)

Each voice must:
- Directly address the others' strongest points
- Concede where they're right
- Introduce new evidence or reasoning not in the opening
- Go somewhere new — don't repeat the opening

### Sycophancy guardrails

LLM agents converge to agreement faster than humans — this is a documented failure mode (arxiv 2509.05396, 2509.23055). Without guardrails, debate produces confident agreement, not insight. Include these rules in every dialectic agent prompt:

1. **No agreement without evidence.** A voice may only concede a point if it cites a specific piece of evidence that changed its position. "You make a good point" without a citation is not a concession — it's sycophancy.
2. **Each rebuttal must introduce irreducible novelty.** At least one argument per rebuttal that the other voices cannot easily absorb into their position. If all rebuttals end up agreeing, the debate has failed.
3. **The synthesis MUST list unresolved tensions.** A "Remaining Disagreements" section is mandatory and must be non-empty. If the voices agree on everything, the debate was either too narrow or the agent flattened genuine differences.
4. **Convergence is not a success signal.** Do NOT stop the debate because voices agree. Stop when arguments are exhausted — when each voice has said its strongest thing and the others have responded to it.
5. **When a dialectic follows factual workstreams**, each voice should argue primarily from a specific subset of the evidence, not the full picture. Assign evidence sources in the prompt: "Voice A, draw primarily from workstreams 1-2. Voice B, draw primarily from workstream 3." The voices may reference other evidence to rebut, but their core arguments should come from their assigned base.

### Step 4: Synthesis

The agent shifts to a neutral observer voice:
1. **The real crux** — the fundamental tension, named precisely
2. **Hidden agreement** — where perspectives agree more than they think
3. **Remaining disagreements** — tensions that were NOT resolved, stated honestly. This section must be non-empty.
4. **Conditional decision map** — "If X, then Perspective A serves you best. If Y, then B."
5. **Reasoning errors** — unsupported claims or blind spots from any side
6. **What's missing** — what additional information would resolve uncertainty
7. **A clear recommendation** — not "it depends" but "given what we know, the stronger position is X because Y, with the caveat that Z could change this"

### Step 5: Practical Guide (when applicable)

When the dialectic touches on practice, add a "Map for the Practitioner":
- **What to do** — specific practices with actual instructions
- **What to expect** — including difficulty and doubt
- **What NOT to do** — common mistakes, one from each perspective
- **Signs of progress** — how to know something is shifting

This was the most valued output in field testing. Include it whenever the dialectic has practical implications.

### Voice authenticity

Write in each voice AUTHENTICALLY. Each should sound like someone who has lived their tradition — not a cardboard representative of a position. A contemplative should sound like someone who prays. A strategist should sound like someone who has made real bets.

### Continuation dialectics

The same voices can reconvene on a follow-up question. When launching a continuation:
1. Reference the previous dialectic — the agent reads it first
2. Voices reference what was said before ("As I argued last time...")
3. Ground rules may evolve based on what the first exchange established

Continuations produce deeper dialogue because voices have shared history.

---

## Research Protocol

Copy this verbatim into every Web Research and Deep Knowledge agent prompt:

```
RESEARCH PROTOCOL — READ THIS BEFORE DOING ANYTHING:

The ONLY acceptable pattern is: Search -> Edit -> Search -> Edit.
NEVER: Search -> Search. NO EXCEPTIONS.

You MUST Edit your output file after EVERY search or web fetch.
Two searches without an Edit means you are stuck.

Work through your sections IN ORDER. For each section:
1. Do ONE search (or write from knowledge in Deep Knowledge mode)
2. IMMEDIATELY Edit the file to write what you learned
3. Search again if needed
4. IMMEDIATELY Edit again with additional findings
5. Only move to the next section after the current one has real content

If a web fetch returns a 403 error, write what you have, THEN try another URL.

CONFIDENCE LINE: After each section, add:
"Confidence: [high/medium/low] — [brief reason]"
The navigator uses these to decide where follow-up is needed.

SOURCE QUALITY FLAGS: Tag individual claims inline when the source is weak:
- [vendor source] — claim comes from a company's own marketing or product page
- [single source] — claim supported by only one source, not independently verified
- [undated] — source has no publication date or is undated web content
- [blog/opinion] — source is a blog post or opinion piece, not research or reporting
These flags are NOT reasons to exclude a claim — weak sources can still be
informative. The flags make source quality visible so the navigator and synthesis
can weigh claims appropriately. When a section has multiple flagged claims,
note the pattern in the confidence line.

When ALL sections are complete, change Status from "IN PROGRESS" to "COMPLETE".
```

### Source mode declarations

Include ONE of these at the top of each agent prompt:

**Web Research:**
```
SOURCE MODE: WEB RESEARCH
You have access to WebSearch and WebFetch. Use them. Every quantitative claim
needs an inline source URL. Follow the research protocol below.
```

**Deep Knowledge:**
```
SOURCE MODE: DEEP KNOWLEDGE
You do NOT have web search. Write from your deep training knowledge. Reference
scholars and works by name: (Author, *Title*, Publisher, Year). Do not fabricate
URLs. Follow the research protocol below — write after each section, don't batch.
```

### Provenance header requirement

Every research output file must start with:

```markdown
# [Output title]

> Provenance: AI/agent-generated research artifact.
> Authority: raw material.
> Review status: unreviewed.
```

If the output is being written inside a project repo that requires YAML frontmatter, use that repo's schema and include:

```yaml
provenance: agent_generated
review_status: unreviewed
```

---

## Unlikely Places: Non-Obvious Source Guide

Include relevant parts of this in agent prompts. Not every source type applies to every question — pick the 2-3 most relevant.

- **Social listening:** Reddit, HackerNews, Twitter/X, niche forums. Unfiltered and more honest than reports. Try `site:reddit.com [topic]`, `[product] complaints OR frustrations OR switched from`.
- **Job postings:** What a company is hiring for tells you where they're investing — before any public announcement.
- **Patent filings and preprints:** Google Scholar, arXiv, USPTO. What's being built before it ships.
- **Conference talks and podcasts:** Practitioner talks (not executive keynotes). Q&A sessions are gold.
- **Regulatory filings:** SEC 10-K/10-Q, EU databases, government audit reports. Hard numbers companies don't volunteer.
- **Customer reviews and complaints:** G2, Capterra, Trustpilot, app store reviews. Patterns in negative reviews reveal real limitations. Also search `[product] alternative`.
- **GitHub repos and issues:** Issues tab reveals real pain points. README positioning. Contributor activity shows momentum.
- **Analyst reports and investor presentations:** Earnings call transcripts contain candid executive commentary during Q&A.
- **Government and NGO data:** World Bank, OECD, national statistics offices — datasets most analysts never touch.

---

## Key Rules

1. **Phase 0 is not optional.** Never design research without understanding the decision context.
2. **Scout before planning.** The research manager does personal recon and shares findings before designing workstreams. This is what makes plans evidence-based.
3. **Design composite plans.** The best research mixes building blocks. Don't default to "all Web Research" — consider where Deep Knowledge or Dialectic would add depth.
4. **Never launch agents without user approval of the plan.**
5. **Check web tool availability before launching.** If denied, switch to Deep Knowledge immediately.
6. **Every agent gets a context brief AND a source mode declaration.**
7. **Every research output gets provenance and review status.**
8. **Every agent gets the research protocol verbatim.**
9. **The navigator is the difference between research and useful research.** Don't skip it.
10. **Push agents toward unlikely sources.** If all research comes from the first page of Google, the plan wasn't good enough.
11. **Dialectic is a composable layer.** Consider adding it to any research with strategic uncertainty — it's not just for "philosophical" questions.
12. **Kill stuck agents immediately.** No progress between two check-ins = stuck. Relaunch with pre-loaded data.
13. **Use the current runtime's general-purpose research agent equivalent.** In Claude Code this is `subagent_type: "general-purpose"` with WebSearch, WebFetch, Read, Write, Edit, Glob, and Grep when available; in other runtimes, adapt to the available tools and state any limitation.
14. **Default output location:** `research/[topic-slug]/` in the current working directory, unless the user specifies otherwise.

---

Now begin. The user's research question follows:

$ARGUMENTS
