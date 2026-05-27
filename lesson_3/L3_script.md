# Script — L3 Knowledge Graphs

> Talk outline / script. Beats to hit, transitions, what to show on screen, what to say at each turn.

## Open

Ask the room a multi-hop question: "Which customers are affected if we change the refund policy that the Enterprise plan depends on?" Show a vector store fumbling it — it retrieves a chunk about refunds and guesses. Then show the same question answered by traversing a graph, hop by hop.

Hook: "Embeddings find things that look alike. A graph answers how things are connected — and most real questions are about connection. So before we extract anything, let's decide the *shape* the knowledge will live in."

## Beats

1. Anatomy: nodes, edges, properties, schema on top. Build the Acme / Enterprise-Plan / refund mini-graph live.
2. A graph is a representation choice (callback to L2) — and a decision we make *before* filling it. The schema is the contract extraction (L4) must satisfy.
3. RDF/SPARQL vs. property-graph/Cypher — same idea, different ergonomics. One triple, one Cypher line. Don't religious-war it.
4. KG vs. vector store — the decision rule: multi-hop/relational → graph; "find similar" → vectors; usually both.
5. Gaps and contradictions become visible — missing edges, conflicting edges. This is the hook for L6 (discovery) and L9 (improvement).

## Demo / playground walkthrough

- Model the support domain live; load a few facts by hand into the graph builder.
- Run three Cypher queries; relational answers fall out cleanly.
- Headline comparison: the multi-hop question, vector store vs. graph, side by side. The graph returns the answer *and* the path.
- Leave a `documented-by` edge missing → a gap query lights it up. "A graph shows you what you don't have."

## Close

Single takeaway: **A knowledge graph makes connection — and the gaps and contradictions in it — first-class and queryable. Design the schema now; it's the contract we'll populate by extraction next.**

## Notes to self

- We're deliberately *before* extraction — no auto-population yet. Today is "what's the structure and is it worth it." Resist demoing extraction; that's L4.
- Keep SPARQL-vs-Cypher light; the audience needs the *concept* of a queryable graph, not a syntax tutorial.
- Tee up L4: "we designed the shape; next we fill it from messy sources — and that's where errors get in."
