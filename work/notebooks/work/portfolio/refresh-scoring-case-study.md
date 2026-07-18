# Deciding Which Pages to Fix First: A Content Refresh Scoring Model

## The problem

When a website has thousands of pages, you can't check them all by hand. Someone has to decide which pages are worth reviewing first, and doing that manually becomes difficult as the number of pages grows. I wanted to use data to identify the pages most likely to be declining so an SEO team could focus their time where it matters most.

## What I did

I started by digging into the data available for each page — things like search volume, impressions, click-through rate, average position, content type, and trend direction. I looked for patterns and relationships between these variables before building anything.

Then I built two ways to flag declining pages:

1. **A hand-written rule** — a simple, direct baseline based on the obvious signals.
2. **A decision tree model** — trained to combine multiple signals instead of relying on one.

Since the real goal was ranking pages by priority, not just sorting them into "decline" or "not decline," I judged both approaches using Precision@20 and Precision@50 — how many of the top 20 and top 50 flagged pages were actually right.

**Results:**

| | Precision@20 | Precision@50 |
|---|---|---|
| Hand-written rule | 0.90 | 0.68 |
| Decision tree | 0.70 | 0.72 |

The rule was sharper at the very top — the first 20 pages it flagged were almost all correct. But the tree held up better as the list got longer, which matters if a team is working through 50 pages, not just 20.

## What didn't work

I expected one or two metrics to carry most of the signal. They didn't. Average position and CTR, for example, correlated far more weakly than I assumed — no single number reliably predicted decline. That's the real reason the tree edged out the rule at scale: it could weigh several weak signals together instead of betting on one.

## Where this stands

This was a proof of concept, not something a team used to make live decisions. But it showed something real: This was a proof of concept rather than a production system. On the starter dataset, the decision tree outperformed the simple rule at Precision@50, suggesting that combining multiple signals can improve page prioritization.

## What I'd do differently

I'd spend more time on feature engineering and evaluate more carefully — cross-validation instead of a single train-test split, and I'd try Random Forest or Gradient Boosting alongside the tree to see if the pattern held. I'd also add explainability, so an SEO team could see *why* a page got flagged, not just that it did. And if this moved toward production, I'd want to validate it against newer data, track how it performs over time, and retrain it as search trends shift — because what predicts decline today won't necessarily predict it in six months.

## About Me

I'm an AI & Data Science undergraduate building machine learning projects that focus on practical problems. My recent project used a decision tree to prioritize webpages for content refresh, improving Precision@50 from 0.68 to 0.72 over a simple rule-based baseline.

Want to talk about machine learning or collaboration? Connect with me on LinkedIn.
