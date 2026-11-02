---
id: recipe:fair-cast
type: recipe
title: 'Fair Cast'
method: method:fair-cast
task: task:fp4-rl-train-rollout-alignment
target_hardware: 'Paper: Qwen3-0.6B to 4B RL export'
framework: PyTorch
repo_url: https://github.com/andrewgcodes/faircast
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- fair-cast
---

# Fair Cast

## Hardware & Environment Setup
- Official: `https://github.com/andrewgcodes/faircast`.
- `code_status: released` as of 2026-11-02.

## Quickstart Implementation

```python
from __future__ import annotations
import torch

def fair_cast(master):
    delta = master.float() - master.to(torch.bfloat16).float()
    scale = (master.abs() / 128).clamp_min(torch.finfo(torch.bfloat16).eps)
    noise = (torch.rand_like(master) - 0.5) * scale
    return (master + noise).to(torch.bfloat16)
```

Do not retarget locked SOTA from this recipe.
