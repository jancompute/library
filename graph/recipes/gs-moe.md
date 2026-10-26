---
id: recipe:gs-moe
type: recipe
title: 'GS-MoE'
method: method:gs-moe
task: task:pretrain-moe-frontier
target_hardware: 'Paper: Mixtral / Qwen-style MoE calibration prune'
framework: PyTorch
repo_url: https://github.com/cbacary/GS-MoE
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- gs-moe
---

# GS-MoE

## Hardware & Environment Setup
- Official: `https://github.com/cbacary/GS-MoE`.
- `code_status: released` as of 2026-10-26.

## Quickstart Implementation

```python
from __future__ import annotations

def shared_rank(group_size: int, rank: int) -> int:
    if group_size <= 0 or rank <= 0:
        raise ValueError('gs-moe')
    return min(rank, group_size)
```

Do not retarget locked SOTA from this recipe.
