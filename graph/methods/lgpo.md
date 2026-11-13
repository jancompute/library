---
id: method:lgpo
type: method
title: LGPO
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'single-turn dense math/code Pass@1 RLVR'
    reason: 'CISPO remains Pass@1; LGPO is a GRPO-host likelihood gate that drops the old-policy logp pass'
    use_instead: method:cispo
  - when: 'exact-KL prefix importance-ratio clipping (EPIC)'
    reason: 'EPIC clips prefix reverse-KL; LGPO gates on current-policy likelihood and skips old-policy logp'
    use_instead: method:epic
  - when: 'cancellation-aware off-policy response mask (absolute token log-ratios)'
    reason: 'CARM is an off-policy sequence mask; LGPO is on-policy likelihood gating'
    use_instead: method:carm
assumptions:
  - 'Fully on-policy GRPO-family RLVR where the importance ratio is identically 1 and old-policy logp is paid only for the clip. No public trainer as of 2026-11-13.'
last_reviewed: '2026-11-13'
papers:
- paper:lgpo
recipes:
- recipe:lgpo
claims:
- benchmark: 'Qwen2.5-3B GRPO-family train time per epoch; on-policy ratio clip'
  metric: 'hours/epoch; ratio-clip activity when ratio=1'
  value: '3.37h→2.85h/epoch (~18%); ratio clip is a no-op when sampler=trainer; τ near top 10–20% likelihood quantile'
  baseline: 'GRPO with old-policy likelihoods'
  date: '2026-11-13'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.15404'
  notes: 'Does not retarget method:cispo. Sibling of method:epic / method:carm. No public code.'
tags:
- rlvr
- grpo
- on-policy
- active
---

# LGPO

## Method Overview
LGPO (Likelihood-Gated Policy Optimization) keeps a soft trust region by gating tokens on current-policy likelihood instead of clipping an importance ratio. When the sampler and trainer are the same policy the GRPO ratio is 1 and ratio-clip does nothing; LGPO still withholds low-likelihood tokens. The old-policy likelihood pass can be dropped.

## When to Use
- Fully on-policy GRPO-family RLVR where old-policy logp is paid only for a clip that never fires.

## When NOT to Use
Pass@1 remains `method:cispo`. Prefix reverse-KL clip remains `method:epic`. Off-policy sequence masks remain `method:carm`. Async stragglers remain `method:sao`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:math-code-rl-dense`. Does **not** replace CISPO.

## Gotchas & Failure Modes
- $\tau$ near the top 10–20% likelihood quantile; too tight a gate starves the update.
- Off-policy or stale-sampler RL still needs a real IS ratio (CISPO / CARM / EPIC).
- No public trainer as of 2026-11-13.
