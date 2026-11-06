---
id: recipe:o2pd
type: recipe
title: 'O2PD'
method: method:o2pd
task: task:student-distillation
target_hardware: 'Paper: VERL, k=16, DAPO-MATH-17K, Qwen3 1.7B/4B'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- o2pd
---

# O2PD

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-06. Host: VERL.

## Quickstart Implementation

```python
from __future__ import annotations

def o2pd_prefix_mask(seq_len, frac=0.2):
    k = max(1, int(seq_len * frac))
    return [i < k for i in range(seq_len)]
```

Do not retarget locked SOTA from this recipe.
