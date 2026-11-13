---
id: method:soscale
type: method
title: SoScale
category: quantization
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'native FP4 forward/backward hardware training from scratch'
    reason: 'Quartet-II remains native FP4 training; SoScale is Hessian-aware PTQ scale-code search plus GPTQ recovery'
    use_instead: method:quartet-ii
  - when: 'dual-scale calibration-free W+A PTQ for AR LLMs (not native FP4 training)'
    reason: 'DualQuant is calibration-free dual-scale reconstruction; SoScale searches hierarchical FP4 scale codes'
    use_instead: method:dualquant
  - when: 'activation-residual compensation for W+A PTQ (ResCom; not native FP4 training)'
    reason: 'ResCom is closed-form residual compensation; SoScale is Hessian-aware scale search'
    use_instead: method:rescom
assumptions:
  - 'W4A4 PTQ on MXFP4 / NVFP4 / HiF4 with a calibrated checkpoint and GPTQ recovery. Paper: Qwen3-14B. No public code as of 2026-11-13.'
last_reviewed: '2026-11-13'
papers:
- paper:soscale
recipes:
- recipe:soscale
claims:
- benchmark: 'Qwen3-14B W4A4 MXFP4/NVFP4/HiF4 vs BF16 avg; vs strongest non-SoScale and local ScaleSearch'
  metric: 'retained BF16 average; pp vs PTQ baselines'
  value: 'retains 97.17%/99.20%/99.40% of BF16 avg under MXFP4/NVFP4/HiF4; +0.21–0.77 vs strongest non-SoScale; +0.47–1.10 vs local ScaleSearch'
  baseline: 'max-abs FP4 scales / ScaleSearch / DualQuant-family PTQ'
  date: '2026-11-13'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.16426'
  notes: 'Does not retarget method:quartet-ii. Distinct from method:dualquant and method:rescom. No public code.'
tags:
- quantization
- fp4
- ptq
- active
---

# SoScale

## Method Overview
SoScale is Hessian-aware search over hierarchical FP4 scale codes, then GPTQ recovery. Default max-abs scaling is a poor match to MXFP4 / NVFP4 / HiF4 block or tree scales. On Qwen3-14B W4A4 it keeps 97.17% / 99.20% / 99.40% of the BF16 average under those three formats.

## When to Use
- W4A4 PTQ on MXFP4 / NVFP4 / HiF4 where scale-code assignment, not the payload grid, is the remaining error.

## When NOT to Use
Native FP4 training remains `method:quartet-ii`. Calibration-free dual-scale PTQ remains `method:dualquant`. Activation-residual PTQ remains `method:rescom`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:fp4-hardware-training`. Does **not** replace Quartet-II.

## Gotchas & Failure Modes
- Needs a Hessian / second-order probe plus GPTQ; not calibration-free.
- This is inference PTQ, not NVFP4 hardware training.
- No public code as of 2026-11-13.
