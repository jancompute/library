---
id: recipe:flamia
type: recipe
title: 'FLAMIA'
method: method:flamia
task: task:fp4-hardware-training
target_hardware: 'Paper: NVIDIA B200 / B300 packed-document attention'
framework: PyTorch
repo_url: https://github.com/yandex-research/flamia-blackwell-attention
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- flamia
---

# FLAMIA

## Hardware & Environment Setup
- Official: `https://github.com/yandex-research/flamia-blackwell-attention`.
- `code_status: released` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def block_scale(x, block=32):
    m = x.abs().reshape(*x.shape[:-1], -1, block).amax(-1)
    return m.clamp_min(1e-6)
```

Do not retarget locked SOTA from this recipe.
