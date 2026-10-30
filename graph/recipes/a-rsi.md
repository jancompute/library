---
id: recipe:a-rsi
type: recipe
title: 'A-RSI'
method: method:a-rsi
task: task:data-free-self-evolution
target_hardware: 'Paper: zero-data multimodal RSI'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- a-rsi
---

# A-RSI

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-30.

## Quickstart Implementation

```python
from __future__ import annotations

def should_refresh(reward_std, acc, std0, acc0):
    return reward_std < 0.5 * std0 or acc > acc0 + 0.1
```

Do not retarget locked SOTA from this recipe.
