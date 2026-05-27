# Script — L5 Knowledge Querying

> Talk outline / script. Beats to hit, transitions, what to show on screen, what to say at each turn.

## Open

"We built the graph (L3) and filled it (L4). Now it just sits there. Two ways to use it: ask it what you know to look for — querying, today — or have it tell you what you didn't know — discovery, next time."

Put three questions on screen: an exact lookup, a "find me a similar past ticket," and a multi-hop ("which customers are hit if we change the policy Enterprise depends on?"). "Same knowledge base. Watch how differently we have to ask."

## Beats

1. Querying vs. discovery — name the split clearly; today is querying.
2. The three retrieval modes — keyword (exact, term-blind to synonyms), semantic (find similar, opaque), structured/graph (filters, joins, traversal, paths). Match mode to question shape.
3. Traversal & paths — the graph superpower; return the path as the explanation. Vectors can't.
4. RAG vs. GraphRAG — ground the LLM in retrieved knowledge; GraphRAG retrieves a subgraph and cites the path. Provenance (L4) is what makes citation possible.
5. Grounded vs. guessing — "not found" is a feature. An ungrounded confident answer is the enemy.

## Demo / playground walkthrough

- Retrieval-mode explorer: fire the three questions through all three modes; show which mode wins which.
- The failure: route the structured question through semantic search → confident, wrong, nearest-chunk answer.
- Headline: multi-hop question, vector-RAG vs. GraphRAG, side by side. GraphRAG returns the answer *and* the cited path; vector-RAG guesses.
- Ask something absent from the graph → system says "not in the knowledge base." Land it: that "not found" is a gold signal for L6/L7.

## Close

Single takeaway: **Querying is matching the retrieval mode to the question and grounding the answer in cited knowledge. A bad answer here is almost always a retrieval failure, not a model failure — and "I don't know" is the most honest thing your system can say.**

## Notes to self

- Keep this lesson about *known questions*. Resist drifting into "find what's missing" — that's L6 discovery.
- The "not found → signal" beat is the explicit bridge to discovery and improvement; plant it deliberately.
- Reuse the same multi-hop question from L3's open so the payoff lands ("remember this from two lessons ago?").
