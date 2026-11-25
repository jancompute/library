---
id: recipe:ghc
type: recipe
title: GHC
method: method:ghc
task: task:llm-pretraining-optimization
target_hardware: 'Paper: 430M dense; 4BA0.2B / 13BA0.6B MoE'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- ghc
---

# GHC

## Hardware & Environment Setup
- `code_status: none` as of 2026-11-25. No public GitHub. Default \(n=4\) streams, \(r=8\) groups, TanhSiLU, freeze first-layer \(H_{\mathrm{pre}}\). Does not replace Muon2 or DeepSeek-V4.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn.functional as F


def tanh_silu(x: torch.Tensor) -> torch.Tensor:
    return torch.tanh(F.silu(x))


def ghc_read_write(
    streams: torch.Tensor,
    h_pre: torch.Tensor,
    h_post: torch.Tensor,
    group_scale: torch.Tensor,
) -> torch.Tensor:
    mixes = torch.einsum("bnsd,nrg->brsd", streams, h_pre)
    outs = mixes * tanh_silu(group_scale).unsqueeze(-1).unsqueeze(-1)
    return torch.einsum("brsd,nrg->bnsd", outs, h_post)
```
