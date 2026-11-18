---
id: recipe:ash
type: recipe
title: ASH
method: method:ash
task: task:math-code-rl-dense
target_hardware: 'Paper: Qwen3-1.7B/4B-Base and Llama-3.2-1B/3B-Instruct HA-GRPO on verl'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- ash
---

# ASH

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-18 (paper uses verl). Train a residual steering vector on hinted vs plain hidden states. Inject it at inference so the hint is not in context.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def ash_steer(h: torch.Tensor, v: torch.Tensor, alpha: float) -> torch.Tensor:
    return h + alpha * v
```

Do not retarget locked SOTA from this recipe.
