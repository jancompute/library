---
id: paper:lstm-looped-kv
type: paper
title: 'LSTM-Style Looped Transformers with Shared KV Caches'
authors:
- 'Andreas Kirsch'
year: 2026
month: 10
arxiv_id: '2610.33360'
url: https://arxiv.org/abs/2610.33360
methods:
- method:lstm-looped-kv
cites:
- paper:recurrent-looped-transformer
- paper:looped-models-done-right
tags:
- looped-lm
- active
---

# LSTM-Style Looped Transformers with Shared KV Caches

## Abstract Summary
LSTM-style looped transformer shares one KV cache across the recurrent core. Parallel train vs recursive continuation mismatch is closed with a consistency loss in the last 10% of tokens.

## Key Contributions
1. LSTM-style shared-KV looping as an active plug-in on task:recurrent-encoder-decoder-lm.

## Empirical Highlights
Width 1024: 40.4% fewer params at matched FLOPs; cache sets 15 to 4. Consistency loss removes 81-89% of the continuation-loss penalty. Does not retarget method:recurrent-looped-transformer.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.33360`
- Code: `none found (`code_status: none`).`
