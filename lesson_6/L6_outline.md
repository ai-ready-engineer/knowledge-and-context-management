# Lesson 6 — Providing Context to Agents

**Number:** L6
**Tagline:** An agent doesn't browse your knowledge base — you assemble its *context*. Getting the right knowledge into a finite context window, at the right moment, is its own discipline.
**Lifecycle stage:** Serve — deliver knowledge to agents as context (the forward pass)
**Quality dimension in focus:** Relevance & findability — cashed in at serve time, under a token budget

## What we cover
- The shift from "user looks things up" to "system assembles an agent's context" — and why context is the unit that matters
- What's in an agent's context: instructions, retrieved knowledge (L5), tool results, memory, conversation history — the KB is one input among several
- Context engineering: choosing what goes in the finite window — upfront vs. just-in-time (agentic) retrieval
- Context window limits, cost/latency, and "context rot" — why more context is often worse
- Short-term vs. long-term memory, and carrying provenance (L4) into context so the agent can cite

## Skills you unlock
- Assemble the minimal sufficient context for a task, relevance over volume
- Choose between pre-loading context and letting the agent fetch it just-in-time
- Diagnose context rot and lost-in-the-middle failures
- Carry provenance into context so answers stay grounded and citable
- Budget the context window against cost, latency, and quality

## Tools and examples
Context assembler (same query, several context strategies side by side) · context-rot demo (answer quality vs. context size) · grounded-vs-ungrounded context with citations.
