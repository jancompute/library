---
id: recipe:race-rubric
type: recipe
title: 'RACE'
method: method:race-rubric
task: task:outcome-only-long-horizon-agent-rl
target_hardware: 'Paper: open-ended rubric RL'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- race-rubric
---

# RACE

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-30.

## Quickstart Implementation

```python
from __future__ import annotations

def race_route(group_std, pass_rate):
    if group_std < 1e-6:
        return 'collapsed'
    if pass_rate <= 0:
        return 'rubric_failed'
    return 'informative'
```

Do not retarget locked SOTA from this recipe.
