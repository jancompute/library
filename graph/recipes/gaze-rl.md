---
id: recipe:gaze-rl
type: recipe
title: Gaze-RL
method: method:gaze-rl
task: task:mllm-finegrained-perception-rl
target_hardware: 'Paper: Qwen2.5-VL-3B/7B and InternVL3.5-8B GRPO/DAPO host'
framework: PyTorch
repo_url: https://github.com/lixuan27/Gaze-RL-main
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- gaze-rl
---

# Gaze-RL

## Hardware & Environment Setup
- Official: `https://github.com/lixuan27/Gaze-RL-main` (`code_status: released`).
- Build a mean-one landing field from visual support and entropy. Rescale the completion advantage. Do not retarget Vision-RL2.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def gaze_advantage(adv: torch.Tensor, phi: torch.Tensor, gamma: float) -> torch.Tensor:
    phi = phi / phi.mean().clamp_min(1e-8)
    return ((1.0 - gamma) + gamma * phi) * adv
```

Do not retarget locked SOTA from this recipe.
