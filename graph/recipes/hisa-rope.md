---
id: recipe:hisa-rope
type: recipe
title: Hidden Sparse Attention
method: method:hisa-rope
task: task:pretrain-dense-7b
target_hardware: 'Paper: 135M/360M from-scratch plus dense conversion'
framework: PyTorch
repo_url: https://github.com/ambroise-b/hisa
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- hisa
---

# Hidden Sparse Attention

## Hardware & Environment Setup
- Official: `https://github.com/ambroise-b/hisa`
- `code_status: released` as of 2026-11-20. Distinct from AF1's HiSA (1-bit PTQ). Does not replace SAS.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def rope_pair_keep_mask(inv_freq: torch.Tensor, max_angle: float) -> torch.Tensor:
    pair_angle = inv_freq.abs()
    keep = pair_angle <= max_angle
    if not bool(keep.any()):
        keep[pair_angle.argmin()] = True
    return keep.repeat_interleave(2)
```
