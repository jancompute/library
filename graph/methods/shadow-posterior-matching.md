---
id: method:shadow-posterior-matching
type: method
title: Shadow Posterior Matching
category: rl-algorithm
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'aligning text-to-image diffusion or flow models with rewards'
    reason: 'DiffusionOPSD / Self-OPD remain reward-alignment defaults; SPM is few-step black-box RL'
    use_instead: method:diffusion-opsd
  - when: 'few-step average-velocity diffusion RL (FewStepRL; not DiffusionOPSD default)'
    reason: 'FewStepRL ports existing hosts onto average-velocity samplers; SPM is shadow-posterior credit'
    use_instead: method:fewsteprl
  - when: 'endpoint-only fake-score DMD for few-step distill (eDMD; not DiffusionOPSD default)'
    reason: 'eDMD is endpoint fake-score DMD; SPM is reward RL on a few-step generator'
    use_instead: method:edmd
  - when: 'intrinsic distribution matching / EMA moment constraint on DMD (IDM)'
    reason: 'IDM is DMD plus EMA moments; SPM is shadow-posterior reward credit'
    use_instead: method:idm
assumptions:
  - '4-step DMD2 generator on SD3.5-Medium. LoRA rank 32, α=γ=0.1, 1,000 iterations, 8×H100. Slug is shadow-posterior-matching because method:bpo already uses PMD. Code shadow-posterior/code as of 2026-11-20.'
last_reviewed: '2026-11-20'
papers:
- paper:shadow-posterior-matching
recipes:
- recipe:shadow-posterior-matching
claims:
- benchmark: 'SD3.5-Medium 4-step vs RTDMD / TDM-R1'
  metric: 'GenEval / OCR / PickScore'
  value: '0.94 / 0.96 / 23.84 vs strongest 4-step baseline 0.86 / 0.95 / 23.36; 10/15 DrawBench pairs'
  baseline: 'RTDMD / TDM-R1 on the same 4-step DMD2 init'
  date: '2026-11-20'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.25998'
  notes: 'Does not retarget method:diffusion-opsd / method:self-opd / method:fewsteprl / method:edmd. Distinct from method:bpo (Policy Mirror Descent).'
tags:
- diffusion
- few-step
- rl
- posterior-matching
- active
---

# Shadow Posterior Matching

## Method Overview
SPM renoises a few-step generator's samples into shadow inputs, correlates black-box rewards with the shadow posterior, and regresses a teacher-anchor plus endpoint-matching term so every call, including the last, receives credit without a fitted reward proxy.

## When to Use
- Few-step image RL when the reward is black-box (GenEval / OCR / PickScore) and multi-step Flow-GRPO-style credit would blur samples or skip the final call.

## When NOT to Use
Multi-step / native-window reward alignment remains `method:diffusion-opsd` / `method:self-opd`. Average-velocity host ports remain `method:fewsteprl`. Endpoint DMD remains `method:edmd`. LLM Policy Mirror Descent remains `method:bpo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:posttrain-diffusion`. Does **not** replace DiffusionOPSD, Self-OPD, FewStepRL, or eDMD.

## Gotchas & Failure Modes
- Tilting temperature α trades reward vs quality: α=0.01 can collapse ImageReward; α=1 under-optimizes OCR.
- Needs the undistilled teacher and a fake score trained on generator samples.
- 4-step SD3.5-M only; not a DiffusionOPSD bake-off.
