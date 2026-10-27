---
id: recipe:lstm-looped-kv
type: recipe
title: 'LSTM-Style Shared-KV Loop'
method: method:lstm-looped-kv
task: task:recurrent-encoder-decoder-lm
target_hardware: 'Paper: FineWeb looped transformer'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- lstm-looped-kv
---

# LSTM-Style Shared-KV Loop

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def cons_loss(par, rec) -> float:
    return sum((a - b) ** 2 for a, b in zip(par, rec))
```

Do not retarget locked SOTA from this recipe.
