---
id: recipe:rcrl
type: recipe
title: 'RcRL'
method: method:rcrl
task: task:outcome-only-long-horizon-agent-rl
target_hardware: 'Paper: Qwen3-4B creative writing / HealthBench'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- rcrl
---

# RcRL

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-05.

## Quickstart Implementation

```python
from __future__ import annotations

def rcrl_advance(criteria, pairwise_margin, stall_steps):
    if stall_steps > 0:
        return criteria + 1
    return criteria
```

Do not retarget locked SOTA from this recipe.
