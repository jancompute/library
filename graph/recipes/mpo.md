---
id: recipe:mpo
type: recipe
title: 'MPO'
method: method:mpo
task: task:outcome-only-long-horizon-agent-rl
target_hardware: 'Paper: 4B / 30B-A3B agent RL'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- mpo
---

# MPO

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def turn_is(pi_turn: float, mu_turn: float, clip: float = 1.2) -> float:
    r = pi_turn / mu_turn if mu_turn else 1.0
    return min(max(r, 1.0 / clip), clip)
```

Do not retarget locked SOTA from this recipe.
