# Lesson 7 — Knowledge Improvement

This is the lesson that turns the lifecycle from a line into a loop. Everything from L1–L6 produces a knowledge base; this lesson keeps it good as the world moves — and feeds what it learns back to the start.

## Concepts

- **Knowledge decays.** Even a perfect knowledge base degrades:
  - **Staleness** — the world changed; the knowledge didn't (a policy updated, a product renamed).
  - **Gaps** — new questions arrive with no supporting knowledge (the L5 "not found" signal; the L6 link-prediction backlog).
  - **Contradictions** — new facts conflict with old ones (the L3 conflicting edges).
  - **Drift** — terminology and usage shift; old representations stop matching how people ask.
- **The improvement loop.** A disciplined cycle, scored against the L1 scorecard:
  1. **Detect** — find defects via signals and probes.
  2. **Prioritize** — fix what hurts most: high-traffic + high-impact first.
  3. **Fix** — update, add, merge, retire — at the right lifecycle stage (re-represent, fix the graph, re-extract).
  4. **Verify** — re-run the L1 gold questions; confirm the scorecard moved the right way and nothing regressed.
- **Feedback signals — where defects announce themselves.**
  - **Usage** — what's retrieved a lot (keep it pristine) vs. never (dead weight).
  - **Failed / unanswered queries (L5)** — the single richest gap signal: questions the KB couldn't answer, surfaced honestly by "not found."
  - **Discovery findings (L6)** — predicted-missing edges, suspected duplicates, silos.
  - **User feedback** — thumbs-down, corrections, escalations.
  - **AI failures** — wrong or unsupported answers traced back (via L4 provenance) to the defective source.
- **AI as a KM co-worker.** The same models that consume knowledge can help maintain it: detect contradictions across the graph, propose updates from new sources, draft answers for gaps, summarize and deduplicate. Powerful — and dangerous if unmanaged.
- **Governance.** Provenance (L4) is what makes safe improvement possible: you can see what changed, why, and from which source. Human-in-the-loop review for anything high-impact. The AI *proposes*; a human *approves* the writes that matter.

## Patterns

- **Drive the loop with signals, not opinions.** Unanswered queries (L5) and discovery findings (L6) are a ranked, evidence-based backlog — far better than "someone thinks the FAQ is outdated."
- **Fix at the right stage.** A contradiction might be a stale source (re-extract, L4), a bad merge (fix entity resolution, L4), a modeling problem (revise the schema, L3), or a genuine conflict (human decision) — diagnose before editing.
- **Always verify against the scorecard.** A fix that improves one gold question while breaking three isn't an improvement. Close the loop with measurement, not vibes.
- **AI proposes, human disposes — proportional to impact.** Auto-apply low-risk, high-confidence changes; queue high-impact ones for review.

## Anti-patterns — and how they materialize

- **Write-only knowledge base.** Everyone adds; nobody retires. It grows, contradictions pile up, freshness rots, and retrieval quality slowly dies while the volume metric looks great.
- **Letting AI rewrite the truth.** An LLM "improves" articles in bulk; it smooths language and silently changes a refund window from 30 to 45 days. No provenance, no review — the knowledge base now confidently asserts a fabrication at scale.
- **Fixing the loud, ignoring the long tail.** The team fixes whatever the latest escalation pointed at; the systematic gap signal (hundreds of quiet unanswered queries from L5) is never mined.
- **Improvement without verification.** Changes ship un-measured; the scorecard isn't re-run; regressions accumulate invisibly until a big failure.

## The quality dimension this lesson moves

**Freshness — and the entire L1 scorecard, sustained over time.** The other lessons each lift a dimension once; this lesson is what keeps *all of them* from decaying. The lifecycle closes: improvement signals feed back to representation (L2), the graph (L3), and extraction (L4); querying (L5) and discovery (L6) are the instruments that generate the signals.

## Hands-on for lesson 7

**Close the loop.** Start from the L1–L6 support-knowledge base, now "aged": a policy changed (stale), some queries return "not found" (gaps), and two sources conflict.

- **Mechanic** — ingest a log of usage + unanswered queries (L5) + thumbs-down + discovery findings (L6). **Detect**: an AI pass flags contradictions (L3 conflicting edges) and gaps (L6 link-prediction); the failure log points (via L4 spans) at defective sources. **Prioritize** by traffic × impact. **Fix**: retire a stale doc, add a doc for the top gap, resolve a conflict (human call). **Verify**: re-run the L1 gold questions and show the scorecard recover. Then run the "AI rewrites in bulk, unreviewed" anti-pattern and watch a fabricated number slip in — and how provenance + review would have caught it.
- **What the student feels** — improvement is a measurable loop, not a cleanup sprint; signals beat opinions; AI is a force multiplier *only* with provenance and human gates.
- **Skills exercised** — designing the loop, prioritizing by signal, safe human+AI collaboration, closing the loop with the scorecard.

## To discuss

- What's your richest untapped signal — unanswered queries, AI failures, escalations — and is anyone mining it?
- Where's your line for auto-apply vs. human review, and is it set by *impact* or by convenience?
- The loop is closed: which earlier stage (representation, graph, extraction) does your evidence say to fix *first*?
