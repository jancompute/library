---
id: recipe:nld-uni
type: recipe
title: 'NLD-Uni'
method: method:nld-uni
task: task:diffusion-lm-ar-delta-recycle
target_hardware: 'Paper: unified discrete diffusion LLM'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- nld-uni
---

# NLD-Uni

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-28.

## Quickstart Implementation

```python
from __future__ import annotations

def progressive_noise(token_ids, step, max_step):
    keep = step / max(max_step, 1)
    return token_ids if keep > 0.5 else token_ids
```

Do not retarget locked SOTA from this recipe.
