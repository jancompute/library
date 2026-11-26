---
id: recipe:molt
type: recipe
title: MoLT
method: method:molt
task: task:recurrent-encoder-decoder-lm
target_hardware: 'Paper: 700M/1.5B dense and 3B MoE at 400B tokens; Qwen3.5-0.8B-Base 100B CPT'
framework: PyTorch
repo_url: https://github.com/hustvl/MoLT
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- molt
---

# MoLT

## Hardware & Environment Setup
- Official: `https://github.com/hustvl/MoLT`
- `code_status: released` as of 2026-11-26. U-MoLT on BlaGPT; fused MoLA Triton. Does not replace RLT, ELR, SMELT, or Muon2.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn.functional as F


def mola_read(
    query: torch.Tensor,
    local_k: torch.Tensor,
    local_v: torch.Tensor,
    memory_k: torch.Tensor,
    memory_v: torch.Tensor,
) -> torch.Tensor:
    k = torch.cat([memory_k, local_k], dim=-2)
    v = torch.cat([memory_v, local_v], dim=-2)
    scores = torch.matmul(query, k.transpose(-2, -1)) * query.shape[-1] ** -0.5
    return torch.matmul(F.softmax(scores, dim=-1), v)
```
