---
id: recipe:tace
type: recipe
title: 'TACE'
method: method:tace
task: task:multi-reward-rlvr
target_hardware: 'Paper: multimodal RLVR GRPO groups'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- tace
---

# TACE

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-30.

## Quickstart Implementation

```python
from __future__ import annotations

def tace_renorm(token_w):
    m = token_w.mean().clamp_min(1e-8)
    return token_w / m
```

Do not retarget locked SOTA from this recipe.
