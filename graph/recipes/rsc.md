---
id: recipe:rsc
type: recipe
title: RSC
method: method:rsc
task: task:agentic-async-rl
target_hardware: 'Paper: Qwen3-4B-Base async agentic RL; sampler refresh R=64'
framework: PyTorch
repo_url: https://github.com/BiEchi/rsc
code_status: announced
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- rsc
---

# RSC

## Hardware & Environment Setup
- Official: `https://github.com/BiEchi/rsc` (`code_status: announced`; empty as of 2026-11-18). Project: `https://biechi.github.io/blog/rsc/`.
- Score-center advantages, then add reverse-KL next-token matching to the behavior policy. Truncated IS is optional.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn.functional as F


def rsc_loss(adv: torch.Tensor, logp: torch.Tensor, logp_old: torch.Tensor, beta: float) -> torch.Tensor:
    centered = adv - adv.mean()
    pg = -(centered.detach() * logp).mean()
    rkl = (logp.exp() * (logp - logp_old)).sum(dim=-1).mean()
    return pg + beta * rkl
```

Do not retarget locked SOTA from this recipe.
