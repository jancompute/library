---
id: recipe:harnessflow
type: recipe
title: 'HarnessFlow'
method: method:harnessflow
task: task:agent-harness-runtime
target_hardware: 'Paper: six agent/coding/web benches, 15 refinements'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- harnessflow
---

# HarnessFlow

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-05.

## Quickstart Implementation

```python
from __future__ import annotations

def harnessflow_select(scores, visits, c_puct):
    return max(range(len(scores)), key=lambda i: scores[i] + c_puct / (1 + visits[i]))
```

Do not retarget locked SOTA from this recipe.
