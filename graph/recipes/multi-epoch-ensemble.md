---
id: recipe:multi-epoch-ensemble
type: recipe
title: 'Multi-Epoch Ensemble'
method: method:multi-epoch-ensemble
task: task:data-constrained-pretrain
target_hardware: 'Paper: FineWeb multi-epoch ensembles'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- multi-epoch-ensemble
---

# Multi-Epoch Ensemble

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def logit_ensemble(logits):
    return sum(logits) / len(logits)
```

Do not retarget locked SOTA from this recipe.
