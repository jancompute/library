---
id: recipe:mxfp8-rl
type: recipe
title: 'MXFP8 RL Matching'
method: method:mxfp8-rl
task: task:fp4-rl-train-rollout-alignment
target_hardware: 'Paper: B200 MXFP8 RL in verl'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- mxfp8-rl
---

# MXFP8 RL Matching

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def same_grid(train_q, rollout_q) -> bool:
    return train_q == rollout_q
```

Do not retarget locked SOTA from this recipe.
