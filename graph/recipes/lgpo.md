---
id: recipe:lgpo
type: recipe
title: LGPO
method: method:lgpo
task: task:math-code-rl-dense
target_hardware: 'Paper: Qwen2.5-3B GRPO-family on-policy RLVR'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- lgpo
---

# LGPO

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-13. Gate current-policy token logp at the top 10–20% quantile. Skip the old-policy likelihood pass only when sampler and trainer are the same weights.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def lgpo_keep(logp: torch.Tensor, tau_quantile: float = 0.85) -> torch.Tensor:
    thresh = torch.quantile(logp.detach(), tau_quantile)
    return logp >= thresh
```

Do not retarget locked SOTA from this recipe.
