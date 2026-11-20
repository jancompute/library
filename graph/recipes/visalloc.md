---
id: recipe:visalloc
type: recipe
title: VisAlloc
method: method:visalloc
task: task:privileged-teacher-opsd
target_hardware: 'Paper: Qwen3.5-4B/9B OPSD, 96 prompts x 8 rollouts'
framework: PyTorch
repo_url: https://github.com/Kaelyn01/VisAlloc
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- visalloc
---

# VisAlloc

## Hardware & Environment Setup
- Official: `https://github.com/Kaelyn01/VisAlloc`
- `code_status: released` as of 2026-11-20. Paired-teacher crop filter plus conserved token weights. Does not replace VISTA.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def visalloc_keep_mask(pos_ok: torch.Tensor, neg_ok: torch.Tensor) -> torch.Tensor:
    return pos_ok & ~neg_ok


def conserved_token_weight(bonus: torch.Tensor, freq: torch.Tensor) -> torch.Tensor:
    inv = (1.0 / freq.clamp_min(1.0)) * bonus
    scale = bonus.sum() / inv.sum().clamp_min(1e-8)
    return inv * scale
```
