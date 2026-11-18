---
id: method:gaze-rl
type: method
title: Gaze-RL
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'region-level RL / fine-grained MLLM perception (RoI proposal)'
    reason: 'Vision-RL2 trains a RoI head; Gaze-RL reallocates completion-level advantage from internal cross-modal geometry'
    use_instead: method:vision-rl2
  - when: 'cycle GRPO coupling region understanding and localization (CycleGRPO)'
    reason: 'CycleGRPO couples understand+localize; Gaze-RL is a mean-one landing field on the same outcome reward'
    use_instead: method:cyclegrpo
  - when: 'online adaptive prompt selection / teacher scaffolding for image/VL GRPO'
    reason: 'EPS rewrites prompts; Gaze-RL does not change the prompt curriculum'
    use_instead: method:eps-prompt-scaffolding
  - when: 'video annotation-as-rollout / fine-grained video perception RL'
    reason: 'OraRL is annotation-as-rollout; Gaze-RL is token credit on a shared GRPO host'
    use_instead: method:orarl
assumptions:
  - 'MLLM GRPO/DAPO host with visual tokens. Paper: Qwen2.5-VL-3B/7B and InternVL3.5-8B; 35% ViRL39K / 65% Video-R1; 200 updates. Code lixuan27/Gaze-RL-main released as of 2026-11-18.'
last_reviewed: '2026-11-18'
papers:
- paper:gaze-rl
recipes:
- recipe:gaze-rl
claims:
- benchmark: 'Qwen2.5-VL-7B Geometry3K / MathVista vs GRPO / DAPO'
  metric: 'accuracy'
  value: 'Geometry3K 36.8→47.9 vs GRPO 39.6 / DAPO 41.9; MathVista 67.2→70.4 vs GRPO 68.6'
  baseline: 'GRPO / DAPO / VPPO'
  date: '2026-11-18'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.22438'
  notes: 'Does not retarget method:vision-rl2. Mentions on task:rl-video-mllm / task:mllm-rl-prompt-curriculum. Code lixuan27/Gaze-RL-main.'
tags:
- multimodal-rl
- credit-assignment
- vision
- active
---

# Gaze-RL

## Method Overview
Gaze-RL builds a mean-one latent reward landing field \(\varphi_t\) from internal cross-modal geometry and predictive entropy, then sets \(\widetilde{A}_t=((1-\gamma)+\gamma\varphi_t)\widehat{A}\). Total rollout credit is preserved; only positionwise allocation changes. No process labels or extra perception head.

## When to Use
- Image/video MLLM RL where the same outcome reward should land on visually anchored, high-entropy tokens.

## When NOT to Use
Region proposal remains `method:vision-rl2`. Understand+localize cycle remains `method:cyclegrpo`. Prompt scaffolding remains `method:eps-prompt-scaffolding`. Video annotation-as-rollout remains `method:orarl`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:mllm-finegrained-perception-rl`. Mentions on `task:rl-video-mllm` and `task:mllm-rl-prompt-curriculum`. Does **not** replace Vision-RL2.

## Gotchas & Failure Modes
- Host is visual-evidence credit, not a prompt curriculum and not OraRL annotation-as-rollout.
- Mean-one field is load-bearing; dropping visual support or entropy both hurt in the paper ablation.
