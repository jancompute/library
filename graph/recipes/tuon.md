---
id: recipe:tuon
type: recipe
title: 'TUON'
method: method:tuon
task: task:llm-pretraining-optimization
target_hardware: 'Paper: tensor-aware Muon-family pretrain'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- tuon
---

# TUON

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def mix_slices(layers, q):
    return [sum(qij * w for qij, w in zip(qi, layers)) for qi in q]
```

Do not retarget locked SOTA from this recipe.
