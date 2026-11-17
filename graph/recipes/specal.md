---
id: recipe:specal
type: recipe
title: SpeCal
method: method:specal
task: task:label-free-reasoner-posttrain
target_hardware: 'Paper: unsupervised RLVR with hidden-state spectra'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- specal
---

# SpeCal

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-17. Keep the unlabeled reward. Rescale group and rollout advantages from hidden-state SVD mass and effective rank.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def specal_eff_rank(hidden: torch.Tensor, eps: float = 1e-8) -> torch.Tensor:
    s = torch.linalg.svdvals(hidden.float())
    p = s / (s.sum() + eps)
    return torch.exp(-(p * (p + eps).log()).sum())
```

Do not retarget locked SOTA from this recipe.
