---
id: method:gated-loop-moe
type: method
title: Gated-Loop MoE
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'compute-matched MoE looping of middle layers (FLOPs/params/KV matched)'
    reason: 'SMELT remains the matched-budget first hop; Gated-Loop MoE reallocates Core depth into extra experts'
    use_instead: method:smelt
  - when: 'elastic mixed-depth looped LM (gated state update / mixed loop counts)'
    reason: 'ELR varies loop count on dense models; Gated-Loop MoE is a gated Core plus extra experts'
    use_instead: method:elr
  - when: 'recurrent CED-style architecture, not a harness kernel'
    reason: 'RLT is experimental CED; Gated-Loop MoE is an MoE Core loop'
    use_instead: method:recurrent-looped-transformer
  - when: 'KV-as-memory looping / U-MoLT encoder-decoder readout (MoLT)'
    reason: 'MoLT reuses KV as loop memory; Gated-Loop MoE gates inner-loop state and buys experts'
    use_instead: method:molt
  - when: 'choosing the frontier MoE architecture template'
    reason: 'DeepSeek-V4 / Kimi-K3 remain the MoE template; this is an optional looped-MoE recipe'
    use_instead: method:deepseek-v4
assumptions:
  - 'Gated inner-loop updates plus Prelude-to-Coda residual. Core 25–35% of unrolled depth; extra routed experts from saved params. 1T-token 69B MLA / 51B KDA vs budget-matched non-recurrent. 200B PPL vs named looped methods is not SMELT Chinchilla protocol. GitHub announced URL 404 as of 2026-11-26.'
last_reviewed: '2026-11-26'
papers:
- paper:gated-loop-moe
recipes:
- recipe:gated-loop-moe
claims:
- benchmark: '1T-token Gated-Loop MoE vs budget-matched non-recurrent'
  metric: 'downstream pp'
  value: '69B MLA +1.16pp; 51B KDA +2.29pp'
  baseline: 'budget-matched non-recurrent MoE'
  date: '2026-11-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.34276'
  notes: 'Core 25–35% of unrolled depth. Does not retarget SMELT, ELR, RLT, or DeepSeek-V4.'
- benchmark: '200B-token reproduction vs other looped methods named in the listing'
  metric: 'PPL vs named looped recipes'
  value: 'lower PPL than other looped methods (listing names Parcae and SMELT)'
  baseline: 'named looped methods at 200B'
  date: '2026-11-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.34276'
  notes: 'Not SMELT Chinchilla protocol. GitHub announced URL 404. Does not retarget SMELT.'
tags:
- architecture
- moe
- looped
- active
---

# Gated-Loop MoE

## Method Overview
Gated-Loop MoE loops a Core block with gated inner-loop state updates and a Prelude-to-Coda residual. The Core is 25–35% of unrolled depth. Parameters saved by not unrolling the rest of the stack buy extra routed experts under the same budget.

## When to Use
- Looped MoE pretrain where you want to spend saved Core depth on extra experts rather than SMELT-style matched middle-layer visits.

## When NOT to Use
Compute-matched looped-MoE first hop remains `method:smelt`. Mixed-depth dense looping remains `method:elr`. Experimental CED remains `method:recurrent-looped-transformer`. KV-as-memory looping remains `method:molt`. Frontier MoE template remains `method:deepseek-v4`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:compute-matched-moe-looped-pretrain` with a mention on `task:elastic-depth-looped-lm`. Distinct from SMELT / ELR / MoLT / RLT / LatentLoop. The 200B PPL listing is not SMELT's Chinchilla protocol. Does **not** replace SMELT, ELR, RLT, or DeepSeek-V4 / Kimi-K3.

## Gotchas & Failure Modes
- GitHub announced URL 404 as of 2026-11-26 (`code_status: announced`).
- Do not treat 200B PPL vs named looped methods as a SMELT bake-off.
- Core fraction 25–35% is a recipe choice, not mixed-depth ELR.
