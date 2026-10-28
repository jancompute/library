---
id: recipe:concur
type: recipe
title: 'CONCUR'
method: method:concur
task: task:multi-reward-rlvr
target_hardware: 'Paper: multi-task gated-auxiliary RL'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- concur
---

# CONCUR

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-28.

## Quickstart Implementation

```python
from __future__ import annotations

def project_monotone(aux, primary):
    order = sorted(range(len(primary)), key=lambda i: (primary[i], aux[i]))
    out = list(aux)
    for a, b in zip(order, order[1:]):
        if primary[a] < primary[b] and out[a] > out[b]:
            mid = 0.5 * (out[a] + out[b])
            out[a] = out[b] = mid
    return out
```

Do not retarget locked SOTA from this recipe.
