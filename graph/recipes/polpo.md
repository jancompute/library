---
id: recipe:polpo
type: recipe
title: POLPO
method: method:polpo
task: task:multi-reward-rlvr
target_hardware: 'Paper: multi-verifier code / instruction-following RL'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- polpo
---

# POLPO

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-17. Build Pareto dominance from verifier bit-vectors. Maximize listwise likelihood of rankings consistent with that partial order. Do not scalarize first.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def pareto_dominates(a: torch.Tensor, b: torch.Tensor) -> torch.Tensor:
    ge = (a >= b).all(dim=-1)
    gt = (a > b).any(dim=-1)
    return ge & gt
```

Do not retarget locked SOTA from this recipe.
