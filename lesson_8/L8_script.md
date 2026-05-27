# Script — L8 Knowledge Backpropagation from Agentic Feedback

> Talk outline / script. Beats to hit, transitions, what to show on screen, what to say at each turn.

## Open

"Last lesson, knowledge flowed out to the agent — the forward pass. The agent then went and *did* something: solved a ticket, or failed, or got corrected by the user. That outcome is an error signal. In a neural net you'd backpropagate it to update the weights. Here we backpropagate it to update the *knowledge*."

Hook: "Your agents in production are the best knowledge auditors you have. They exercise every fact against the real world, all day. The question is whether that signal flows back — or evaporates in a log."

## Beats

1. The metaphor: forward pass (L7) → outcome → backward pass (update the knowledge). And its hard part: credit assignment — *which* fact caused the win or loss?
2. The signals agents emit — retrieval hit/miss, tool fail, dead-ends, corrections, repeated unmet needs, facts discovered mid-task.
3. Distillation, not logging — a trajectory is noise; the update is a clean, deduplicated knowledge candidate.
4. Credit assignment via provenance (callback to L4) — trace a failure to the stale fact; reinforce what helped.
5. The danger — feedback loops and model collapse. Write the agent's own hallucinations back and you train on your errors. This is why backprop *proposes*; L9 *disposes*.

## Demo / playground walkthrough

- Run the L7 agent over a batch of tasks; collect structured feedback (used retrievals, tool failures, corrections, unanswered).
- Distill: turn a solved ticket into one clean KB candidate; collapse 200 identical dead-ends into one gap report.
- Credit assignment: trace a tool failure through provenance to the exact stale fact. "There's your bug."
- The contamination demo (the moral climax): pipe raw agent outputs back into the KB; over a few cycles a wrong fact reinforces itself and quality collapses. Then add grounding + a gate → collapse arrested. Hand the gate to L9.

## Close

Single takeaway: **Agents are the forward pass; their outcomes are an error signal you should backpropagate into the knowledge. Distill it, assign credit with provenance, and never write unverified agent output straight back — that's how you poison the well. Backprop proposes; the improvement loop disposes.**

## Notes to self

- Keep the metaphor honest — name where it breaks (credit assignment is genuinely hard; we approximate with provenance + heuristics).
- The contamination/model-collapse demo is the emotional core; make the wrong fact reinforce *gradually* so the room feels the trap close.
- Explicit handoff to L9: the candidate updates from here are inputs to the improvement loop's detect→prioritize→fix→verify.
