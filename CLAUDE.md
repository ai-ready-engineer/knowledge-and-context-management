# Project notes — Knowledge and Context Management in the Age of AI

Part of the AI-Ready Engineer masterclass series (sibling to Experiment Design and Evaluation of AI Systems). Single folder — no public/private split. Shares the AI-Ready Swiss theme in `style.css`.

## Course spine

The course follows the **knowledge lifecycle** as a loop, with **quality of knowledge** as the through-line:

```
represent → connect (graph) → extract → query → discover → provide context → backpropagate → improve → (back to represent)
```

- L1 establishes the quality scorecard (all dimensions).
- L3 (graph) comes before L4 (extraction): the graph is the structure; extraction populates it. The L3 schema is the contract extraction must satisfy.
- "Getting knowledge out" splits into L5 **querying** (retrieve what you know to ask for: search, RAG, GraphRAG, traversal/paths) and L6 **discovery** (surface what you didn't: centrality, communities, link prediction). Graph methods serve both — there is no separate "Graph Methods" lesson.
- The agent loop is L7 + L8: L7 **providing context to agents** is the forward pass (knowledge → agent); L8 **knowledge backpropagation from agentic feedback** is the backward pass (agent outcomes → candidate knowledge updates). L8 *proposes*; L9 *disposes* (the write-back gate lives in L9).
- Each later lesson improves one or two dimensions of that scorecard.
- L9 closes the loop, consolidating signals from L5, L6, L7, and L8 and feeding fixes back to representation, the graph, and extraction.

Lesson list (9): 1 Quality · 2 Representation · 3 Graphs · 4 Extraction · 5 Querying · 6 Discovery · 7 Providing Context to Agents · 8 Knowledge Backpropagation from Agentic Feedback · 9 Improvement.

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
