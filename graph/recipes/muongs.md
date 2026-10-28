---
id: recipe:muongs
type: recipe
title: 'MuonGS'
method: method:muongs
task: task:llm-pretraining-optimization
target_hardware: 'Paper: 160M/400M dense and 1B-total MoE pretrain'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- muongs
---

# MuonGS

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-28.

## Quickstart Implementation

```python
from __future__ import annotations

def radial_strip(update, weight):
    scale = (update * weight).sum() / ((weight * weight).sum() + 1e-12)
    return update - scale * weight
```

Do not retarget locked SOTA from this recipe.
