# Lesson 4 — Knowledge Extraction

In L3 we designed the graph's schema. Extraction is how we *fill* it from messy sources. It is also the single biggest entry point for errors — and the place to either capture provenance or lose trust forever.

## Concepts

- **What we extract — to fit the L3 schema.**
  - **Entities** — the nodes: people, products, accounts, policies, dates, amounts (NER is the classic version).
  - **Relations** — the edges: *Acme* **is-customer-of** *us*; *Policy-12* **supersedes** *Policy-9*.
  - **Events** — time-stamped happenings: *refund issued* to *Acme* on *2026-03-01*.
  - The schema from L3 tells the extractor exactly which node and edge types are legal — extraction is "fill this shape," not "find interesting stuff."
- **Classic IE vs. LLM extraction.**
  - *Classic* — rules, regexes, gazetteers, trained NER/relation models. Fast, cheap, deterministic, auditable; brittle to phrasing, expensive to build per domain.
  - *LLM-based* — prompt the model to read text and emit structured records. Flexible, handles new domains with a few examples, reads context; but slower, costlier, and can **hallucinate** facts that aren't in the source.
- **Schema-guided extraction.** Don't ask an LLM for "the important facts." Give it the L3 **schema** (via structured outputs / function calling) and have it fill *that*. Constrains the output, makes it parseable, makes "did it invent an edge type?" checkable, and guarantees what comes out can load into the graph.
- **Entity resolution (linking & dedup).** "ACME Corp", "Acme Inc.", "acme" are one node. Extraction produces mentions; resolution merges mentions into canonical entities. Skip it and your graph has five nodes for one customer — and every L5 query and L6 metric is wrong.
- **Normalization.** Dates, currencies, units, names to canonical forms — otherwise "30 days" and "1 month" never match, and the graph can't connect them.
- **Provenance.** Every extracted fact should carry *where it came from* (doc, span, timestamp), stored on the node/edge. Without it you can't verify, update, or retire the fact when its source changes — and L1's citation-correctness probe is impossible.

## Patterns

- **Extract to the schema, not to prose.** Structured output you can validate and load beats a paragraph you must re-parse.
- **Keep the span.** Store the source document and exact text span on each node/edge — this powers L1's citation-correctness probe and L9's retire-when-source-dies.
- **Resolve before you load.** Run entity resolution and normalization *before* writing to the graph, not after duplicates spread.
- **Hybrid extraction.** Cheap classic IE for the high-volume easy cases; LLM for the messy long tail.

## Anti-patterns — and how they materialize

- **Trusting the LLM's facts without grounding.** The model emits "refund window: 45 days" — plausible, parseable, schema-valid, and *not in the document*. It filled the shape from prior knowledge. Without a stored span nobody catches it.
- **No entity resolution.** "Acme" loads as 5 nodes; an L6 count says you have 5 enterprise customers when you have one. Each mention was "correct"; the graph is wrong.
- **Extraction with no eval.** A pipeline ships because the output *looks* structured; nobody measured precision/recall against a labeled sample, so a 70%-recall extractor silently drops a third of the facts and leaves graph gaps.
- **Lossy normalization.** Forcing every date to a year drops the month; "expires Q3" becomes "expires 2026" and a freshness check (L9) can never fire.

## The quality dimension this lesson moves

**Correctness & provenance.** Extraction decides whether the facts entering the graph are true and traceable. A fact with a source span can be verified and maintained; a fact without one is a liability the moment the source changes.

## Hands-on for lesson 4

**Fill the graph.** Give students ~20 support tickets / product docs and the L3 schema (entities: customer, product, policy; relations: affects, supersedes; events: refund_issued).

- **Mechanic** — run an LLM extractor to the schema; inspect the structured output *with* source spans; load it into the L3 graph. Then deliberately remove the "must be grounded in a span" instruction and watch hallucinated facts appear and pollute the graph. Run entity resolution on customer mentions; merge "Acme"/"ACME Corp" and watch a graph count correct itself. Score precision/recall against a small labeled gold set.
- **What the student feels** — the gap between "looks structured" and "is correct and grounded"; how dedup changes every downstream query; the graph from L3 coming alive — or getting poisoned.
- **Skills exercised** — schema-guided extraction, provenance capture, entity resolution, extraction eval.

## To discuss

- Where do you draw the line: classic IE for the bulk, LLM for the tail — or LLM for everything and pay the cost?
- Who reviews extracted facts before they become graph "truth" — and can a human keep up at volume? (Sets up L9.)
