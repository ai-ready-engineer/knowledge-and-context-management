# Enterprise Knowledge and Context Management

## Why this course

AI changes knowledge management:

1. Agents are a primary — if not *the* primary — consumer of knowledge. This gives us a unique opportunity: getting high-resolution feedback on knowledge, at scale, directly from the agents themselves.

2. Context engineering — what to show an agent, in what form, at what time — is central to the success of our agents.

3. The way agents consume knowledge is different from how humans do — and even humans increasingly consume knowledge *through* agents. This changes how we represent and structure knowledge.

4. Agents are also increasingly producers of knowledge. Humans have to pick what they want to control and what can instead evolve at the speed of agents.

These have implications for enterprises:
- Knowledge gets a loss function. It becomes "testable" and can evolve almost on its own.
- Balancing speed, quality, and governance is the new mastery.
- Knowledge has many authors and many forms — we can now process, represent, and make use of all of them to get the right content to consumers.
- Knowledge graduates from documentation to infrastructure.


## Who this course is for

- **Engineers and engineering managers building with AI:** RAG, agents, and assistants are only as good as the knowledge they sit on. Learn to build that knowledge layer deliberately.
- **Product managers and knowledge owners:** Turn a pile of documents into a measurable, improvable knowledge asset — and know when it is good enough to ship.
- **Data and platform teams:** Choose representations, model a knowledge graph, design extraction pipelines, and serve the right context to agents.
- **Executives** *(compact course)*: Understand why knowledge quality is now a product-quality lever, and what to ask the teams who own it.


## Objectives

**For the individual** — treat knowledge as something you can design and measure, not just accumulate. After the course, given a knowledge base behind an AI system, you can say what is good and bad about it, why an answer failed, and what to fix first.

**For the company** — knowledge quality as shared infrastructure. When teams share a vocabulary for representation, extraction, graphs, and quality, a knowledge defect gets caught and fixed before it degrades every downstream answer.


## What you will learn

By the end of the course, "knowledge" will look like a managed, measurable asset. You will be able to:

- Write a quality scorecard for your knowledge based on intrinsic and extrinsic (usage) metrics.
- Pick the right representation — text, schema, taxonomy, embedding, graph — for each use case, and defend the choice.
- Sketch a knowledge graph schema for your domain, and call when it earns its keep over a plain vector store.
- Extract structured knowledge from messy sources, abstract it into higher-level structure, and infer the edges nobody wrote down.
- Choose the right query mode — keyword, semantic, structured, RAG, GraphRAG — and tell a grounded answer from a guess.
- Assemble agent context that is grounded, fresh, and within the window's budget — and know what to cut when it isn't.
- Turn agent failures into knowledge fixes, and run the improvement loop that keeps the base fresh, complete, and correct.


## What the course is NOT about

- We are not training foundation models — we manage the knowledge that AI systems consume and produce.
- We are not doing organizational change management or "KM as HR" — the focus is the technical knowledge layer behind AI products.
- We are not building a full production RAG stack — we build the knowledge it depends on.


## Prerequisites

The course has no prerequisites except for:

- Curiosity
- Something you actually want your organization to *know*
- Patience for the unglamorous truth that good AI starts with good knowledge

The course is "hands-on" but no heavy coding is required: you will get to play with small examples to *feel* what a representation, a graph, or an extraction buys you — and where each one breaks.


## Format

Each lesson: a core part **for everybody** (no code, no math prereq), a **hands-on example** (interactive, no install), and **practical examples**. Optional deeper notebooks are take-home.


## How the course works

The course follows **one stage of the knowledge lifecycle** per lesson — represent, connect, extract, abstract, infer, query, provide context, improve — keeping **quality of knowledge** as the through-line: every stage is judged by whether the knowledge it produces is correct, complete, consistent, fresh, and findable.

The lifecycle is a loop, not a line: the final lesson consolidates the signals from extraction (L4), inference (L5), querying (L6), context-serving (L7), and the agents themselves, and feeds fixes back into representation, the graph, and extraction.

The **agent loop** runs through the second half: knowledge flows out to agents as context (L7, the forward pass), and agent feedback flows back to update the knowledge (L8, "agentic backpropagation").


## Lessons

Eight 1-hour sessions following the knowledge lifecycle: *represent → connect → extract → abstract → infer → query → provide context → improve*.

1. **[Defining and Measuring Knowledge Quality](lesson_1/L1_outline.md)** — What "knowledge" is, what makes it good, and how to measure it — the scorecard the rest of the course optimizes.
2. **[Knowledge Representation](lesson_2/L2_outline.md)** — Text, schemas, taxonomies, triples, embeddings — and how the choice decides what you can later do with the knowledge.
3. **[Knowledge Graphs](lesson_3/L3_outline.md)** — Connecting facts into a graph of entities and relations — the structure we populate, query, and mine.
4. **[Knowledge Extraction & Abstraction](lesson_4/L4_outline.md)** — Fill the graph from messy sources, then form higher-level structure: clusters, summaries, taxonomies, hierarchies.
5. **[Knowledge Inference](lesson_5/L5_outline.md)** — Derive what the graph doesn't explicitly state — centrality and communities, link prediction, rule-based and embedding-based reasoning.
6. **[Knowledge Querying](lesson_6/L6_outline.md)** — Getting out what you know — search, semantic retrieval, structured queries, RAG, and GraphRAG.
7. **[Providing Context to Agents](lesson_7/L7_outline.md)** — Assembling the right knowledge into an agent's finite context window, at the right moment — the "context" half of the course.
8. **[Knowledge Improvement & Agentic Feedback](lesson_8/L8_outline.md)** — Backpropagate agent feedback into the knowledge, and run the loop that keeps it fresh, complete, and correct — without poisoning the well.
