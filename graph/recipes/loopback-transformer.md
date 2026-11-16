---
id: recipe:loopback-transformer
type: recipe
title: Loopback Transformer
method: method:loopback-transformer
task: task:llm-pretraining-optimization
target_hardware: 'Paper: ClimbMix 191M–3B residual looped pretrain'
framework: PyTorch
repo_url: https://github.com/yancyou/Loopback
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- loopback-transformer
---

# Loopback Transformer

## Hardware & Environment Setup
- Official: `https://github.com/yancyou/Loopback` (`code_status: released`).
- Store residual updates, not full block outputs. Geometric decay sets total update weight; attention allocates it. Match tokens and executed depth to the Standard Transformer baseline.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def loopback_read(updates: torch.Tensor, decay: float) -> torch.Tensor:
    t = updates.size(0)
    weights = decay ** torch.arange(t - 1, -1, -1, device=updates.device, dtype=updates.dtype)
    weights = weights / weights.sum().clamp_min(1e-8)
    return (weights[:, None, None] * updates).sum(dim=0)
```

Do not retarget locked SOTA from this recipe.
