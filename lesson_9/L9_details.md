# Lesson 9 — Knowledge Improvement

This is the lesson that turns the lifecycle from a line into a loop. Everything from L1–L8 produces knowledge, serves it, and generates feedback; this lesson keeps the knowledge good as the world moves — and feeds what it learns back to the start.

## Concepts

- **Knowledge decays.** Even a perfect knowledge base degrades:
  - **Staleness** — the world changed; the knowledge didn't (a policy updated, a product renamed).
  - **Gaps** — new questions arrive with no supporting knowledge (the L5 "not found" signal; the L6 link-prediction backlog; repeated unmet agent needs from L8).
  - **Contradictions** — new facts conflict with old ones (the L3 conflicting edges).
  - **Drift** — terminology and usage shift; old representations stop matching how people and agents ask.
- **The improvement loop.** A disciplined cycle, scored against the L1 scorecard:
  1. **Detect** — find defects via signals and probes.
  2. **Prioritize** — fix what hurts most: high-traffic + high-impact first.
  3. **Fix** — update, add, merge, retire — at the right lifecycle stage (re-represent, fix the graph, re-extract).
  4. **Verify** — re-run the L1 gold questions; confirm the scorecard moved the right way and nothing regressed.
- **Feedback signals — where defects announce themselves.** This lesson consolidates every signal the course has generated:
  - **Failed / unanswered queries (L5)** — questions the KB couldn't answer, surfaced honestly by "not found."
  - **Discovery findings (L6)** — predicted-missing edges, suspected duplicates, silos.
  - **Context failures (L7)** — the right knowledge existed but never reached the agent's window, or reached it stale.
  - **Agentic backpropagation (L8)** — distilled candidate updates and credit-assigned failures from agents in production: the richest, most current channel.
  - **Usage** — what's retrieved a lot (keep it pristine) vs. never (dead weight).
  - **User feedback** — thumbs-down, corrections, escalations.
- **AI as a KM co-worker.** The same models that consume knowledge can help maintain it: detect contradictions across the graph, propose updates, draft answers for gaps, summarize and deduplicate. Powerful — and dangerous if unmanaged.
- **Governance — the gate.** Provenance (L4) is what makes safe improvement possible: you can see what changed, why, and from which source. This is also where the **L8 write-back gate** lives: agent-generated candidates are *proposals* that must be grounded, deduplicated (L4), and approved — automatically when low-risk and high-confidence, by a human when high-impact. The AI proposes; the loop disposes.

## Patterns

- **Drive the loop with signals, not opinions.** Unanswered queries (L5), discovery findings (L6), and agentic backprop (L8) are a ranked, evidence-based backlog — far better than "someone thinks the FAQ is outdated."
- **Fix at the right stage.** A contradiction might be a stale source (re-extract, L4), a bad merge (fix entity resolution, L4), a modeling problem (revise the schema, L3), a serving problem (fix context assembly, L7), or a genuine conflict (human decision) — diagnose before editing.
- **Always verify against the scorecard.** A fix that improves one gold question while breaking three isn't an improvement. Close the loop with measurement, not vibes.
- **Gate agentic write-back.** Auto-apply low-risk, high-confidence agent proposals; queue high-impact ones for review. This is the safeguard L8 hands you against feedback-loop contamination.

## Anti-patterns — and how they materialize

- **Write-only knowledge base.** Everyone (and every agent) adds; nobody retires. It grows, contradictions pile up, freshness rots, and retrieval quality slowly dies while the volume metric looks great.
- **Letting AI rewrite the truth.** An LLM "improves" articles in bulk; it smooths language and silently changes a refund window from 30 to 45 days. No provenance, no review — the knowledge base now confidently asserts a fabrication at scale. (The L8 contamination risk, now at the KB level.)
- **Fixing the loud, ignoring the long tail.** The team fixes whatever the latest escalation pointed at; the systematic gap signal (hundreds of quiet unanswered queries from L5, thousands of agent dead-ends from L8) is never mined.
- **Improvement without verification.** Changes ship un-measured; the scorecard isn't re-run; regressions accumulate invisibly until a big failure.

## The quality dimension this lesson moves

**Freshness — and the entire L1 scorecard, sustained over time.** The other lessons each lift a dimension once; this lesson is what keeps *all of them* from decaying. The lifecycle closes: improvement signals feed back to representation (L2), the graph (L3), and extraction (L4); querying (L5), discovery (L6), context-serving (L7), and agentic backprop (L8) are the instruments that generate the signals.

## Hands-on for lesson 9

**Close the loop.** Start from the L1–L8 support-knowledge base, now "aged": a policy changed (stale), some queries return "not found" (gaps), two sources conflict, and a batch of agent runs (L8) has produced candidate updates and credit-assigned failures.

- **Mechanic** — ingest the signal streams: unanswered queries (L5), discovery findings (L6), context failures (L7), and L8 agentic backprop. **Detect**: an AI pass flags contradictions (L3 conflicting edges) and gaps; the L8 failures point (via L4 spans) at defective sources. **Prioritize** by traffic × impact. **Fix**: retire a stale doc, add a doc for the top gap, resolve a conflict (human call), accept a grounded agent proposal through the gate. **Verify**: re-run the L1 gold questions and show the scorecard recover. Then run the "auto-accept ungated agent write-back" anti-pattern and watch a fabricated number slip in — and how the gate + provenance would have caught it.
- **What the student feels** — improvement is a measurable loop, not a cleanup sprint; signals beat opinions; AI and agents are force multipliers *only* with provenance and gates.
- **Skills exercised** — designing the loop, prioritizing by signal, gating agentic write-back, closing the loop with the scorecard.

## To discuss

- What's your richest untapped signal — unanswered queries, agent dead-ends, escalations — and is anyone mining it?
- Where's your gate for agentic write-back (L8) set, and is it by *impact* or by convenience?
- The loop is closed: which earlier stage (representation, graph, extraction, context) does your evidence say to fix *first*?
