# Script — L6 Knowledge Discovery

> Talk outline / script. Beats to hit, transitions, what to show on screen, what to say at each turn.

## Open

"Last lesson you asked the graph questions. Today the graph tells *you* something you didn't know to ask." Put the L3–L4 graph on screen and light up the most central node: "This one policy is load-bearing for 40% of answers. If it's wrong, the whole assistant is wrong — and you'd never have seen that in a folder of docs, or by querying."

Hook: "Querying needs a question. Discovery generates them."

## Beats

1. Discovery vs. querying — discovery reads the *structure*, not your search box. Name the split (callback to L5).
2. Centrality — important / load-bearing / single point of failure. Degree, betweenness, PageRank, one KM use each. Tie the load-bearing node to L1 quality.
3. Communities — topics nobody tagged; silos that should be linked. Show the partition — then turn the resolution knob and watch it change (it's a view, not a fact).
4. Link prediction — the gap radar; the one that feeds L7. Ranked list of edges that *should* exist.
5. Embeddings/GNNs — conceptual only. When patterns are too subtle for hand-picked metrics. Warning: don't bring a GNN to an `ORDER BY degree` fight.

## Demo / playground walkthrough

- Centrality on the support graph → the load-bearing policy; tie to L1 (an error here poisons many answers).
- Community detection → topics emerge; wobble the resolution; same data, different clusters. Sober the room.
- Link prediction → ranked list of missing documentation edges = a prioritized backlog for L7.
- Failure demo: inject an un-resolved duplicate hub (skipped L4) → centrality crowns a fake concept. Algorithms measure your data's defects too.

## Close

Single takeaway: **Discovery reads the graph's structure to surface what you didn't know — importance (centrality), groups (communities), gaps (link prediction). Every output is a prioritized suggestion to review, and it's only as good as the graph underneath.**

## Notes to self

- Keep GNNs strictly conceptual; if someone wants the math, point to a deep-dive, not the main thread.
- Every method output must end in a *KM action* — rank, merge, document, link. No algorithm for its own sake.
- The link-prediction backlog is the explicit handoff to L7's improvement loop.
