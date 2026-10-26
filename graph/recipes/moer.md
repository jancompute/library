---
id: recipe:moer
type: recipe
title: 'MOER'
method: method:moer
task: task:math-code-rl-dense
target_hardware: 'Paper: mix-policy reasoning RL with expert prefixes'
framework: PyTorch
repo_url: https://github.com/CityU-MLO/MOER
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- moer
---

# MOER

## Hardware & Environment Setup
- Official: `https://github.com/CityU-MLO/MOER`.
- `code_status: released` as of 2026-10-26.

## Quickstart Implementation

```python
from __future__ import annotations

def rollback_prefix(ok: bool, prefix_len: int) -> int:
    if prefix_len < 0:
        raise ValueError('prefix_len')
    return 0 if not ok else prefix_len
```

Do not retarget locked SOTA from this recipe.
