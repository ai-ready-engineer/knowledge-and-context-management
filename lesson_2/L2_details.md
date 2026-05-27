# Lesson 2 — Knowledge Representation

The representation is the decision you make *before* you can retrieve, compare, reason, or check for contradictions. Choose it for the questions you need to answer.

## Concepts

- **The representation spectrum.** Same knowledge, different forms:
  - **Unstructured** — prose, docs, transcripts. Cheap to create, expressive, but hard to query precisely or check for consistency.
  - **Semi-structured** — markdown with sections, tables, key-value front-matter. Some structure, retrieval handles, still mostly text.
  - **Structured** — relational tables, **taxonomies** (a tree of categories), **ontologies** (categories + relations + rules), **triples** (subject–predicate–object). Precise, queryable, checkable — but expensive to build and rigid.
  - **Vector / embedding** — text mapped to points in a high-dimensional space; "similar meaning ≈ nearby." Powers semantic retrieval, but is *opaque*: you can't query it for "all refunds over 30 days," only for "things like this."
- **Symbolic vs. sub-symbolic.** Symbolic (schemas, triples) is explicit, inspectable, and supports exact queries and logical consistency checks. Sub-symbolic (embeddings) is fuzzy, robust to phrasing, great for "find me something like this" — but can't enforce a rule or guarantee a fact. Most real systems need both.
- **Taxonomy vs. ontology vs. schema.** Taxonomy = controlled hierarchy of terms. Ontology = taxonomy + typed relations + constraints (a refund *is-a* transaction; a transaction *has* an amount). Schema = the shape records must fit. They are what makes two teams' knowledge *interoperable* instead of two private vocabularies.
- **Chunking and embeddings for RAG.** To make documents retrievable we split them into chunks and embed each. Chunk too big → retrieval is imprecise and dilutes the answer; too small → you lose the context that made the fact meaningful. The chunk boundary is a representation decision that silently caps answer quality.

## Patterns

- **Let the questions choose the representation.** "All contracts expiring in Q3" needs structure; "explain our refund philosophy" needs text; "find similar past tickets" needs embeddings.
- **Use a controlled vocabulary for anything you'll filter or join on.** Free-text "category" fields become five spellings of the same thing.
- **Hybrid by default.** Text + embeddings for recall, a thin schema/taxonomy on top for precision and consistency.

## Anti-patterns — and how they materialize

- **One representation to rule them all.** Everything is dumped into a vector store. Semantic search works until someone asks "which policies changed after January" — a structured question embeddings can't answer, so the system fabricates one.
- **Schema so rigid nobody fills it.** A 40-field ontology is designed; contributors skip the hard fields; the structured knowledge is 90% null and the real knowledge stays in a free-text "notes" blob.
- **Chunking by character count.** Splitting every 1,000 characters cuts a table in half and severs a fact from its qualifier ("...unless the customer is enterprise"), so retrieval returns half-truths.

## The quality dimension this lesson moves

**Findability & consistency.** The representation decides what can be retrieved (findability) and whether contradictions are even detectable (consistency). A taxonomy makes "are these two facts about the same thing?" answerable; a pile of prose does not.

## Hands-on for lesson 2

**The representation explorer.** Take ~10 facts about a product's refund policy and show them in four representations side by side: prose paragraph, a table, RDF-style triples, and embedded chunks.

- **Mechanic** — pose the same five questions ("what's the refund window for enterprise?", "find similar policies", "did anything contradict?", "list all policies with a 30-day window") against each representation. See which questions each form answers cleanly, badly, or not at all.
- **What the student feels** — there is no "best" representation; there is a best *for the question*. The opaque power of embeddings vs. the brittle precision of triples becomes concrete.
- **Skills exercised** — choosing a representation, reasoning about embedding limits, sketching a small schema.

## To discuss

- Where in your stack is the representation, not the model, the actual bottleneck?
- Who owns the taxonomy, and what stops it from forking into per-team dialects?
