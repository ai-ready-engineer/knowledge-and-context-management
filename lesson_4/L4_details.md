# Lesson 4 — Knowledge Extraction & Discovery

In L3 we designed the graph's schema. This lesson does two things with it: **extraction** *fills* the graph from messy sources, and **discovery** *mines* the filled graph for knowledge that's implied but never stated. Putting facts in, then reading what the structure reveals.

---

## Part A — Extraction (filling the graph)

Extraction is the bridge from unstructured text to the L3 graph. It is also the single biggest entry point for errors — and the place to either capture provenance or lose trust forever.

### Concepts
- **What we extract — to fit the L3 schema.** Entities (nodes), relations (edges), events (time-stamped facts). The schema says what's legal: extraction is "fill this shape," not "find interesting stuff."
- **Classic IE vs. LLM extraction.** Classic (NER, rules, trained models) is fast, cheap, deterministic, brittle. LLM-based extraction is flexible and context-aware but slower, costlier, and can **hallucinate** facts not in the source.
- **Schema-guided extraction.** Give the LLM the L3 schema via structured outputs / function calling and have it fill *that* — parseable, checkable, and guaranteed loadable into the graph.
- **Entity resolution & normalization.** "ACME Corp" / "Acme Inc." / "acme" are one node. Resolve and normalize *before* loading, or every downstream count and query is wrong.
- **Provenance.** Every fact carries its source (doc, span, timestamp), stored on the node/edge — the basis for L1's citation check and L7's retire-when-source-dies.

### Patterns & anti-patterns
- Extract to the schema, keep the span, resolve before you load, go hybrid (classic for the bulk, LLM for the tail).
- **Trap:** trusting LLM facts without grounding (a plausible, schema-valid, fabricated "45-day window"); skipping entity resolution (one customer becomes five nodes); shipping extraction with no precision/recall eval.

---

## Part B — Discovery (mining the graph)

Querying (L5) gets out what you know to ask for. **Discovery** surfaces what you didn't — latent knowledge implied by the graph's structure.

### Concepts
- **Centrality — what's important.** Degree, betweenness, PageRank: find the canonical/authoritative node, and the load-bearing fact whose error would poison many answers (tie to L1).
- **Community detection — what clusters together.** Louvain/Leiden/label propagation reveal topics nobody tagged, duplicate clusters, and **silos** (groups that *should* be linked but aren't).
- **Link prediction — what's missing.** Predict edges that *should* exist (common-neighbor, Adamic–Adar, embedding-based). The **gap radar** that feeds L7's improvement loop.
- **Node embeddings & GNNs (conceptual).** Bring embedding-style similarity to the graph for link prediction / node classification at scale — reach for them only when hand-picked metrics aren't enough. (Not a GNN course.)

### Patterns & anti-patterns
- Pick the method from the question: important → centrality; topics/silos → communities; missing → link prediction. Discovery *proposes*; it doesn't commit.
- **Trap:** over-reading centrality when a hub is really an un-resolved-entity artifact (a skipped-Part-A defect); treating a community partition as truth when it shifts with the resolution knob; auto-adding predicted edges without review.

---

## The quality dimensions this lesson moves

**Correctness & provenance** (extraction): are the facts entering the graph true and traceable? **Completeness & relevance** (discovery): what's missing or disconnected, and what matters most? Note the dependency — discovery is only as trustworthy as the extraction beneath it; it will faithfully measure your data's defects.

## Hands-on for lesson 4

**Fill, then mine.** ~20 support tickets/docs and the L3 schema.
- **Extract** to the schema with an LLM (with source spans); load into the graph; drop the grounding instruction and watch hallucinated facts pollute it; run entity resolution and watch a count correct itself; score precision/recall.
- **Discover** over the filled graph: centrality surfaces the load-bearing policy; community detection reveals topics/silos (and wobbles with the resolution knob); link prediction returns a ranked list of *missing* documentation edges — a prioritized backlog for L7. Inject an un-resolved duplicate hub and watch centrality crown a fake concept.

## To discuss
- Classic IE for the bulk vs. LLM for everything — where's your line?
- Link prediction proposes 200 missing edges — who reviews them, and at what confidence do you auto-apply vs. queue? (Straight into L7.)
