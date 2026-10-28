---
id: recipe:adaroll-grpo
type: recipe
title: 'AdaRoll-GRPO'
method: method:adaroll-grpo
task: task:math-code-rl-dense
target_hardware: 'Paper: GRPO reasoning RL'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- adaroll-grpo
---

# AdaRoll-GRPO

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-28.

## Quickstart Implementation

```python
from __future__ import annotations

def allocate(budget, values):
    order = sorted(range(len(values)), key=lambda i: values[i], reverse=True)
    counts = [1] * len(values)
    leftover = budget - len(values)
    for i in order[: max(leftover, 0)]:
        counts[i] += 1
    return counts
```

Do not retarget locked SOTA from this recipe.
