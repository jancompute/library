---
id: recipe:gpdpo
type: recipe
title: 'GPDPO'
method: method:gpdpo
task: task:multi-reward-rlvr
target_hardware: 'Paper: API-Bank multi-reward RL'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- gpdpo
---

# GPDPO

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def dominates(a, b) -> bool:
    return all(x >= y for x, y in zip(a, b)) and any(x > y for x, y in zip(a, b))
```

Do not retarget locked SOTA from this recipe.
