# Lesson 7 — Providing Context to Agents

This is the "context" half of the course made concrete. We have knowledge (L1–L4) and ways to get it out (L5–L6). Now an **agent** needs it — and an agent doesn't browse a knowledge base. You assemble the **context** it reasons over. This is the forward pass: knowledge flows out to the agent.

## Concepts

- **Context is the unit, not the document.** The agent reasons over whatever is in its context window *right now*. The best knowledge base in the world is useless if the relevant fact isn't in context when the agent thinks. Serving is where findability (L2) and relevance are finally cashed in.
- **What's in an agent's context.** It's a budget shared by many tenants:
  - **Instructions** — system prompt, role, policies.
  - **Retrieved knowledge** — the L5 query results (chunks, subgraphs, facts).
  - **Tool results** — outputs the agent fetched mid-task (ephemeral knowledge).
  - **Memory** — short-term (this conversation) and long-term (persisted across sessions).
  - **Conversation history** — the running dialogue.
  The KB-derived knowledge is one slice; context engineering is allocating the budget across all of them.
- **Upfront vs. just-in-time (agentic) retrieval.** Either pre-load the context you think the agent needs, or give the agent retrieval *tools* and let it pull knowledge just-in-time as the task unfolds. Upfront is simple and predictable; agentic is adaptive but less controllable. Most real agents blend the two.
- **The window is finite — and bigger isn't better.** Context costs tokens (money + latency) and suffers **context rot** / lost-in-the-middle: as the window fills, the model attends worse, especially to the middle. A focused 2K-token context often beats a 100K-token dump.
- **Memory and the KB.** Long-term memory is knowledge the agent accumulates — and the moment it persists and is reused, it *is* part of the knowledge base, subject to every quality dimension from L1. (How it gets back there is L8.)
- **Provenance flows through (L4).** If retrieved knowledge carries its source span into context, the agent can cite — and you can check the answer. Drop provenance at assembly time and grounded facts blur with the model's guesses.

## Patterns

- **Assemble the minimal sufficient context.** Relevance over volume; the goal is the *right* knowledge in the window, not the *most*.
- **Prefer just-in-time for open-ended tasks.** Give the agent retrieval/graph tools (L5) so it pulls what it needs when it needs it, instead of pre-stuffing everything.
- **Carry provenance and structure.** Keep source spans; lay context out in labeled sections so the model can find and cite the right piece.
- **Refresh context across long runs.** Re-retrieve as the task evolves; don't reason for 20 turns on the context you assembled at turn one.

## Anti-patterns — and how they materialize

- **Context maximalism.** "Stuff the whole KB in — the model has 200K tokens." Cost and latency spike, answer quality *drops* via context rot, and the one relevant fact is buried mid-window where the model ignores it.
- **Stale context.** A cached retrieval serves last month's policy into the agent's window; the KB was fresh (L1), but freshness failed *at serve time*. Context is a place staleness re-enters.
- **Provenance stripped at assembly.** Retrieval had sources; the assembler concatenated raw text; the agent now can't cite, and a hallucinated sentence sits indistinguishably next to three real facts.
- **Assemble-once.** Context is built at the first turn and never refreshed; ten tool calls later the agent is reasoning over a stale working set and contradicts what it just learned.

## The quality dimension this lesson moves

**Relevance & findability — at serve time, under a budget.** Every earlier lesson made the knowledge good and retrievable; this lesson decides whether the right slice actually reaches the agent's reasoning, efficiently. A correct, fresh, findable fact that never makes it into context might as well not exist.

## Hands-on for lesson 7

**Assemble the context.** Take a task and a query (reuse L5) against the support-knowledge graph.

- **Mechanic** — assemble the agent's context three ways: (1) dump everything retrievable, (2) top-k focused retrieval, (3) agentic just-in-time (the agent calls a retrieval/graph tool as needed). Compare answer quality, token cost, and latency. Inflate the dump until **context rot** appears — quality drops as size grows. Then assemble *with* provenance and watch the agent produce cited answers; strip it and watch grounding vanish.
- **What the student feels** — more context is not better; relevance and placement beat volume; just-in-time adapts where pre-stuffing can't; provenance must survive assembly.
- **Skills exercised** — minimal-sufficient context, upfront vs. just-in-time, diagnosing context rot, carrying provenance to the agent.

## To discuss

- For your agents, what fraction of context should be pre-loaded vs. fetched just-in-time — and who owns that budget?
- Long-term memory that persists is now part of your KB. Is it held to the L1 scorecard, or is it a back door for unmanaged knowledge? (Sets up L8.)
