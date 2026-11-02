---
id: recipe:sv-training
type: recipe
title: 'SV-Training'
method: method:sv-training
task: task:instruct-sft-alignment
target_hardware: 'Paper: SFT/distill and GRPO post-train'
framework: PyTorch
repo_url: https://github.com/tiejin98/sv_training
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- sv-training
---

# SV-Training

## Hardware & Environment Setup
- Official: `https://github.com/tiejin98/sv_training`.
- `code_status: released` as of 2026-11-02.

## Quickstart Implementation

```python
from __future__ import annotations

def sv_hook(hidden, direction, scale):
    return hidden + scale * direction

def sv_repair(adv, wrong_mask, direction_score):
    repaired = adv.clone()
    repaired[wrong_mask] = direction_score[wrong_mask]
    return repaired
```

Do not retarget locked SOTA from this recipe.
