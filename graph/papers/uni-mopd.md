---
id: paper:uni-mopd
type: paper
title: 'Strong Starts, Simple Recipes: Unified Multi-Teacher On-Policy Distillation from Multimodal Specialists'
authors:
- Wenzheng Chang
- Taiqiang Wu
- Yuqi Xu
- Yongfu Zhu
- Zelin Peng
- Ji Zhao
- Shuai Dong
- Wenpu Liu
- Caoyuan Ma
- Xuehui Wang
- Ziyue Wang
- Weichu Xie
- Haiyuan Wan
- Ngai Wong
- Tong He
- Wenqi Shao
- Jiaqi Wang
year: 2026
month: 11
arxiv_id: '2611.34397'
url: https://arxiv.org/abs/2611.34397
methods:
- method:uni-mopd
cites: []
tags:
- distillation
- mopd
- merge
---

# Strong Starts, Simple Recipes: Unified Multi-Teacher On-Policy Distillation from Multimodal Specialists

## Abstract Summary
Uni-MOPD treats the student init as the design variable: uniform-merge same-base specialists, then short full-vocabulary reverse-KL MOPD with uniform domain sampling. The merge already matches 200 MOPD updates on the base before any training. Distinct from BaC-MOPD (error-replay plus balanced reverse-KL after merge) and from training-free OPD (no update). Paper Open-MOPD numbers are not the library 83.4% bake-off.

## Key Contributions
1. Uniform merge as the MOPD start, not as the final model.
2. Short MOPD with uniform sampling and full-vocab reverse KL; no schedules, token weights, or truncation.
3. Five multimodal domains / 19 benches; 3.3× faster than released Open-MOPD code.

## Empirical Highlights
Before training, uniform merge matches 200 MOPD updates on the base. Short distillation recovers remaining specialist gaps. Outperforms Open-MOPD at the same budget at 3.3× wall-clock vs its released code. Checkpoints on Hugging Face; train framework announced.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.34397`
- Checkpoints: `https://huggingface.co/AmberHeart/Uni-MOPD`
- Train code: announced, not released as of 2026-11-26
