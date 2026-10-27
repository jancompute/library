---
id: recipe:dtca
type: recipe
title: 'DTCA'
method: method:dtca
task: task:diffusion-lm-ar-delta-recycle
target_hardware: 'Paper: LLaDA-8B-Instruct dLLM RL'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- dtca
---

# DTCA

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def credit(before: float, after: float) -> float:
    return after - before
```

Do not retarget locked SOTA from this recipe.
