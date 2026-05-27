# Project notes — Knowledge and Context Management

Part of the AI-Ready Engineer masterclass series (sibling to Experiment Design and Evaluation of AI Systems). Single folder — no public/private split. Shares the AI-Ready Swiss theme in `style.css`.

## Course spine

The course follows the **knowledge lifecycle** as a loop, with **quality of knowledge** as the through-line:

```
represent → connect (graph) → extract & discover → query → provide context → improve → (back to represent)
```

- L1 establishes the quality scorecard (all dimensions).
- L3 (graph) comes before L4: the graph is the structure; extraction populates it. The L3 schema is the contract extraction must satisfy.
- L4 **Knowledge Extraction & Discovery** does both halves: *extraction* fills the graph (entities, relations, events, with provenance), and *discovery* mines it (centrality, communities, link prediction). Discovery is only as good as the extraction beneath it.
- L5 **querying** retrieves what you know to ask for (search, RAG, GraphRAG, traversal/paths).
- The agent loop spans L6 + L7: L6 **providing context to agents** is the forward pass (knowledge → agent); L7 folds the backward pass (**agentic backpropagation**: agent outcomes → candidate updates) into the **improvement loop** (detect → prioritize → fix → verify). Agents/AI *propose*; the loop *disposes* (the write-back gate lives in L7).
- Each later lesson improves one or two dimensions of that scorecard.
- L7 closes the loop, consolidating signals from L4, L5, L6, and the agents, and feeding fixes back to representation, the graph, and extraction.

Lesson list (7): 1 Quality · 2 Representation · 3 Graphs · 4 Extraction & Discovery · 5 Querying · 6 Providing Context to Agents · 7 Improvement & Agentic Feedback.

## Per-lesson convention

Each lesson has three files:

- `LN_outline.md` — public-facing summary: tagline, lifecycle stage, "What we cover", "Skills you unlock", quality dimension in focus, tools.
- `LN_details.md` — teaching detail: concepts, patterns, anti-patterns (each shown via a worked example), the quality dimension this lesson moves, and a `## Hands-on for lesson N` section describing the lab.
- `LN_script.md` — delivery: open/hook, beats, demo walkthrough, close.

Keep each lesson tied to the quality scorecard from L1 — state which dimension(s) the lesson improves and how you would measure the improvement.

## Conventions

- Lifecycle stage and the quality dimension(s) in focus appear at the top of every outline.
- Prefer worked examples over abstract definitions — the running domain is an organization's support/product knowledge base feeding an AI assistant.
- Distinguish symbolic (graphs, schemas) from sub-symbolic (embeddings) representations consistently.
