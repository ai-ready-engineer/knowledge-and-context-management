# Lesson 1 — Quality of Knowledge

Knowledge is now a *component* that answers on your behalf, not a shelf people occasionally browse. Its quality is your product's quality.

## Concepts

- **Data vs. information vs. knowledge.** Data is raw signal; information is data in context; knowledge is information you can *act on* and that connects to other things you know. The DIKW pyramid is a handy first cut — but treat it critically: in practice the levels blur, and "wisdom" on top is mostly hand-waving. What matters is *actionability* and *connectedness*, not the layer count.
- **Knowledge quality is multi-dimensional.** A knowledge base is not "80% good." It is good along some dimensions and bad along others:
  - **Correctness** — the facts are true.
  - **Completeness / coverage** — the questions people actually ask are answerable.
  - **Consistency** — no two parts contradict each other.
  - **Freshness / timeliness** — it reflects the current state of the world.
  - **Relevance** — it contains what matters, not noise.
  - **Provenance / trustworthiness** — every fact traces to a source you can check.
  - **Findability / accessibility** — the right piece can actually be retrieved when needed.
  - **Actionability** — it is specific enough to decide or do something.
- **The AI changes the stakes.** In a RAG or agent system the model retrieves and answers automatically. There is no human to notice the stale page or the missing fact. So knowledge quality sets the *ceiling*: a perfect model on a bad knowledge base gives confident wrong answers.

## Patterns

- **Make quality measurable per dimension**, not as one vague number. A scorecard with 6–8 dimensions beats a single "health score."
- **Tie knowledge quality to downstream AI quality.** Maintain a set of gold questions; measure answerability (can the KB even support an answer?) and citation correctness (does the cited source actually say it?).
- **Keep provenance from day one.** A fact without a source is a fact you cannot maintain.

## Anti-patterns — and how they materialize

- **The single health number.** A dashboard says "KB health: 92%." Nobody can say what dropped when an answer goes wrong, because the number averages correctness, freshness, and coverage into mush.
- **Counting volume as quality.** "We have 12,000 articles" — half are duplicates, a third are stale, and the top 20 customer questions are unanswerable. Volume measured; quality not.
- **Quality measured only by human spot-checks.** An editor reads a few pages and declares it good; meanwhile the AI is failing on the long tail nobody sampled.

## The three moves (the course shape)

For each quality dimension this course teaches the same three moves:

- **Understand it** — what the dimension means and where defects come from (a stale source, a bad extraction, a missing link).
- **Measure it** — the concrete probe: gold questions for coverage, contradiction detection for consistency, last-updated + decay model for freshness.
- **Improve it** — the lifecycle stage that fixes it (representation, the graph, extraction, or the improvement loop in L9).

## Hands-on for lesson 1

**The knowledge-quality scorecard.** Take a small real-ish knowledge base (a folder of ~30 support/product docs) and a set of ~20 gold questions with known answers.

- **Mechanic** — run the gold questions against the KB (simple retrieval + answer). For each, score: *answerable?* (was the supporting fact present), *correct?*, *cited correctly?* Aggregate into the per-dimension scorecard. Then inject defects — delete a doc (coverage drops), duplicate a doc with a changed number (consistency/contradiction), backdate freshness — and watch which scorecard cells move.
- **What the student feels** — a bad answer is rarely "the model's fault"; it maps to a specific defective cell. The scorecard localizes the blame.
- **Skills exercised** — building the scorecard, tracing a bad answer to a defect, setting a ship bar.

## To discuss

- How many dimensions before the scorecard becomes theater? Pick the 4–5 that move decisions in your org.
- Whose number is it — who owns each dimension, and who is accountable when it drops?
