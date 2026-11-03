---
id: recipe:proland
type: recipe
title: 'ProLand'
method: method:proland
task: task:lora-quality-tuning
target_hardware: 'Paper: DeBERTa-v3-base GLUE; Qwen2.5-3B / Llama-3.2-3B / Moonlight-16B-A3B'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- proland
---

# ProLand

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def proland_step(A, B, gA, gB, eta, land):
    A = A - eta * gA
    B = B - eta * gB
    return A - land * (A @ A.T - A.new_zeros(A.shape[0], A.shape[0]).fill_diagonal_(1)) @ A, B
```

Do not retarget locked SOTA from this recipe.
