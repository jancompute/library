---
id: recipe:tsbpo
type: recipe
title: 'TSBPO'
method: method:tsbpo
task: task:outcome-only-long-horizon-agent-rl
target_hardware: 'Paper: Qwen2.5-1.5B ALFWorld / WebShop'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- tsbpo
---

# TSBPO

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-02.

## Quickstart Implementation

```python
from __future__ import annotations

def tsbpo_adv(sib_return, sib_mean, obs_return, obs_mean):
    traj = sib_return - sib_mean
    step = obs_return - obs_mean
    return traj + step
```

Do not retarget locked SOTA from this recipe.
