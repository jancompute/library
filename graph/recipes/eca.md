---
id: recipe:eca
type: recipe
title: ECA
method: method:eca
task: task:web-search-agent-rl
target_hardware: 'Paper: Qwen2.5-3B/7B GRPO-host search RL'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- eca
---

# ECA

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-19 (Snowball0823/ECA is unrelated). Evidence-only potential Φ(D) from retrieved documents; ECA-Horizon / ECA-TD / ECA-MC on a GRPO host.

## Quickstart Implementation

```python
from __future__ import annotations


def eca_horizon(phi: list[float], gamma: float = 1.0) -> list[float]:
    g = 0.0
    out: list[float] = []
    for p in reversed(phi):
        g = p + gamma * g
        out.append(g)
    out.reverse()
    return out
```

Do not retarget locked SOTA from this recipe.
