---
id: recipe:mcpo
type: recipe
title: 'MCPO'
method: method:mcpo
task: task:math-code-rl-dense
target_hardware: 'Paper: MiniCPM5-2B-Base / Qwen3-4B-Base LoRA, G group GRPO, 200 steps'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- mcpo
---

# MCPO

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-11. Overlay on a GRPO/CISPO-family trainer. Thresholds $\ell=0.1$, $u=0.7$ ($\equiv M\ge 0.9\to h=0$, $M\le 0.3\to h=1$). $\kappa=\ln 4$.

## Quickstart Implementation

```python
from __future__ import annotations

import math

import torch


def margin_score(p1: torch.Tensor, p2: torch.Tensor, ell: float = 0.1, u: float = 0.7) -> torch.Tensor:
    m = p1 - p2
    return ((1.0 - m) - ell).div(u - ell).clamp(0.0, 1.0)


def mcpo_token_advantage(A: torch.Tensor, h: torch.Tensor, kappa: float = math.log(4.0)) -> torch.Tensor:
    w = torch.exp(kappa * A.sign() * h)
    return A * w / w.mean().clamp_min(1e-8)
```

Do not retarget locked SOTA from this recipe.
