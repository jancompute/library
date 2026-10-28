---
id: recipe:ciga
type: recipe
title: 'CIGA'
method: method:ciga
task: task:training-data-attribution
target_hardware: 'Paper: instruction-tuning attribution'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- ciga
---

# CIGA

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-28.

## Quickstart Implementation

```python
from __future__ import annotations

def stable_layers(scores_orig, scores_para, floor=0.5):
    return [i for i, (a, b) in enumerate(zip(scores_orig, scores_para)) if abs(a - b) <= floor]
```

Do not retarget locked SOTA from this recipe.
