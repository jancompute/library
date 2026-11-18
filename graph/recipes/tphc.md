---
id: recipe:tphc
type: recipe
title: TPHC
method: method:tphc
task: task:llm-pretraining-optimization
target_hardware: 'Paper: 1.1B / 100B SlimPajama; 8B TP-sharded TPHC4'
framework: PyTorch
repo_url: https://github.com/wuyou2002/TPHC
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- tphc
---

# TPHC

## Hardware & Environment Setup
- Official: `https://github.com/wuyou2002/TPHC` (`code_status: released`).
- Group Hyper-Connection streams per tensor-parallel rank. Sparse per-group write. Do not retarget mHC, SimpleHC, or DeepSeek-V4.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def tphc_grouped_write(streams: torch.Tensor, update: torch.Tensor, group_ids: torch.Tensor) -> torch.Tensor:
    out = streams.clone()
    n_groups = int(group_ids.max().item()) + 1
    for g in range(n_groups):
        mask = group_ids == g
        out[:, mask] = out[:, mask] + update[:, mask]
    return out
```

Do not retarget locked SOTA from this recipe.
