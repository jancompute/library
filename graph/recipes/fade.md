---
id: recipe:fade
type: recipe
title: 'FADE'
method: method:fade
task: task:math-code-rl-dense
target_hardware: 'Paper: online group RLVR'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- fade
---

# FADE

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def fade_logit(skill, ability, intercept):
    return (skill * ability).sum() - intercept
```

Do not retarget locked SOTA from this recipe.
