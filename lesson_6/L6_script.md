# Script — L6 Providing Context to Agents

> Talk outline / script. Beats to hit, transitions, what to show on screen, what to say at each turn.

## Open

"For six lessons we've treated knowledge as something a *person* looks up. But the consumer now is an *agent* — and the agent never opens your knowledge base. It only ever sees what you put in its context window. So the question stops being 'is the knowledge good?' and becomes 'is the right knowledge *in the window* when the agent thinks?'"

Hook: "This is the 'context' in Enterprise Knowledge and Context Management. The forward pass — knowledge flowing out to the agent."

## Beats

1. Context is the unit, not the document. The agent reasons over the window, period.
2. What's in the context — instructions, retrieved knowledge (L5), tool results, memory, history. A shared budget. The KB is one tenant.
3. Upfront vs. just-in-time (agentic) retrieval — pre-stuff vs. give the agent tools to pull. Blend.
4. The window is finite and bigger isn't better — cost, latency, context rot / lost-in-the-middle. The 2K-beats-100K punchline.
5. Memory + provenance — persisted memory becomes KB (subject to L1); provenance must flow through so the agent can cite.

## Demo / playground walkthrough

- Context assembler: one task, three strategies — dump-everything / top-k / agentic just-in-time. Show the table: quality, tokens, latency.
- Context rot demo: grow the dump; watch answer quality fall while cost rises. "More context made it worse."
- Provenance: assemble with source spans → cited answer; strip them → a hallucination hides among the facts.

## Close

Single takeaway: **The agent only knows what's in its context. Providing context is choosing the minimal, relevant, grounded, fresh slice that fits the budget — knowledge that never reaches the window might as well not exist.**

## Notes to self

- This is where "Context Management" earns its place in the title. Tie it back: every prior lesson made knowledge good; this one delivers it.
- Keep the agent framing concrete (a support agent resolving a ticket), not abstract "context theory."
- Tee up L7: the agent now acts on this context — and what happens next (success, failure, correction) is a signal that should flow *back* into the knowledge. That return path — backpropagation — opens the final lesson, alongside the improvement loop.
