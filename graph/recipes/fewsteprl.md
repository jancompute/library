---
id: recipe:fewsteprl
type: recipe
title: 'FewStepRL'
method: method:fewsteprl
task: task:posttrain-diffusion
target_hardware: 'Paper: few-step average-velocity diffusion host'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- fewsteprl
---

# FewStepRL

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-10.

## Quickstart Implementation

```python
from __future__ import annotations

def few_step_avg_velocity(v_t, v_s, n_steps: int):
    return (v_t + v_s) / max(n_steps, 1)
```

Do not retarget locked SOTA from this recipe.
