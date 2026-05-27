# Lesson 7 — Knowledge Improvement & Agentic Feedback

The capstone. In L6 knowledge flowed *out* to agents. Now the agent acts — succeeds, fails, gets corrected — and that outcome is an error signal. This lesson **backpropagates** it into the knowledge, then runs the **improvement loop** that turns all the course's signals into safe, verified updates. The lifecycle becomes a loop.

---

## Part A — Agentic backpropagation (the backward pass)

### Concepts
- **The metaphor.** Forward pass (L6): the agent consumes context and acts. Backward pass: the outcome tells you something about the knowledge that fed it — like gradients updating weights, agent feedback updates the KB. The hard part is **credit assignment**: *which* fact caused the win or the failure?
- **The signals agents emit.** Retrieval hit/miss, tool success/failure, dead-ends and retries, user/environment corrections (the strongest signal), repeated unmet needs (the L5 "not found" at scale), and facts discovered mid-task.
- **Distillation, not logging.** A raw trajectory is noise. Backprop means *distilling* it into clean, deduplicated knowledge — a resolved how-to, a corrected fact, a new entity/relation for the graph (L3). Logs are not knowledge.
- **Credit assignment via provenance (L4).** Because served facts carry their source, you can trace a failure to the specific stale/wrong fact — and a success to the knowledge worth reinforcing.
- **The danger: feedback loops & model collapse.** Write the agent's own (possibly hallucinated) outputs straight back and the system trains on its own errors; a wrong-but-popular fact gets "confirmed" by repetition. This is why backprop *proposes*; the loop *disposes*.

---

## Part B — The improvement loop (closing the loop)

### Concepts
- **Knowledge decays:** staleness, gaps (L5 "not found", L4 link-prediction backlog, repeated agent dead-ends), contradictions (L3 conflicting edges), and drift.
- **The loop:** **detect → prioritize → fix → verify**, scored against the L1 scorecard.
  1. *Detect* via signals and probes. 2. *Prioritize* by traffic × impact. 3. *Fix* at the right stage (re-represent, fix the graph, re-extract). 4. *Verify* — re-run the L1 gold questions; confirm the scorecard moved and nothing regressed.
- **Signals consolidated:** failed queries (L5), discovery findings (L4), context failures (L6), agentic backprop (Part A), usage, and user feedback — a ranked, evidence-based backlog.
- **AI as a KM co-worker:** detect contradictions, propose updates, fill gaps, summarize — powerful, dangerous if unmanaged.
- **Governance — the gate.** Provenance (L4) makes safe improvement possible. Agent-generated candidates are *proposals* that must be grounded, deduplicated, and approved — automatically when low-risk/high-confidence, by a human when high-impact.

---

## Patterns & anti-patterns

- **Patterns:** capture structured agent feedback as data; distill, don't dump; trace credit with provenance; drive the loop with signals, not opinions; always verify against the scorecard; gate agentic write-back proportional to impact.
- **Anti-patterns:** writing agent output straight back (well-poisoning / model collapse); logging everything, learning nothing; no credit assignment ("agents are failing" but nobody knows which fact); reinforcing popularity instead of correctness; improvement without verification (silent regressions); the write-only KB nobody ever retires from.

## The quality dimension this lesson moves

**Freshness, completeness & correctness — sustained over time.** Every earlier lesson lifts a dimension once; this lesson keeps *all of them* from decaying. Agents in production are the earliest, richest signal of what the knowledge is missing or getting wrong; backprop converts that into candidate updates, and the loop prioritizes, applies (through the gate), and verifies them. The lifecycle closes: fixes feed back to representation (L2), the graph (L3), and extraction (L4).

## Hands-on for lesson 7

**Run the backward pass, then close the loop.** Start from the L1–L6 support-knowledge base, now "aged," plus a batch of agent runs.
- **Backprop:** collect structured feedback (used retrievals, tool failures, corrections, unanswered); distill trajectories into candidate updates; trace one tool failure through provenance to the stale fact behind it. Run the **contamination demo** — pipe raw agent outputs back into the KB and watch a wrong fact reinforce itself and quality collapse; then add grounding + a gate and arrest it.
- **Loop:** ingest all signal streams; detect contradictions/gaps; prioritize by traffic × impact; fix (retire stale, add gap doc, resolve conflict, accept a grounded agent proposal through the gate); re-run the L1 gold questions and watch the scorecard recover.

## To discuss
- What agent signals are you already collecting but not learning from?
- Where's your write-back gate set — by *impact* or by convenience?
- The loop is closed: which earlier stage (representation, graph, extraction, context) does your evidence say to fix *first*?
