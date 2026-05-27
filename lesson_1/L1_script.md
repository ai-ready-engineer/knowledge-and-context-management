# Script — L1 Quality of Knowledge

> Talk outline / script. Beats to hit, transitions, what to show on screen, what to say at each turn.

## Open

Walk in on a failing AI assistant. Ask it a real customer question; it answers confidently and *wrong*. Then show the source: the relevant doc is six months stale, and a duplicate says something different. The model did nothing wrong — the knowledge was bad.

Hook line: "We spend all our effort prompting and fine-tuning the model. But the answer was decided before the model ever ran — by the knowledge it could reach."

## Beats

1. Data → information → knowledge. Quick, concrete, then puncture the DIKW pyramid: it's a ladder, not a law. What we care about is *actionable, connected, trustworthy* knowledge.
2. Knowledge isn't "good" or "bad" — it's good along dimensions. Put the 8 dimensions on screen. For each, a one-line failure story.
3. The AI raises the stakes: retrieval is automatic, no human in the gap, so KB quality = answer ceiling.
4. From vibes to scorecard. Show the per-dimension scorecard. Each cell has a probe (gold questions, contradiction rate, staleness).
5. The three moves (understand / measure / improve) — and map each dimension to the lifecycle stage / later lesson that fixes it (representation, graph, extraction, querying, discovery, improvement). This sets up the whole course.

## Demo / playground walkthrough

- Show the scorecard on a small KB with all green.
- Inject a defect live: delete a doc → coverage cell goes red, and a gold question becomes unanswerable. Duplicate-with-a-changed-number → consistency red, contradiction surfaced.
- Punchline: every bad answer landed in a specific cell. That cell names the lesson that fixes it.

## Close

Single takeaway: **Knowledge is a measurable asset. You can only improve what you measure — and in the age of AI, the knowledge scorecard, not the model, is where most quality is won or lost.**

## Notes to self

- Resist turning this into an ontology lecture — that's L2. Keep L1 about *what good means* and *how we measure it*.
- The injected-defect demo is the emotional core; rehearse it so the right cells light up.
