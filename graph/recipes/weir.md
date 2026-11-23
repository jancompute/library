---
id: recipe:weir
type: recipe
title: Weir
method: method:weir
task: task:outcome-only-long-horizon-agent-rl
target_hardware: 'Paper: Qwen2.5-3B/7B-Instruct, 6-8 trajectories/task'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- weir
---

# Weir

## Hardware & Environment Setup
- `code_status: none` as of 2026-11-23. No public GitHub. Neyman task budgets \(B_q\propto\sqrt{\hat p(1-\hat p)}\) plus watershed forks on a discounted prefix tree. Does not replace CANOPY.

## Quickstart Implementation

```python
from __future__ import annotations

import math


def neyman_budget(pass_rate: float, total: int, mass: float) -> int:
    sigma = math.sqrt(max(pass_rate * (1.0 - pass_rate), 0.0))
    return max(1, round(total * sigma / mass))
```
