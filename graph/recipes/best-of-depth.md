---
id: recipe:best-of-depth
type: recipe
title: 'Best-of-Depth'
method: method:best-of-depth
task: task:elastic-depth-looped-lm
target_hardware: 'Paper: looped-LM candidate depths'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- best-of-depth
---

# Best-of-Depth

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-04.

## Quickstart Implementation

```python
from __future__ import annotations

def best_of_depth(losses_by_k):
    return min(range(len(losses_by_k)), key=lambda k: losses_by_k[k])
```

Do not retarget locked SOTA from this recipe.
