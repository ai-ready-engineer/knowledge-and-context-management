# Script — L4 Knowledge Extraction

> Talk outline / script. Beats to hit, transitions, what to show on screen, what to say at each turn.

## Open

Put the L3 graph schema on screen — empty, just the shape. Next to it, a raw support ticket: a wall of text. "We designed the box. Now: how do we fill it from this mess, reliably, a million times?"

Hook: "This is the step where the graph gets its facts. It's also the step where it gets its lies."

## Beats

1. What we extract — entities, relations, events — *to fit the L3 schema*. Extraction is "fill this shape," not "find interesting stuff."
2. Classic IE vs. LLM extraction — the trade table. Deterministic/cheap/brittle vs. flexible/costly/hallucination-prone.
3. Schema-guided extraction — hand the model the L3 schema (structured outputs / function calling). What comes out is guaranteed loadable.
4. Entity resolution — the unglamorous step that makes graph counts true. "Acme" five ways → one node.
5. Provenance — keep the span on every node/edge. Powers L1's citation check and L9's retire-when-source-dies.

## Demo / playground walkthrough

- Run the schema-guided extractor on 20 docs; show clean records with source spans; load them into the L3 graph — it comes alive.
- Live failure: drop the grounding instruction → a hallucinated "45-day window" loads into the graph, schema-valid and wrong. Then the span check catches it.
- Run entity resolution: a graph count drops from 5 customers to 1. Every downstream query just changed.
- Flash precision/recall against the gold set — "looks structured" was 70% recall, leaving real graph gaps.

## Close

Single takeaway: **Extract to the schema, keep the source span, resolve entities before you load. Structure that isn't grounded and deduplicated is confident nonsense — and now it's in your graph.**

## Notes to self

- The hallucination demo is the gut-punch — make the fabricated fact plausible, and show it *polluting the graph from L3*, not just a JSON blob.
- Don't teach a specific NER library; teach the *shape* of the pipeline. Tools change; the stages don't.
- Tee up L5: "the graph is built and populated — now, how do we get knowledge *out* of it?"
