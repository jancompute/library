---
id: task:rl-video-mllm
type: task
title: "Reinforcement Learning for Video Multimodal LLMs"
domain: "video-mllm"
summary: "Sample-efficient reinforcement learning and post-training for unified video multimodal large language models without costly chain-of-thought generation."
scope: "Video MLLM RL for temporal grounding, tracking, segmentation, and video QA, especially annotation-as-rollout without costly CoT."
out_of_scope:
  - "General image / multimodal reasoning RL prompt curriculum (not video annotation-as-rollout)"
  - "Dense text Pass@1 RLVR"
  - "Region-level image perception RL (Vision-RL2)"
redirects:
  - when: "turn-level GRPO remaining-return + turn-mean loss for streaming video (TurnWise)"
    to: "method:turnwise"
  - when: "multi-frame video GRPO / complementary frame sets (FrameGRPO)"
    to: "method:framegrpo"
  - when: "general image/multimodal reasoning RL prompt curriculum (not video OraRL)"
    to: "task:mllm-rl-prompt-curriculum"
  - when: "image region-proposal RL (not video annotation-as-rollout)"
    to: "task:mllm-finegrained-perception-rl"
  - when: "dense/sparse paired-view video RL with grounding + reliability-gated reference reward (SAVER)"
    to: "method:saver"
current_sota:
  - method: method:orarl
    as_of: "2026-08-27"
    benchmark: "TimeLens / GOT-10k / RefCOCO / MeViS / VSI-Bench"
    metric: "perception accuracy & step efficiency"
    value: "Video-ORA-9B achieves 66.0 mIoU, 78.2 AO, 73.1 VSI-Bench at 2.2x SFT step time"
    notes: "OraRL (2608.20492) decouples oracle baseline to prevent advantage inversion and applies sign-balanced pruning."
methods:
  - method:turnwise
  - method:framegrpo
  - method:saver
  - method:orarl
  - method:sapo
  - method:grpo
  - method:eps-prompt-scaffolding
  - method:vision-rl2
last_reviewed: '2026-11-05'
tags:
  - video-mllm
  - multimodal-rl
  - post-training
  - reinforcement-learning
---

# Reinforcement Learning for Video Multimodal LLMs

## Problem Definition
Post-training multimodal large language models for fine-grained video perception (temporal grounding, object tracking, spatial segmentation, long-form video QA) is severely sample-starved under standard on-policy group RL. Rollouts rarely generate exact bounding coordinates or timestamps, while chain-of-thought (CoT) expands token length and training latency without proportional precision gains.

## SOTA Recommendation (as of 2026-08-27)
- **Primary Method**: **OraRL** (`method:orarl`, `paper:orarl` `arXiv:2608.20492`) for annotation-as-rollout with decoupled advantage estimation and sign-balanced pruning.
- **Not This Task**: general image/multimodal reasoning RL prompt curriculum is `method:eps-prompt-scaffolding` on `task:mllm-rl-prompt-curriculum`. Region-level image perception RL is `method:vision-rl2` on `task:mllm-finegrained-perception-rl`. OraRL is unchanged.
- **Optional dense/sparse paired-view video RL (not this first hop)**: `method:saver` (`arXiv:2610.10893`) grounding + reliability-gated reference reward on 1,250 Time-R1 examples. Qwen3.5-2B 0.1fps mIoU 18.4→30.0; QA 45.9→50.8. Code lmsdss/SAVER. Does not replace OraRL.
- **Optional multi-frame video GRPO**: `method:framegrpo` (`arXiv:2610.26022`). Complementary frame sets plus gated temporal credit. Does not replace OraRL.
- **Optional streaming turn-level GRPO**: `method:turnwise` (`arXiv:2611.06728`). Remaining-return credit plus turn-mean loss. Qwen2.5-VL-3B 43.56 / 21.59 / 49.43; Qwen3-VL-4B 42.44 / 11.15 / 58.96. Code announced, no URL. Does not replace OraRL.
