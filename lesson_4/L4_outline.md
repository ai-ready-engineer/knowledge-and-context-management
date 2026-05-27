# Lesson 4 — Knowledge Extraction & Discovery

**Number:** L4
**Tagline:** Fill the graph from messy sources — and then mine its structure for knowledge you didn't know was there. Extraction puts facts in; discovery surfaces what's implied, missing, or important.
**Lifecycle stage:** Populate & mine (build the L3 graph, then read its structure)
**Quality dimension in focus:** Correctness & provenance (extraction); completeness & relevance (discovery)

## What we cover
- **Extraction** — entity, relation, and event extraction to fill the L3 schema
- Classic IE (NER, rules, patterns) vs. LLM-based extraction with structured outputs / function calling
- Entity resolution, deduplication, normalization, and keeping provenance
- **Discovery** — reading the graph's structure for latent knowledge
- Centrality (what's important / load-bearing), community detection (topics & silos), link prediction (the gap radar); node embeddings & GNNs, conceptually

## Skills you unlock
- Design an extraction pipeline from raw source to graph-ready records
- Use an LLM to extract to the L3 schema, and constrain it so it doesn't invent facts
- Resolve and merge entities; trace every fact back to its source
- Match a discovery task — gap detection, dedup, topic finding, expertise location — to the right graph method
- Use link prediction to surface missing knowledge before users hit the gap

## Tools and examples
LLM schema-guided extractor with provenance · entity-resolution playground · graph-methods lab (centrality, communities, link prediction) · link-prediction gap-finder.
