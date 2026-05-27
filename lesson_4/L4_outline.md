# Lesson 4 — Knowledge Extraction

**Number:** L4
**Tagline:** Now we fill the graph. Extraction turns messy sources into the entities, relations, and facts the schema asked for — and it's where errors and hallucinations sneak in.
**Lifecycle stage:** Populate (build the L3 graph from sources)
**Quality dimension in focus:** Correctness & provenance

## What we cover
- From documents to structure: entity, relation, and event extraction — filling the L3 schema
- Classic information extraction (NER, rules, patterns) vs. LLM-based extraction with structured outputs
- Schema-guided extraction and function calling — making an LLM emit exactly the nodes and edges the graph expects
- Entity resolution, deduplication, and normalization — the same thing said five ways becomes one node
- Extraction quality: precision/recall, hallucination risk, and keeping provenance

## Skills you unlock
- Design an extraction pipeline from raw source to graph-ready records
- Use an LLM to extract to the L3 schema, and constrain it so it doesn't invent facts
- Resolve and merge entities that refer to the same real-world thing
- Evaluate extraction quality (precision/recall) and trace every fact to its source
- Decide when classic IE is enough and when an LLM earns its cost

## Tools and examples
LLM schema-guided extractor (text in → graph-ready records out) · entity-resolution playground (merge duplicates) · extraction-quality scorer with provenance links into the graph.
