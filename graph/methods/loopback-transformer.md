---
id: method:loopback-transformer
type: method
title: Loopback Transformer
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'choosing the ~7B dense pretrain optimizer'
    reason: 'Muon2 remains the ~7B optimizer; Loopback is a residual looped architecture'
    use_instead: method:muon2
  - when: 'elastic mixed-depth looped LM (gated state update / mixed loop counts)'
    reason: 'ELR remains mixed-depth elastic recurrence; Loopback stores residual updates and reads them with geometric decay plus attention'
    use_instead: method:elr
  - when: 'multi-stream attention residuals vs vanilla / mHC / AttnRes (MSAR)'
    reason: 'MSAR is a residual topology; Loopback is a looped residual-update memory'
    use_instead: method:msar
assumptions:
  - 'Dense NTP pretrain on ClimbMix with training tokens and executed depth matched to a standard Transformer. Code released at yancyou/Loopback as of 2026-11-16.'
last_reviewed: '2026-11-16'
papers:
- paper:loopback-transformer
recipes:
- recipe:loopback-transformer
claims:
- benchmark: 'ClimbMix val loss, 191M/374M/778M, 40-75% Transformer params excluding embeddings and lm_head; tokens and executed depth matched'
  metric: 'validation CE'
  value: '191M 2.6187 vs Standard 2.6234; 374M 2.4008 vs 2.4395; 778M 2.2404 vs 2.2644; lowest among Standard plus seven looped residual designs'
  baseline: 'Standard Transformer; seven looped residual designs'
  date: '2026-11-16'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.07226'
  notes: 'Does not retarget method:muon2 or method:elr. Sibling of method:msar / method:simplehc. HF Daily leftover 2611.07226.'
- benchmark: 'ClimbMix 3B; WikiText ppl; 13-task mean; extra loop visits'
  metric: 'WikiText ppl; 13-task mean accuracy'
  value: 'WikiText 16.74 vs Standard 17.28; 13-task mean 49.45%; extra visits 50.17% vs a larger loss rise on Plain Loop'
  baseline: 'Standard Transformer; Plain Loop'
  date: '2026-11-16'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.07226'
  notes: 'Word-problem acc 2.6%→6.4% at 3B. Does not retarget Muon2.'
tags:
- architecture
- looped-lm
- residual
- active
---

# Loopback Transformer

## Method Overview
Loopback stores each block's residual update instead of the full block output, keeps the shared stack's input on a separate path, and reads the stored updates with geometric decay plus an attention allocator. The decay sets total update weight and a recency prior; attention allocates that weight. Parameter sharing alone does not decide how repeated computation is reused.

## When to Use
- Residual looped pretrain when you want fewer Transformer parameters at matched tokens and executed depth.

## When NOT to Use
~7B optimizer remains `method:muon2`. Mixed-depth elastic loops remain `method:elr`. Residual topology without looping remains `method:msar` / `method:simplehc`. Teacher folding into a student remains `method:concertina`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:llm-pretraining-optimization`. Mention on `task:elastic-depth-looped-lm`. Does **not** replace Muon2, MSAR, or ELR.

## Gotchas & Failure Modes
- Gains are vs a Standard Transformer at matched executed depth, not vs Muon2 as an optimizer.
- Extra visits help less on Loopback than on Plain Loop, but they are not a free lunch.
- Code: `https://github.com/yancyou/Loopback` (`code_status: released`).
