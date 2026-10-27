---
id: recipe:papo
type: recipe
title: 'PAPO'
method: method:papo
task: task:multi-reward-rlvr
target_hardware: 'Paper: multi-reward GRPO/PPO'
framework: PyTorch
repo_url: https://xiangchi-yuan.github.io/papo-project/
code_status: announced
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- papo
---

# PAPO

## Hardware & Environment Setup
- Official: `https://xiangchi-yuan.github.io/papo-project/`.
- `code_status: announced` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def papo(primary: float, aux: float, tau: float = 1.0) -> float:
    if primary * aux >= 0:
        return primary + aux
    return primary + aux * max(0.0, 1.0 - abs(aux) / (abs(primary) * tau + 1e-8))
```

Do not retarget locked SOTA from this recipe.
