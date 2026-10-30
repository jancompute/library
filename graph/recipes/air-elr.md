---
id: recipe:air-elr
type: recipe
title: 'AIR (Affine Inverse-square-Root ELR)'
method: method:air-elr
task: task:llm-pretraining-optimization
target_hardware: 'Paper: 128B-token MoE pretrain'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- air-elr
---

# AIR (Affine Inverse-square-Root ELR)

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-30.

## Quickstart Implementation

```python
from __future__ import annotations

def air_lr(t, t_max, peak, terminal):
    raw = (t_max ** 0.5) / max(t, 1) ** 0.5
    start, end = (t_max ** 0.5), 1.0
    affine = (raw - end) / (start - end)
    return terminal + (peak - terminal) * affine
```

Do not retarget locked SOTA from this recipe.
