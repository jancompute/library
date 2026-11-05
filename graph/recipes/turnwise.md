---
id: recipe:turnwise
type: recipe
title: 'TurnWise'
method: method:turnwise
task: task:rl-video-mllm
target_hardware: 'Paper: Qwen2.5-VL-3B / Qwen3-VL-4B streaming video'
framework: PyTorch
repo_url: none found
code_status: announced
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- turnwise
---

# TurnWise

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: announced` as of 2026-11-05.

## Quickstart Implementation

```python
from __future__ import annotations

def turnwise_remaining(traj_reward, silent_prefix_reward):
    return traj_reward - silent_prefix_reward
```

Do not retarget locked SOTA from this recipe.
