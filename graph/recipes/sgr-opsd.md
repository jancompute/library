---
id: recipe:sgr-opsd
type: recipe
title: 'SGR-OPSD'
method: method:sgr-opsd
task: task:outcome-only-long-horizon-agent-rl
target_hardware: 'Paper: Qwen2.5-3B/7B ALFWorld / WebShop / Search-QA'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- sgr-opsd
---

# SGR-OPSD

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def graph_calibrate(teacher_w, emp_return, state_avg):
    return teacher_w * (emp_return - state_avg).sign()
```

Do not retarget locked SOTA from this recipe.
