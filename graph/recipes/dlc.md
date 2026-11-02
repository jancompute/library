---
id: recipe:dlc
type: recipe
title: 'DLC'
method: method:dlc
task: task:fp4-rl-train-rollout-alignment
target_hardware: 'Paper: Qwen3-0.6B / 1.7B disaggregated RL'
framework: PyTorch
repo_url: https://github.com/Skylanding/Training-Inference-Mismatch
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- dlc
---

# DLC

## Hardware & Environment Setup
- Official: `https://github.com/Skylanding/Training-Inference-Mismatch`.
- `code_status: released` as of 2026-11-02.

## Quickstart Implementation

```python
from __future__ import annotations

def dlc_step(disc, lag_ratio, ess, ess_min=0.5):
    centered = disc - disc.mean()
    clipped = lag_ratio.clamp(0.2, 5.0)
    return centered, clipped, ess < ess_min
```

Do not retarget locked SOTA from this recipe.
