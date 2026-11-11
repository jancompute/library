---
id: method:steerdistill
type: method
title: 'SteerDistill'
category: quantization
status: active
sota_for: []
supersedes: []
do_not_use_for:
    - when: 'deployed checkpoint must stay NF4/INT4/MXFP4 with no high-precision adapter'
      reason: 'GradCodeS remains the fully low-bit FT first hop; SteerDistill is W4A16 agent QAT via closed-loop teacher steering'
      use_instead: method:gradcodes
    - when: 'ultra-low-bit QAT recovery via on-policy reverse-KL'
      reason: 'OnlineQAT is reverse-KL QAT; SteerDistill constructs locally verified behavioral corrections then distills them'
      use_instead: method:onlineqat
    - when: 'QAT recovery via self-generated trajectories (Right On Q)'
      reason: 'Right On Q is trajectory QAT; SteerDistill steers failed agent turns with a BF16 teacher'
      use_instead: method:right-on-q
assumptions:
    - 'W4A16/W2A16 quantized agent with a frozen BF16 teacher of the same checkpoint. Code air-embodied-brain/SteerDistill released. Paper: Qwen3-8B and two other models, five agentic benches. arXiv 2611.13410 above watermark 2611.12886.'
last_reviewed: '2026-11-11'
papers:
- paper:steerdistill
recipes:
- recipe:steerdistill
claims:
- benchmark: 'Five agentic benches, three models, W4A16'
  metric: 'mean score vs strongest quantized baseline / BF16'
  value: 'beats strongest quantized baseline by 1.67–2.18; within 1.0 of BF16; τ²-Bench vs QeRL +1.84 pp at 67% fewer GPU-h'
  baseline: 'strongest quantized baseline / QeRL / BF16 teacher'
  date: '2026-11-11'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.13410'
  notes: 'Does not retarget method:gradcodes or method:onlineqat. Unguided retries correct only 9.6% of divergent turns; steering raises Pass@4 to 82.3%. Inference has no teacher hook.'
tags:
- quantization
- qat
- agents
- distillation
- active
---

# SteerDistill

## Method Overview
SteerDistill is quantization-aware distillation for tool-using agents. A frozen BF16 teacher localizes the first environment-transition divergence, prompts the quantized student to revise that turn, and refines the prompt from execution feedback until the transition matches a successful teacher reference. Distillation then matches the steered student at corrected turns and the BF16 teacher elsewhere, with no guidance at inference. W4A16 stays within $1$ point of BF16 on five agentic benches.

## When to Use
- W4A16 (or W2A16) deployment of a multi-turn agent where vanilla QAT or logit KD leaves a task-success gap to BF16.

## When NOT to Use
Fully low-bit FT remains `method:gradcodes`. Reverse-KL QAT remains `method:onlineqat`. Trajectory QAT remains `method:right-on-q`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:full-lowbit-finetune`. Does **not** replace GradCodeS or OnlineQAT.

## Gotchas & Failure Modes
- Needs a frozen BF16 teacher and successful teacher references for failed tasks.
- Do not ship the steering prompt; internalization trains without $G$.
- Sibling of Right On Q / OnlineQAT / Harness-Zero, not a replacement.
