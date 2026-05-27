# Lesson 8 — Knowledge Backpropagation from Agentic Feedback

**Number:** L8
**Tagline:** Agents using your knowledge are the richest signal of what it's missing or getting wrong. Backpropagation is turning that agentic feedback into knowledge updates — without poisoning the well.
**Lifecycle stage:** Learn — the return path, agent → knowledge (the backward pass)
**Quality dimension in focus:** Completeness, freshness & correctness — revealed through use

## What we cover
- The backpropagation metaphor: agents are the forward pass (L7); their outcomes are an error signal that should flow back to update the knowledge
- The signals agents emit: retrieval hits/misses, tool successes/failures, dead-ends, user corrections, repeated unmet needs, facts discovered mid-task
- Distilling reusable knowledge from agent trajectories — turning a solved task into a durable KB entry, not a raw log
- Credit assignment: tracing a success or failure back to the specific knowledge responsible (via L4 provenance)
- The danger: feedback loops and model collapse — agents writing their own hallucinations back into the knowledge base

## Skills you unlock
- Instrument agents to emit structured feedback as first-class knowledge signals
- Distill trajectories into clean, deduplicated candidate knowledge — not log dumps
- Trace credit and blame to specific facts using provenance
- Recognize and prevent contamination / self-reinforcing feedback loops
- Decide what an agent may propose vs. what a human or gate must approve (handoff to L9)

## Tools and examples
Agent-feedback collector (retrieval relevance, tool outcome, corrections) · trajectory-to-knowledge distiller · contamination demo (write hallucinations back, watch quality collapse) and the grounding/gating that stops it.
