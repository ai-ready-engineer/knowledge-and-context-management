# Script — L2 Knowledge Representation

> Talk outline / script. Beats to hit, transitions, what to show on screen, what to say at each turn.

## Open

Put one fact on screen — "Enterprise customers get a 60-day refund window; everyone else gets 30." Then show it four ways: a sentence, a row in a table, two triples, and an embedding blob. Ask: "Which of these lets me answer 'list every plan with a 60-day window'? Which lets me find a *similar* policy I've never seen the words for?"

Hook: "The model gets all the attention, but the representation decided what was answerable before the model woke up."

## Beats

1. The spectrum: unstructured → semi-structured → structured → vector. One slide, examples of each on the same content.
2. Symbolic vs. sub-symbolic — the core mental model. Explicit/inspectable/exact vs. fuzzy/robust/opaque. Neither wins; they cover different questions.
3. Taxonomy vs. ontology vs. schema — the interoperability layer. Build a tiny taxonomy live (5 categories) and add one typed relation to make it an ontology.
4. Chunking & embeddings for RAG — the quiet quality killer. Show a chunk that severed "...unless enterprise" from its rule.
5. Hybrid by default — text+embeddings for recall, thin schema on top for precision and consistency.

## Demo / playground walkthrough

- Representation explorer: same 10 refund facts, four forms. Fire the five questions.
- Highlight the failure: the embedding store confidently "answers" the structured question by retrieving the nearest-looking chunk — and gets it wrong.
- Show chunking: re-split the doc at a sentence boundary vs. mid-rule; watch the retrieved answer flip from correct to half-true.

## Close

Single takeaway: **Choose the representation for the questions you must answer — and expect to need more than one. The representation is a quality decision, made before the model runs.**

## Notes to self

- Don't go down the RDF-vs-property-graph rabbit hole here — that's L3 (Knowledge Graphs, next). Keep L2 about the *spectrum* and the symbolic/sub-symbolic split.
- Keep the live taxonomy tiny; the point is the *act* of controlling vocabulary, not a complete ontology.
