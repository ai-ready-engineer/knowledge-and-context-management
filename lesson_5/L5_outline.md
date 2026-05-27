# Lesson 5 — Knowledge Querying

**Number:** L5
**Tagline:** Getting out what you already know. When you know what you're looking for — search, retrieval, RAG, GraphRAG, and graph traversal turn a populated knowledge base into answers.
**Lifecycle stage:** Use — query (the "I know what I want" path)
**Quality dimension in focus:** Findability & relevance

## What we cover
- The two modes of using knowledge: **querying** (retrieve what's known) vs. **discovery** (find what's unknown, L6) — this lesson is querying
- Keyword vs. semantic (embedding) retrieval — exact match vs. "find similar"
- Structured queries over the graph — SPARQL/Cypher, traversal, paths, multi-hop questions
- RAG and GraphRAG — grounding an LLM's answer in retrieved knowledge, with citations
- Combining retrieval modes, and reading what a query can and can't guarantee

## Skills you unlock
- Pick the retrieval mode that fits the question — keyword, semantic, structured, or graph traversal
- Write graph queries that answer multi-hop and relational questions
- Build a RAG/GraphRAG answer that cites its sources (using L4 provenance)
- Tell when an answer is grounded vs. when the system is guessing
- Diagnose a bad answer as a retrieval failure, not a model failure

## Tools and examples
Retrieval-mode explorer (keyword vs. semantic vs. structured on the same question) · GraphRAG vs. vector-RAG side-by-side on a multi-hop question · path/traversal playground over the L3–L4 graph.
