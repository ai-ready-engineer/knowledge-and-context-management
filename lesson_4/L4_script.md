# Script — L4 Knowledge Extraction & Discovery

> Talk outline / script. Beats to hit, transitions, what to show on screen, what to say at each turn.

## Open

Put the empty L3 schema next to a raw support ticket. "We designed the box. Now two moves: *fill* it from this mess — extraction — and then *mine* what the filled structure reveals that nobody ever wrote down — discovery."

Hook: "Extraction is where the graph gets its facts — and its lies. Discovery is where the graph tells you something you didn't know to ask."

## Beats

**Extraction**
1. What we extract — entities, relations, events — to fit the L3 schema. "Fill this shape," not "find interesting stuff."
2. Classic IE vs. LLM extraction — the trade-off; schema-guided extraction via structured outputs.
3. Entity resolution + provenance — the unglamorous steps that make counts true and facts traceable.

**Discovery**
4. Centrality (load-bearing knowledge), community detection (topics/silos), link prediction (the gap radar that feeds L7).
5. Embeddings/GNNs — conceptual only; don't bring a GNN to an `ORDER BY degree` fight. And the warning: discovery faithfully measures your data's defects too.

## Demo / playground walkthrough

- Extract 20 docs to the schema with spans; load into the graph. Drop grounding → a hallucinated "45-day window" pollutes it; the span check catches it. Run entity resolution → a count drops 5→1.
- Centrality → the load-bearing policy (tie to L1). Community detection → topics emerge, then wobble with the resolution knob. Link prediction → ranked missing-edge backlog for L7.
- Failure: inject an un-resolved duplicate hub (skipped extraction step) → centrality crowns a fake concept.

## Close

Single takeaway: **Extract to the schema with provenance and resolution, then mine the structure for what's important and what's missing. Discovery is only as good as the extraction beneath it — and both feed the improvement loop.**

## Notes to self

- Two halves, one lesson: keep the hinge explicit — "garbage extraction makes discovery confidently wrong."
- The link-prediction backlog is the handoff to L7's improvement loop.
