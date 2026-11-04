---
id: recipe:fura-s
type: recipe
title: 'FuRA-S'
method: method:fura-s
task: task:4bit-peft-quantization
target_hardware: 'Paper: 1–5 MB INT4 on-device specialists'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- fura-s
---

# FuRA-S

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-04.

## Quickstart Implementation

```python
from __future__ import annotations

def fura_s_spec(blocks, perturbation):
    return [b + perturbation for b in blocks]
```

Do not retarget locked SOTA from this recipe.
