---
id: recipe:canon-layers
type: recipe
title: Canon Layers
method: method:canon-layers
task: task:pretrain-dense-7b
target_hardware: 'Paper: 1.3B–8B from scratch on 1–2T Nemotron-CC'
framework: PyTorch
repo_url: https://github.com/facebookresearch/PhysicsLM4
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- canon
---

# Canon Layers

## Hardware & Environment Setup
- Official: `https://github.com/facebookresearch/PhysicsLM4`
- `code_status: released` as of 2026-11-20. Canon mix plus GLA5/GDN2 low-rank gates. Does not replace Muon2 or Mamba-2.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn as nn
import torch.nn.functional as F


class CanonMix(nn.Module):
    def __init__(self, dim: int, kernel_size: int = 3) -> None:
        super().__init__()
        self.dw = nn.Conv1d(dim, dim, kernel_size, padding=kernel_size // 2, groups=dim)

    def forward(self, x: torch.Tensor) -> torch.Tensor:
        return x + self.dw(x.transpose(1, 2)).transpose(1, 2)


def low_rank_output_gate(h: torch.Tensor, g1: torch.Tensor, g2: torch.Tensor, bias: torch.Tensor) -> torch.Tensor:
    return F.silu(h @ g2.T @ g1.T + bias)
```
