---
id: recipe:roam-grpo
type: recipe
title: ROAM-GRPO
method: method:roam-grpo
task: task:passk-reasoning-coverage
target_hardware: 'Paper: Qwen3.5-2B GRPO on MATH lvl5 subset'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- roam
---

# ROAM-GRPO

## Hardware & Environment Setup
- `code_status: none` as of 2026-11-20. Embedding-distance novelty on a GRPO host. Does not replace ES-reasoning.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn.functional as F


def roam_novelty(emb: torch.Tensor) -> torch.Tensor:
    sim = F.normalize(emb, dim=-1) @ F.normalize(emb, dim=-1).T
    dist = 1.0 - sim
    dist.fill_diagonal_(0.0)
    return dist.mean(dim=-1)
```
