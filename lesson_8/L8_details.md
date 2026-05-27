# Lesson 8 — Knowledge Backpropagation from Agentic Feedback

In L7 knowledge flowed *out* to the agent (the forward pass). Now the agent acts — and succeeds, fails, gets corrected, hits dead-ends. Those outcomes are an *error signal*. **Backpropagation** is the discipline of flowing that signal *back* into the knowledge base, the way gradients flow back to update weights. The agent's experience becomes the knowledge's update.

## Concepts

- **The metaphor — and its limits.** Forward pass (L7): the agent consumes context and produces actions. Backward pass (here): the outcome tells you something about the knowledge that fed it. Like training, the useful version isn't "store the output" — it's "use the error to update the right parameter." The hard part, as in real backprop, is **credit assignment**: *which* piece of knowledge caused the win or the failure?
- **The signals agents emit.** Production agents are the richest, most current evidence of knowledge quality:
  - **Retrieval hit/miss** — was the retrieved knowledge actually used and helpful, or ignored?
  - **Tool success/failure** — an action failed because a fact was wrong or missing.
  - **Dead-ends and retries** — the agent looped or gave up: a gap or a contradiction.
  - **User/environment corrections** — the strongest signal: "no, the window is 30 days."
  - **Repeated unmet needs** — many agents asking what the KB can't answer (the L5 "not found", now at scale).
  - **Facts discovered mid-task** — the agent (or a tool) surfaced something new and reusable.
- **Distillation, not logging.** A raw trajectory is noise. Backprop means *distilling* it into clean, deduplicated knowledge: a resolved how-to, a corrected fact, a new entity/relation for the graph (L3). Logs are not knowledge.
- **Credit assignment via provenance (L4).** Because every served fact can carry its source (L7), you can trace a failure to the specific stale or wrong fact — and a success to the knowledge worth reinforcing. No provenance, no credit assignment, no learning.
- **The headline danger: feedback loops and model collapse.** If the agent's own (possibly hallucinated) outputs are written straight back into the KB, the system trains on its own errors. Quality collapses, contradictions compound, and a wrong-but-popular fact gets "confirmed" by repetition. This is the central risk of closing the agent loop — and why backprop *proposes* updates rather than committing them (the application and verification belong to L9).

## Patterns

- **Capture structured feedback as first-class signals.** Log retrieval relevance, tool outcome, and corrections as data, not just free-text traces.
- **Distill, don't dump.** Turn a successful resolution into one clean, deduplicated KB candidate; collapse a thousand similar dead-ends into one gap report.
- **Trace credit with provenance.** Attribute outcomes to specific knowledge; reinforce what helped, flag what hurt.
- **Propose, never auto-commit unverified agent knowledge.** Agent-generated candidates are *suggestions* that must be grounded and gated before they touch the KB — hand them to L9's loop.
- **Reinforce correctness, not popularity.** Heavy use of a fact is not evidence it's true; separate "used a lot" from "verified."

## Anti-patterns — and how they materialize

- **Writing agent output straight back (the well-poisoning).** The agent confidently states a wrong refund window; an auto-ingest pipeline writes it to the KB; next week other agents retrieve it, repeat it, and it looks confirmed. Model collapse, in slow motion.
- **Logging everything, learning nothing.** Terabytes of traces, no distillation; the signal is there but never turned into a single knowledge update.
- **No credit assignment.** "Agents are failing on refunds" — but nobody can say which fact is wrong, so the fix is a guess.
- **Popularity as truth.** The system reinforces whatever agents use most; a convenient wrong fact out-competes the correct one nobody reaches.

## The quality dimension this lesson moves

**Completeness, freshness, and correctness — revealed through use.** Agents in production exercise the knowledge against the real world continuously; their feedback is the earliest and richest signal of what's missing, stale, or wrong. Backprop converts that signal into *candidate* updates — which L9 then prioritizes, applies, and verifies.

## Hands-on for lesson 8

**Run the backward pass.** Use the L7 agent over a batch of support tasks against the graph.

- **Mechanic** — collect structured feedback: which retrievals were used, which tools failed, where the user corrected the agent, what went unanswered. **Distill** the trajectories into candidate knowledge updates (a corrected fact, a new relation, a gap report). **Trace** one tool failure back through provenance (L4) to the stale fact that caused it. Then run the **contamination demo**: pipe the agents' raw outputs straight back into the KB and watch quality collapse over a few cycles — a wrong fact reinforcing itself. Finally, add grounding + a gate (defer to L9) and show the collapse arrested.
- **What the student feels** — agent feedback is gold *and* dynamite; distillation and credit assignment turn it into knowledge; writing outputs back unguarded is how you poison your own well.
- **Skills exercised** — instrumenting feedback, distilling trajectories, credit assignment via provenance, preventing feedback-loop contamination.

## To discuss

- What agent signals are you already collecting but not learning from?
- Where's the line between "the agent may write this back automatically" and "a human must approve"? (This is exactly what L9 governs.)
- How do you keep a heavily-used wrong fact from looking validated by its own popularity?
