# Lesson 5 — Knowledge Querying

We now have a populated graph (L3 + L4). There are two ways to *use* it: **query** what you already know is there, and **discover** what you don't (L4). This lesson is querying — the "I know what I'm looking for" path.

## Concepts

- **Querying vs. discovery.** Querying answers a question you can pose: "what's the refund window for Enterprise?", "which customers are on Plan X?". Discovery (L4) surfaces things you didn't know to ask: a missing link, a hidden cluster, an emerging topic. Same knowledge base, two very different jobs.
- **Retrieval modes — match the mode to the question.**
  - **Keyword / lexical** — exact and boolean match. Precise when you know the term; blind to synonyms and paraphrase.
  - **Semantic / embedding** (L2 vectors) — "find things *like* this." Robust to phrasing; opaque and can't do exact filters or relations.
  - **Structured / graph** — SPARQL/Cypher over the L3 graph: exact filters, joins, **traversal**, **paths**, multi-hop. Answers "how is X connected to Y" and "everything that depends on Z."
- **Traversal and paths.** The graph's superpower for querying: follow edges to answer relational and multi-hop questions, and return the *path* as an explanation ("Acme → Enterprise-Plan → Policy-12"). This is what a vector store fundamentally cannot do.
- **RAG and GraphRAG.** Don't make the LLM answer from memory — *retrieve* supporting knowledge and ground the answer in it.
  - *Vector RAG* — retrieve the most similar chunks, stuff them in context.
  - *GraphRAG* — retrieve a relevant *subgraph* (entities + their connections) and let the model reason over structure, follow relations, and cite the path.
  - Provenance from L4 is what lets either one cite its sources — turning an answer into a *checkable* answer.
- **Grounded vs. guessing.** A querying system should make it visible whether an answer is supported by retrieved knowledge or generated from the model's priors. "No supporting knowledge found" is a feature, not a failure.

## Patterns

- **Choose the retrieval mode from the question shape.** Exact/structured → graph query. "Find similar" → semantic. Multi-hop/relational → traversal/GraphRAG. Often: semantic to find the entry point, then traverse.
- **Always cite.** Return the source span (L4) or the graph path. An uncited answer can't be trusted or improved.
- **Make "I don't know" first-class.** If retrieval finds nothing relevant, say so — don't let the LLM paper over a gap (which is exactly the signal L7 wants).

## Anti-patterns — and how they materialize

- **One retrieval mode for every question.** Everything goes through semantic search; a structured question ("policies that changed after January") gets the nearest-looking chunk and a fabricated answer. (The L2 trap, now at query time.)
- **Ungrounded generation dressed as retrieval.** The "RAG" system retrieves nothing useful but the LLM answers confidently anyway; the citation, if any, doesn't actually support the claim.
- **GraphRAG over an unvalidated graph.** The subgraph handed to the model is full of duplicate nodes (skipped L4 resolution) or hallucinated edges; the model reasons fluently over a broken structure.
- **Silent empty results.** A query returns nothing and the UI shows a confident generated answer instead of "not in the knowledge base" — burying the gap that should have become a discovery/improvement signal.

## The quality dimension this lesson moves

**Findability & relevance.** Querying is where the knowledge base's findability is cashed in: the right mode retrieves the right knowledge for the question, and citations make relevance checkable. A bad answer here is usually a retrieval failure (wrong mode, missing knowledge), not a model failure — and that diagnosis is the skill.

## Hands-on for lesson 5

**Query the populated graph.** Use the L3–L4 support-knowledge graph.

- **Mechanic** — pose a set of questions of different shapes: an exact lookup, a "find similar past ticket," and a multi-hop relational one. Run each through keyword, semantic, and graph/traversal retrieval; see which mode answers which cleanly. Then run the multi-hop question two ways — vector-RAG vs. GraphRAG — and compare the answer *and* the citations/path. Finally, ask something the graph doesn't contain and confirm the system says "not found" instead of fabricating.
- **What the student feels** — there's no universal retrieval; the mode must fit the question. GraphRAG's cited path is auditable where the vector answer is a guess. "I don't know" is the honest, useful answer.
- **Skills exercised** — matching mode to question, writing traversal/path queries, building cited RAG/GraphRAG, diagnosing retrieval vs. model failure.

## To discuss

- For your traffic, what's the mix of exact / similar / multi-hop questions? That sets your retrieval architecture.
- Every "not found" is a gap signal — where does it go? (Straight into L4 discovery and L7 improvement.)
