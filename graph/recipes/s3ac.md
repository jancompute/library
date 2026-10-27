---
id: recipe:s3ac
type: recipe
title: 'S3AC'
method: method:s3ac
task: task:token-level-critic-rl
target_hardware: 'Paper: long-CoT actor-critic RLVR'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- s3ac
---

# S3AC

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def daps_keep(difficulty: float, outcome_rate: float, floor: float = 0.0) -> bool:
    return difficulty * (1.0 - outcome_rate) > floor
```

Do not retarget locked SOTA from this recipe.
