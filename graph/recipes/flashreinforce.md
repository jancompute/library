---
id: recipe:flashreinforce
type: recipe
title: FlashREINFORCE
method: method:flashreinforce
task: task:agentic-async-rl
target_hardware: 'Paper: Qwen2.5-Math-1.5B / R1-Distill-Qwen-1.5B / Qwen3-30B-A3B async RL'
framework: PyTorch
repo_url: https://github.com/NVIDIA-NeMo/labs-molt
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- flashreinforce
---

# FlashREINFORCE

## Hardware & Environment Setup
- Official: `https://github.com/NVIDIA-NeMo/labs-molt` (`code_status: released`).
- Quick start: `examples/scripts/quick_start/rl_flash_reinforce_r1d_1p5b.sh`. One rollout per prompt. Sequence trust region plus sample-mean optimization.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def flashreinforce_scale(adv: torch.Tensor, seq_kl: torch.Tensor, kl_coef: float, batch_mean: torch.Tensor) -> torch.Tensor:
    centered = adv - batch_mean
    return centered - kl_coef * seq_kl
```

Do not retarget locked SOTA from this recipe.
