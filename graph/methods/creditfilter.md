---
id: method:creditfilter
type: method
title: CreditFilter
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'single-turn dense math/code Pass@1 RLVR (one verifier reward, not a token window)'
    reason: 'CISPO remains Pass@1; CreditFilter is a DAPO-host within-response entropy-rank window'
    use_instead: method:cispo
  - when: 'RLVR token-filter plug-in keeping top-20% tokens by |E·ω| on GRPO/DAPO/CISPO-family trainers'
    reason: 'GMTS ranks tokens across the batch by |entropy × advantage|; CreditFilter ranks within each response'
    use_instead: method:gmts
  - when: 'first-mistake process credit (Cliff; Pitfall Step prefix/suffix)'
    reason: 'Cliff is first-error process credit, not a fork-probability entropy window'
    use_instead: method:cliff
assumptions:
  - 'DAPO host: 128 prompts × 16 responses, 400 steps, lr 1e-6, clip 0.2/0.27, overlong penalty, dynamic sampling. Qwen3-8B-Base, DAPO-17k. Mean@32, temperature 1.0, top-p 0.7, 20480-token cap. Three data seeds; Table 1 is seed 201. Code yoctta/CreditFilter (verl overlay) as of 2026-11-23.'
last_reviewed: '2026-11-23'
papers:
- paper:creditfilter
recipes:
- recipe:creditfilter
claims:
- benchmark: 'Qwen3-8B-Base DAPO-17k, three-seed late mean@32 vs DAPO'
  metric: 'MATH500 / AIME24 / AIME25 mean@32'
  value: '0.860±0.025 / 0.326±0.042 / 0.258±0.035 vs DAPO 0.783±0.107 / 0.221±0.050 / 0.167±0.032 (+7.7 / +10.5 / +9.1)'
  baseline: 'DAPO'
  date: '2026-11-23'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.27227'
  notes: 'Seed 201 late: CreditFilter 0.876/0.338/0.277 vs DAPO 0.830/0.244/0.177 vs GRPO 0.833/0.263/0.184. Equal-step tokens 2.1× DAPO (longer responses); still leads at equal tokens. One model, one prompt set, n=30 AIME. Does not retarget CISPO or GMTS.'
tags:
- rlvr
- token-credit
- dapo
- entropy
- active
---

# CreditFilter

## Method Overview
Expected forking values along a response sum to the reward variance. Fork probability decays exponentially in within-response entropy rank. CreditFilter multiplies the group advantage by an exponential window over that rank, with class-specific widths from the measured envelope, plus difficulty damping and an entropy-gated fallback to uniform credit. CreditFilter-D tracks the widths during training.

## When to Use
- Critic-free RLVR on a DAPO-style host when uniform token credit wastes updates on low-entropy execution tokens.

## When NOT to Use
Pass@1 RLVR remains `method:cispo`. Batch top-20% |E·ω| remains `method:gmts`. First-mistake prefix/suffix credit remains `method:cliff`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:math-code-rl-dense`. Distinct from GMTS (batch rank) and CISPO (the Pass@1 loss). Does **not** replace CISPO.

## Gotchas & Failure Modes
- Ranking across the batch instead of within each response loses 5–8 points vs the within-response window.
- At equal steps the method trains on ~2.1× DAPO tokens because responses grow longer; report equal-token numbers too.
- One base model, one prompt set, 30-problem AIME sets, 20480-token cap; unanswered samples count as wrong.
