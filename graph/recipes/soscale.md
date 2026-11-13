---
id: recipe:soscale
type: recipe
title: SoScale
method: method:soscale
task: task:fp4-hardware-training
target_hardware: 'Paper: Qwen3-14B W4A4 MXFP4/NVFP4/HiF4 PTQ'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- soscale
---

# SoScale

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-13. Search hierarchical FP4 scale codes with a Hessian-aware objective, then GPTQ-recover. Do not retarget Quartet-II.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def pick_scale(block: torch.Tensor, candidates: torch.Tensor) -> torch.Tensor:
    err = (block.unsqueeze(0) - candidates.unsqueeze(-1)).abs().mean(dim=-1)
    return candidates[int(err.argmin().item())]
```

Do not retarget locked SOTA from this recipe.
