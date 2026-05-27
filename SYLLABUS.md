# Knowledge and Context Management

> A short course for everyone who builds with, ships, or depends on AI systems that sit on top of an organization's knowledge — engineers, PMs, knowledge owners, data teams, leaders. No heavy coding required. We build the knowledge layer that determines whether the AI on top of it is any good.

Each lesson takes one stage of the **knowledge lifecycle** — *represent → connect → extract → query → discover → provide context → backpropagate → improve* — and keeps **quality of knowledge** as the through-line.

## Why this course

AI changed the stakes of knowledge management. A RAG system, an assistant, or an agent is only as good as the knowledge it can reach — and it now reaches that knowledge automatically, at scale, with no human to catch the stale doc, the missing fact, or the contradiction. The knowledge base used to be a place people *looked things up*; now it is a component that *answers on your behalf*. Its quality is your product's quality.

Three claims:

1. Quality of knowledge sets the ceiling on quality of AI answers — you cannot prompt your way past a bad knowledge base.
2. Knowledge is an asset with a lifecycle: it must be represented, extracted, connected, measured, and continuously improved — not just stored.
3. The same AI that consumes knowledge can help manage it — extracting, linking, and repairing it — if you keep humans and provenance in the loop.

## Objectives

**For the individual** — treat knowledge as something you can design and measure, not just accumulate. After the course, given a knowledge base behind an AI system, you can say what is good and bad about it, why an answer failed, and what to fix first.

**For the company** — knowledge quality as shared infrastructure. When teams share a vocabulary for representation, extraction, graphs, and quality, a knowledge defect gets caught and fixed before it degrades every downstream answer.

## Format

9 lessons. Each lesson: a core part **for everybody** (no code, no math prereq), a **hands-on example** (interactive, no install), and **practical examples**. Optional deeper notebooks are take-home.

The course follows the knowledge lifecycle as a loop: **represent → connect → extract → query → discover → provide context → backpropagate → improve → (back to represent)**. Lesson 1 establishes the quality scorecard; each later lesson improves one or two of its dimensions; Lesson 9 consolidates the signals — from querying (L5), discovery (L6), context-serving (L7), and agentic backpropagation (L8) — and feeds fixes back to the start.

Two structural ideas run through the second half. "Getting knowledge out" splits into **querying** (retrieve what you know to ask for) and **discovery** (surface what you didn't), with graph methods serving both. And the **agent loop** is made explicit: knowledge flows *out* to agents as context (L7, the forward pass), and agent outcomes flow *back* as candidate knowledge updates (L8, the backward pass — "backpropagation"), gated and consolidated by the improvement loop (L9).

## Lessons

1. [Quality of Knowledge](lesson_1/L1_outline.md)
2. [Knowledge Representation](lesson_2/L2_outline.md)
3. [Knowledge Graphs](lesson_3/L3_outline.md)
4. [Knowledge Extraction](lesson_4/L4_outline.md)
5. [Knowledge Querying](lesson_5/L5_outline.md)
6. [Knowledge Discovery](lesson_6/L6_outline.md)
7. [Providing Context to Agents](lesson_7/L7_outline.md)
8. [Knowledge Backpropagation from Agentic Feedback](lesson_8/L8_outline.md)
9. [Knowledge Improvement](lesson_9/L9_outline.md)
