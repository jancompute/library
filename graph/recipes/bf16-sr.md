---
id: recipe:bf16-sr
type: recipe
title: 'BF16+SR'
method: method:bf16-sr
task: task:fp4-rl-train-rollout-alignment
target_hardware: 'NVIDIA mixed-precision RLVR: FP32 shadow, BF16 rollout/train copy'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- bf16-sr
---

# BF16+SR

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-11. Apply SR when copying FP32 shadow weights into the BF16 tensors used for rollout and the forward/backward. Forward-pass SR is sufficient.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def stochastic_round_to_bf16(w: torch.Tensor) -> torch.Tensor:
    w_m = w.to(torch.bfloat16).float()
    w_p = torch.nextafter(w_m, torch.where(w >= w_m, w_m + 1, w_m - 1))
    ulp = (w_p - w_m).abs().clamp_min(torch.finfo(w.dtype).tiny)
    prob = ((w - w_m).abs() / ulp).clamp(0, 1)
    pick_far = torch.rand_like(w) < prob
    return torch.where(pick_far, w_p, w_m).to(torch.bfloat16)
```

Do not retarget locked SOTA from this recipe.
