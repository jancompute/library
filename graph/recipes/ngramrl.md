---
id: recipe:ngramrl
type: recipe
title: 'NgramRL'
method: method:ngramrl
task: task:frontier-rl-posttrain-stack
target_hardware: 'Paper: structured-generation RL rollouts'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- ngramrl
---

# NgramRL

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-26.

## Quickstart Implementation

```python
from __future__ import annotations

def ngram_draft(suffix: tuple, table: dict, n: int):
    if n <= 0:
        raise ValueError('n')
    return table.get(suffix[-n:], ())
```

Do not retarget locked SOTA from this recipe.
