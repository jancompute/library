---
id: recipe:setgrpo
type: recipe
title: 'SetGRPO'
method: method:setgrpo
task: task:multi-reward-rlvr
target_hardware: 'Paper: Qwen3.5 / Llama3.2 rubric RL'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- setgrpo
---

# SetGRPO

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-28.

## Quickstart Implementation

```python
from __future__ import annotations

def keep_update(risk, threshold):
    return risk <= threshold
```

Do not retarget locked SOTA from this recipe.
