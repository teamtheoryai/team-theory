---
name: quote-ranking
description: Recipe that pulls every relevant verbatim quote on a topic from interview transcripts and ranks them, mapped to the scorecard, with no scoring or recommendation. Use when the user runs /human-capital:quote-ranking, or asks to find quotes, pull evidence, or see what a candidate said about a topic.
user-invocable: true
---

# Recipe: quote finder and ranker

Run the five steps in [recipe.md](../../reference/recipe.md) with the values below. This skill holds no judgment: what to look for and what the deliverable must contain come from the Team Theory workflow.

**Team Theory workflow:** `SCI-W-013` (Quote Finder & Ranker).

## Inputs

| Input | Source | What to fetch |
|---|---|---|
| Interview transcripts | `~~meeting transcripts`, Team Theory `list_documents` / `get_document` | Every interview with the candidate for this role |
| Target (scorecard) | This conversation, `~~cloud storage`, `~~ATS` (the job), Team Theory `list_documents` / `get_document`, `search_portfolio_knowledge` | The target for the role |
| Topic | The user | The topic or facets to search for, if narrower than the whole target |

The transcripts are **required**. Read each one in full.

## Destinations

| Destination | Action |
|---|---|
| `~~cloud storage`, `~~knowledge base` | Save as a document |
| `~~ATS` | Attach the quote map to the candidate |
| `~~chat` | Post it to the channel the user names |

## Output format

- A document artifact.
- Header block: candidate, role, topic, the transcripts used.
- One section per scorecard facet (or per topic), each a table of quotes in rank order: rank, verbatim quote, source transcript and timestamp.
- Quotes verbatim, never paraphrased.
- No ratings and no recommendation.
- Ends with **Sources** and **Methodology trace**.
