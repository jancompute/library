---
id: recipe:maco-rl
type: recipe
title: Maco-RL
method: method:maco-rl
task: task:agentic-async-rl
target_hardware: 'Paper: Qwen3.5-27B / Qwen3.8-27B, verl + RLOO, G=8, 256 traj/update'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- maco-rl
---

# Maco-RL

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-27.

## Quickstart Implementation

```python
from __future__ import annotations


def tbs_bucket(n_success: int, group_size: int) -> str:
    if n_success <= 0:
        return "frontier"
    if n_success >= group_size:
        return "history"
    return "reinforcement"


QUOTAS = {"frontier": 0.20, "reinforcement": 0.60, "history": 0.20}
```

Do not retarget locked SOTA from this recipe.
