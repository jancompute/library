---
id: recipe:hilo-rd
type: recipe
title: 'HiLo-RD'
method: method:hilo-rd
task: task:diffusion-lm-ar-delta-recycle
target_hardware: 'Paper: masked dLLM math decoding'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- hilo-rd
---

# HiLo-RD

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-28.

## Quickstart Implementation

```python
from __future__ import annotations

def committed_match(teacher_h, student_h, committed_mask):
    delta = (teacher_h - student_h) * committed_mask
    return (delta * delta).mean()
```

Do not retarget locked SOTA from this recipe.
