---
id: recipe:tdlm
type: recipe
title: 'TDLM'
method: method:tdlm
task: task:diffusion-lm-ar-delta-recycle
target_hardware: 'Paper: LLaDA / Dream dLLM'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- tdlm
---

# TDLM

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-28.

## Quickstart Implementation

```python
from __future__ import annotations

def temporal_read(history, pos):
    return history[pos][-1] if history[pos] else None
```

Do not retarget locked SOTA from this recipe.
