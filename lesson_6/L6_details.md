# Lesson 6 — Knowledge Discovery

Querying (L5) gets out what you know to ask for. **Discovery** surfaces what you didn't — the latent knowledge already implied by the structure of the graph. This is where graph algorithms turn a static knowledge base into an instrument that finds importance, structure, and gaps.

## Concepts

- **Discovery vs. querying.** A query needs a question; discovery generates the questions. "What's the most load-bearing piece of knowledge we have?", "what topics exist that nobody tagged?", "what relation is *missing*?" — none of these is a lookup. They are read off the graph's *structure*.
- **Centrality — what's important.**
  - *Degree* — how many connections (a heavily-referenced policy).
  - *Betweenness* — sits on many paths (a concept everything routes through — and a single point of failure if it's wrong or undocumented).
  - *PageRank / eigenvector* — important because important things point to it (authority).
  - KM uses: find the canonical doc on a topic, rank knowledge, spot the load-bearing fact whose error would poison many answers (tie to L1).
- **Community detection — what clusters together.** Louvain, Leiden, label propagation partition the graph into densely-connected groups. KM uses: discover topics no one tagged, find duplicate clusters, reveal **silos** (two communities that *should* be linked but aren't), organize navigation.
- **Link prediction — what's missing.** Given the graph's structure, predict edges that *should* exist (common-neighbor, Adamic–Adar, or embedding-based scores). KM uses: surface knowledge gaps ("these tickets reference a policy no document covers"), suggest related-article links, propose entity merges. This is the **gap radar** that feeds L7's improvement loop.
- **Node embeddings & GNNs (conceptual).** node2vec / GNNs learn a vector per node from its neighborhood — bringing embedding-style similarity *to the graph*, and powering link prediction and node classification at scale. Reach for them when the graph is large and patterns are too subtle for hand-picked metrics; skip them when a degree count or a Louvain pass already answers the question. (We stay conceptual — this is not a GNN course.)

## Patterns

- **Pick the method from the discovery question.** "What's authoritative?" → centrality. "What topics/silos exist?" → communities. "What's missing?" → link prediction. "Who knows this?" → paths + centrality.
- **Use link prediction as a gap radar.** Run it periodically; high-confidence missing edges are a prioritized to-do list for L7.
- **Graph similarity vs. embedding similarity.** Embeddings (L2) capture *semantic* likeness from text; graph methods capture *structural/relational* likeness. They disagree usefully — combine them.
- **Discovery proposes; it does not commit.** Every output is a suggestion for a human (or L7's loop) to review, never an automatic write.

## Anti-patterns — and how they materialize

- **Over-reading centrality.** A node is high-betweenness because of an extraction artifact (an un-resolved hub entity from skipping L4 dedup), and the team "discovers" a fake key concept. The algorithm measured the data's defects, not the domain.
- **Communities as truth.** Louvain returns 12 clusters; someone reorganizes the whole KB around them. Re-run with a different resolution → 7 clusters. The partition was a *view*, not a fact.
- **Link prediction without review.** Predicted edges get auto-added; a few are wrong; the graph now asserts relations that never existed and GraphRAG (L5) reasons over them. Prediction is a *suggestion*, not a write.
- **GNN cannon for a degree-count problem.** A team trains a GNN to find important docs when `ORDER BY degree` answered it in one line.

## The quality dimension this lesson moves

**Completeness & relevance.** Link prediction and community gaps reveal what's *missing or disconnected* (completeness); centrality and similarity surface what *matters most* (relevance). Discovery turns the static graph into a tool that finds its own defects — feeding directly into L7.

## Hands-on for lesson 6

**The discovery lab.** Use the L3–L4 support-knowledge graph.

- **Mechanic** — run centrality and read off the load-bearing policies (and tie back to L1: an error here poisons many answers). Run community detection and watch topics/silos emerge — then change the resolution and watch them wobble. Run link prediction and get a *ranked list of missing documentation edges*. Build a tiny gap-finder and expertise-locator from these. Then inject an un-resolved duplicate hub (a skipped-L4 defect) and watch centrality crown a fake concept.
- **What the student feels** — each method answers a specific discovery question; outputs are *suggestions* to interpret, not verdicts; and the methods inherit every defect from L3/L4.
- **Skills exercised** — matching method to discovery task, sober interpretation, turning a prediction into a prioritized, reviewable fix.

## To discuss

- Which of your KM pains is really a discovery question in disguise — gap detection, dedup, topic finding, expertise location?
- Link prediction proposes 200 missing edges — who reviews them, and at what confidence do you auto-apply vs. queue for a human? (Straight into L7.)
