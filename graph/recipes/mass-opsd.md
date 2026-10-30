---
id: recipe:mass-opsd
type: recipe
title: 'MASS'
method: method:mass-opsd
task: task:privileged-teacher-opsd
target_hardware: 'Paper: math reasoning OPSD'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- mass-opsd
---

# MASS

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-30.

## Quickstart Implementation

```python
from __future__ import annotations

def mass_aggregate(teacher_logps):
    return sum(teacher_logps) / len(teacher_logps)
```

Do not retarget locked SOTA from this recipe.
