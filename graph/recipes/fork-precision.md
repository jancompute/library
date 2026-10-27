---
id: recipe:fork-precision
type: recipe
title: 'FORK (Precision Objective)'
method: method:fork-precision
task: task:outcome-only-long-horizon-agent-rl
target_hardware: 'Paper: rubric-based RL'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- fork-precision
---

# FORK (Precision Objective)

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def fork_reward(recall: float, precision: float, beta: float = 1.0) -> float:
    if recall + precision <= 0:
        return 0.0
    b2 = beta * beta
    return (1 + b2) * recall * precision / (b2 * recall + precision)
```

Do not retarget locked SOTA from this recipe.
