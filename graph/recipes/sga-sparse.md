---
id: recipe:sga-sparse
type: recipe
title: 'SGA-Sparse'
method: method:sga-sparse
task: task:full-lowbit-finetune
target_hardware: 'Paper: LLaMA 1B–8B, ~30B tokens'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- sga-sparse
---

# SGA-Sparse

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-10.

## Quickstart Implementation

```python
from __future__ import annotations

import torch

def sga_topk_mask(gate: torch.Tensor, k: int) -> torch.Tensor:
    thresh = torch.topk(gate.abs(), k, dim=-1).values[..., -1:]
    return gate.abs() >= thresh
```

Do not retarget locked SOTA from this recipe.
