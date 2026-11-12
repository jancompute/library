---
id: method:physopsd
type: method
title: PhysOPSD
category: diffusion-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'aligning text-to-image diffusion or flow models with rewards'
    reason: 'DiffusionOPSD remains the T2I OPSD default; PhysOPSD is code-as-privilege video OPSD'
    use_instead: method:diffusion-opsd
  - when: 'teacher-free flow matching multi-objective alignment (Self-OPD)'
    reason: 'Self-OPD is teacher-free flow matching; PhysOPSD uses a compiled-code privileged teacher'
    use_instead: method:self-opd
  - when: 'privileged-teacher OPSD / gold-solution self-distillation'
    reason: 'VISTA remains gold-solution text OPSD; PhysOPSD is video with executable physics code as privilege'
    use_instead: method:vista
  - when: 'video annotation-as-rollout / fine-grained video perception RL'
    reason: 'OraRL is video MLLM perception RL; PhysOPSD is video-generation OPSD'
    use_instead: method:orarl
assumptions:
  - 'Video diffusion/flow generators with an executable physics compiler. PhysOPSD-Engine + PhysOPSD-3K. Code aigc3d/PhysOPSD released. HF Daily leftover below the 11-11 watermark. arXiv 2611.12411.'
last_reviewed: '2026-11-12'
papers:
- paper:physopsd
recipes:
- recipe:physopsd
claims:
- benchmark: 'UniVideo 13B / OmniWeaving 8.3B VideoPhy-2 / VBench, PhysOPSD-3K'
  metric: 'VideoPhy-2 overall / PhyGround / VBench vs SFT 80K / offline RL 21K'
  value: 'VideoPhy-2 overall +4.2 / +4.1; PhyGround +1.6 / +3.4; VBench UniVideo 83.5→84.0; 3K samples vs SFT 80K / offline RL 21K'
  baseline: 'SFT / offline RL / vanilla OPSD without compiled physics'
  date: '2026-11-12'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.12411'
  notes: 'Does not retarget method:diffusion-opsd, method:self-opd, or method:vista. Code aigc3d/PhysOPSD. Distinct from method:scope-t2i / method:rewardverse.'
tags:
- diffusion
- opsd
- video
- active
---

# PhysOPSD

## Method Overview
PhysOPSD is privileged on-policy self-distillation for video generation. A compiler turns scene code into a physical context the teacher sees and the student does not. Dual-level privilege (global + token-wise) plus shared-noise variation trains the student to match the teacher's physically plausible path without seeing the code at inference.

## When to Use
- Video generators that need physical plausibility, when you can compile scene code into a privileged teacher and train on a small PhysOPSD-style set.

## When NOT to Use
T2I reward alignment remains `method:diffusion-opsd` / `method:self-opd`. Gold-solution text OPSD remains `method:vista`. Video MLLM perception RL remains `method:orarl`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:posttrain-diffusion`. Mention on `task:privileged-teacher-opsd`. Does **not** replace DiffusionOPSD, Self-OPD, or VISTA.

## Gotchas & Failure Modes
- Privilege is compiled physics, not a gold video. Without a compiler the method is ordinary OPSD.
- 3K samples assume the PhysOPSD-Engine pipeline, not a generic video SFT mix.
