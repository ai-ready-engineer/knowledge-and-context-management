# Script — L7 Knowledge Improvement & Agentic Feedback

> Talk outline / script. Beats to hit, transitions, what to show on screen, what to say at each turn.

## Open

"Last lesson, knowledge flowed out to the agent — the forward pass. The agent then went and *did* something: solved a ticket, failed, got corrected. That outcome is an error signal. In a neural net you'd backpropagate it to update the weights. Here we backpropagate it to update the *knowledge* — and then run the loop that keeps the whole thing alive."

Hook: "Your agents in production are the best knowledge auditors you have. The question is whether their signal flows back — or evaporates in a log."

## Beats

**Backpropagation (the backward pass)**
1. The metaphor and its hard part: credit assignment — *which* fact caused the win or loss?
2. The signals agents emit — retrieval hit/miss, tool fail, dead-ends, corrections, unmet needs, mid-task discoveries.
3. Distillation, not logging; credit assignment via provenance (L4).
4. The danger — feedback loops and model collapse. Backprop *proposes*; the loop *disposes*.

**The improvement loop (closing it)**
5. Knowledge decays; the loop: detect → prioritize → fix → verify against the L1 scorecard.
6. Signals consolidated — L5 unanswered, L4 discovery, L6 context failures, agentic backprop, usage, user feedback.
7. Governance — the write-back gate, provenance, human-in-the-loop proportional to impact.

## Demo / playground walkthrough

- Run agents over a batch; collect feedback; distill a solved ticket into one clean KB candidate; trace a tool failure through provenance to the stale fact.
- The contamination demo (moral climax): pipe raw agent outputs back → a wrong fact reinforces itself, quality collapses → add grounding + gate → arrested.
- The loop: ingest signal streams; detect; prioritize; fix (incl. a gated agent proposal); re-run gold questions → scorecard recovers, *measured*.
- Final slide: the loop closes — represent → connect → extract & discover → query → serve context → improve (with agentic backprop) → back to represent.

## Close

Single takeaway: **Agents are the forward pass; their outcomes are an error signal you backpropagate into the knowledge. Distill it, assign credit with provenance, gate every write — then run a measured detect→fix→verify loop. KM is a loop, not a project, and the same agents that use your knowledge can keep it true — only with provenance and gates.**

## Notes to self

- This is the capstone — tie every beat back to L1–L6 so the course lands as one connected lifecycle.
- The contamination/model-collapse demo is the emotional core; make the wrong fact reinforce *gradually*.
- Two halves (backprop → loop) but one message: feedback in, verified knowledge out, safely.
