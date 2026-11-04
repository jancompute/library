---
id: recipe:mdskill
type: recipe
title: 'MDSkill'
method: method:mdskill
task: task:agent-memory
target_hardware: 'Paper: ALFWorld / WebShop'
framework: PyTorch
repo_url: https://anonymous.4open.science/r/MDSKILL-CF53
code_status: announced
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- mdskill
---

# MDSkill

## Hardware & Environment Setup
- Announced: `https://anonymous.4open.science/r/MDSKILL-CF53`.
- `code_status: announced` as of 2026-11-04.

## Quickstart Implementation

```python
from __future__ import annotations

def mdskill_views(traj, n_views):
    return [traj] * n_views
```

Do not retarget locked SOTA from this recipe.
