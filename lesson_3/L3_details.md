# Lesson 3 — Knowledge Graphs

A knowledge graph makes *connection* a first-class part of the representation. We introduce it now, right after representation, because the graph is the **target structure** the rest of the course fills (extraction, L4), queries (L5), and mines (L6).

## Concepts

- **Anatomy.** A KG is **entities** (nodes) joined by **relations** (edges), each carrying **properties**. *Acme* —`is-customer-of`→ *Us*; *Acme* —`subscribes-to`→ *Enterprise-Plan*; *Enterprise-Plan* —`has-refund-window`→ *60 days*. On top sits a **schema/ontology** that says which node and edge types are legal.
- **A graph is a representation choice (callback to L2).** It sits at the structured/symbolic end of the spectrum. Choosing it now — before we extract anything — means we decide *what shape the knowledge will take* before we start filling it. The schema you design here is the contract extraction must satisfy in L4.
- **Two main flavors.**
  - **RDF triples** — everything is a `(subject, predicate, object)` triple; queried with **SPARQL**; strong on standards, interoperability, formal semantics (W3C, linked data).
  - **Labeled property graph (LPG)** — nodes and edges with arbitrary properties; queried with **Cypher** (Neo4j) and similar; pragmatic, popular in engineering. *Same idea, different ergonomics.*
- **KG vs. vector store.** A vector store (L2 embeddings) answers "find me text *like* this." A graph answers "*how* is X connected to Y," "what's two hops from here," "everything that depends on this policy." Multi-hop and relational questions — the bulk of real KM questions — are exactly what embeddings cannot do. Most systems use both: vectors for fuzzy entry points, graph for structure.
- **Gaps and contradictions become visible.** In a pile of documents, a missing fact is invisible and a contradiction is buried. In a graph, a gap is a *node with no `documented-by` edge* and a contradiction is *two conflicting edges*. That visibility is what makes L6's discovery and L7's improvement possible.

## Patterns

- **Model the questions, not the documents.** Design node and edge types around the queries you need to answer (who-depends-on-what, what-changed, who-knows-this) — and around what you can realistically extract in L4.
- **Design the schema before you populate.** A clear, small schema is the contract for extraction. Decide the legal node/edge types now.
- **Plan for conflict.** Decide up front whether conflicting facts are last-write-wins, keep-both-with-provenance, or human-review — you'll need this the moment extraction (L4) loads real sources.

## Anti-patterns — and how they materialize

- **A graph because graphs are cool.** A team builds a KG for a corpus whose only questions are "find a similar doc." Months of ontology work to underperform a vector store on the one query type that matters.
- **No schema.** The graph is built ad hoc; every later extractor invents its own edge labels (`uses`, `is-using`, `utilizes`); the graph becomes a hairball no query traverses consistently.
- **Over-modeling.** A 40-type ontology no extraction pipeline can ever fill; the graph stays 90% empty while the real knowledge lives in a `notes` blob. (The schema must be extractable — a direct constraint on L4.)

## The quality dimension this lesson moves

**Completeness & consistency.** A graph turns coverage gaps into *missing edges* and contradictions into *conflicting edges* — defects that are invisible in a document pile and obvious in a graph. This visibility is the foundation discovery (L6) and improvement (L7) build on.

## Hands-on for lesson 3

**Model and query a domain.** Before any extraction, design the graph by hand.

- **Mechanic** — model the support domain as entities and relations (customer, product, policy, plan; relations: subscribes-to, depends-on, supersedes, documented-by). Load a handful of facts by hand into a small property graph. Write two or three Cypher queries ("which plans have a 60-day window?", "what depends on Policy-12?", "two hops from Acme"). Then pose a multi-hop question to a vector store and to the graph; see which can answer it. Leave a `documented-by` edge missing and watch a query expose the gap.
- **What the student feels** — relational questions that embeddings fumble fall out of a graph in one query; the schema they design *is* the spec for extraction; gaps and conflicts are visible by construction.
- **Skills exercised** — domain modeling, basic queries, KG-vs-vector decision, schema design as the extraction contract.

## To discuss

- For your use case, what fraction of real questions are multi-hop/relational vs. "find similar"? That ratio decides whether the graph earns its cost.
- How rich can the schema be before extraction (L4) can't fill it? Design to what you can extract.
