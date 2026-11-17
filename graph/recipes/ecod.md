---
id: recipe:ecod
type: recipe
title: ECOD
method: method:ecod
task: task:outcome-only-long-horizon-agent-rl
target_hardware: 'Paper: Qwen2.5-1.5B/7B-Instruct ALFWorld / WebShop'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- ecod
---

# ECOD

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-17. Compare student and teacher traces. Weight teacher tokens by a temporal prior from successful teacher lengths.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def ecod_weight(t: torch.Tensor, teacher_success_len: float, tau: float = 0.25) -> torch.Tensor:
    return torch.exp(-tau * (t.float() / max(teacher_success_len, 1.0)))
```

Do not retarget locked SOTA from this recipe.
