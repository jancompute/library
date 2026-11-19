---
id: recipe:curvdelta
type: recipe
title: CurvDelta
method: method:curvdelta
task: task:lora-quality-tuning
target_hardware: 'Paper: Gemma-3-1B / Llama-2-7B sequential PEFT; Llama-3.1-8B TOFU'
framework: PyTorch
repo_url: https://github.com/xiaozi-max/curvdelta_learning
code_status: released
pip_dependencies:
- torch>=2.5.0
- peft
tags:
- recipe
- curvdelta
---

# CurvDelta

## Hardware & Environment Setup
- Official: `https://github.com/xiaozi-max/curvdelta_learning`.
- Unlearning: `https://github.com/xiaozi-max/curvdelta_unlearning`.
- `code_status: released` as of 2026-11-19. K-FAC low-curvature subspace for sequential PEFT. Does not supersede vanilla LoRA + rsLoRA + LR sweep.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def low_curvature_mask(diag_fisher: torch.Tensor, keep: float = 0.2) -> torch.Tensor:
    k = max(1, int(diag_fisher.numel() * keep))
    thresh = torch.kthvalue(diag_fisher, k).values
    return diag_fisher <= thresh
```

Do not retarget locked SOTA from this recipe.
