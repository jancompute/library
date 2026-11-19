---
id: paper:chorus
type: paper
title: 'Chorus: Shared N-gram Embeddings with Layer-wise Adaptation'
authors:
- Stephen Chung
- Wenyu Du
year: 2026
month: 11
arxiv_id: '2611.23386'
url: https://arxiv.org/abs/2611.23386
methods:
- method:chorus
cites: []
tags:
- ngram
- embedding
- pretrain
- memory
- active
---

# Chorus: Shared N-gram Embeddings with Layer-wise Adaptation

## Abstract Summary
Chorus stores n-grams in shared tables and rescales/projects them per layer. 1.2B tables 0.9229 BPB beat 9.6B Engram/FactorEngram (87% smaller). ClimbMix 9.6B Chorus 0.9148 vs FactorEngram 0.9258 / Engram 0.9273. FineWeb 17.1M 1.193 vs TN-gram 1.198; 133M 1.057 vs Engram 1.066 / TN-gram 1.065. DCLM 22-task 0.1240 vs TN-gram ~0.121. Ember −99.2% table-optimizer mem (1.2B: 4.47 GiB→35.7 MiB). Code dualverse-ai/chorous (typo in repo name). Does not retarget Muon2 or OLMo-3.

## Key Contributions
1. Shared n-gram tables with layer-wise rescale and project.
2. Beats 8×-larger Engram/FactorEngram tables at 1.2B.
3. Ember optimizer-state compression for the tables.

## Empirical Highlights
1.2B 0.9229 BPB vs 9.6B Engram/FactorEngram. ClimbMix 9.6B 0.9148 vs 0.9258 / 0.9273.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.23386`
- Code: `https://github.com/dualverse-ai/chorous`
