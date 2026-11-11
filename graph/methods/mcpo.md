---
id: method:mcpo
type: method
title: 'MCPO (Margin-Credit Policy Optimization)'
category: rl-algorithm
status: active
sota_for: []
supersedes: []
do_not_use_for:
    - when: 'single-turn dense math/code Pass@1 RLVR'
      reason: 'CISPO remains Pass@1; MCPO redistributes GRPO token advantages by top-2 margin'
      use_instead: method:cispo
    - when: 'first-mistake process credit (Pitfall Step prefix/suffix)'
      reason: 'Cliff is first-error token credit; MCPO scores hesitation, not the first mistake'
      use_instead: method:cliff
    - when: 'asymmetric entropy×sign exploration credit'
      reason: 'EAPO is entropy×sign; MCPO is a top-2-margin reweight of the same GRPO advantage'
      use_instead: method:eapo
assumptions:
    - 'GRPO host. Top-2 margin from the old-policy forward the trainer already runs. Paper: MiniCPM5-2B-Base and Qwen3-4B-Base, LoRA, 200 steps, DAPO-Math. No dedicated public trainer as of 2026-11-11. arXiv 2611.14015 above watermark 2611.12886. Pair with paper:dense-rewards-grpo: Monte-Carlo process rewards can lose at matched tokens; MCPO adds no extra tokens.'
last_reviewed: '2026-11-11'
papers:
- paper:mcpo
recipes:
- recipe:mcpo
claims:
- benchmark: 'MiniCPM5-2B-Base / Qwen3-4B-Base six-bench competition-math macro avg@32'
  metric: 'pp vs unmodified GRPO'
  value: 'MiniCPM5-2B +6.55 (95% CI [4.1, 9.0], 5/5 seeds); Qwen3-4B +4.75 (3/3 seeds); pass@32 +13.8'
  baseline: 'unmodified GRPO (same sampling, clip, length handling)'
  date: '2026-11-11'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.14015'
  notes: 'Does not retarget method:cispo. Answers 2–3× longer; paper does not separate length from accuracy. No extra model eval and no batch statistics.'
tags:
- rlvr
- token-credit
- margin
- grpo
- active
---

# MCPO (Margin-Credit Policy Optimization)

## Method Overview
MCPO keeps the GRPO group advantage $A_i$ and redistributes it over tokens by the old-policy top-2 margin $M=p_1-p_2$. A close call ($M\le 0.3$) gets score $h=1$; a clear winner ($M\ge 0.9$) gets $h=0$. Positive-advantage completions put more credit on close calls; negative ones put more penalty on confident tokens. The mean token advantage stays $A_i$. The margin is read from the trainer's existing old-policy forward pass.

## When to Use
- GRPO/CISPO-family math RLVR where uniform token credit wastes updates on tokens that were never in doubt, and you will not pay extra generated tokens for a process reward.

## When NOT to Use
Pass@1 default remains `method:cispo`. First-mistake credit remains `method:cliff`. Entropy×sign remains `method:eapo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:math-code-rl-dense`. Does **not** replace CISPO. Pair with `paper:dense-rewards-grpo`: dense Monte-Carlo process rewards can lose at matched tokens; MCPO does not sample continuations.

## Gotchas & Failure Modes
- No dedicated public trainer (`code_status: none`). Overlay on a GRPO host.
- Length and accuracy move together; the paper does not separate them.
- Sibling of Cliff / EAPO / GMTS, not a replacement.
