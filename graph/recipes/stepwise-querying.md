---
id: recipe:stepwise-querying
type: recipe
title: 'Stepwise Querying'
method: method:stepwise-querying
task: task:student-distillation
target_hardware: 'Paper: two-student math/code SFT'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- stepwise-querying
---

# Stepwise Querying

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-02.

## Quickstart Implementation

```python
from __future__ import annotations

QUERIES = ("derive", "check", "correct")

def stepwise_prompts(problem, step, kind):
    if kind not in QUERIES:
        raise ValueError(kind)
    return f"{kind} step {step} of: {problem}"
```

Do not retarget locked SOTA from this recipe.
