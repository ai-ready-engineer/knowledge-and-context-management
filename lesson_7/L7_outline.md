# Lesson 7 — Knowledge Improvement & Agentic Feedback

**Number:** L7
**Tagline:** Agents using your knowledge are the richest signal of what it's missing or getting wrong. Backpropagate that feedback into the knowledge — then run the loop that detects, fixes, and verifies, without poisoning the well.
**Lifecycle stage:** Learn & improve — the backward pass, and the loop that closes back to Represent
**Quality dimension in focus:** Freshness, completeness & correctness — sustaining the whole L1 scorecard over time

## What we cover
- **Agentic backpropagation** — agents are the forward pass (L6); their outcomes are an error signal that flows back to update the knowledge
- Signals agents emit: retrieval hits/misses, tool failures, dead-ends, user corrections, repeated unmet needs, facts discovered mid-task
- Distilling reusable knowledge from trajectories, and credit assignment via provenance (L4)
- **The improvement loop** — detect → prioritize → fix → verify, scored against the L1 scorecard, fed by signals from L4–L6 and the agents
- The danger and the governance: feedback loops / model collapse, the write-back gate, human-in-the-loop, and not letting AI quietly rewrite the truth

## Skills you unlock
- Instrument agents to emit structured feedback as first-class knowledge signals
- Distill trajectories into clean, deduplicated candidate updates; trace blame to specific facts
- Design a detect → prioritize → fix → verify loop driven by signals, not opinions
- Gate agent-generated write-back and prevent self-reinforcing contamination
- Close the loop: feed fixes back to representation, the graph, and extraction

## Tools and examples
Agent-feedback collector · trajectory-to-knowledge distiller · contamination demo (write hallucinations back, watch quality collapse) · improvement-loop dashboard with before/after scorecard.
