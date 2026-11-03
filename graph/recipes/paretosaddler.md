---
id: recipe:paretosaddler
type: recipe
title: 'ParetoSaddler'
method: method:paretosaddler
task: task:agent-harness-runtime
target_hardware: 'Paper: ClawMark / GAIA2 harness search'
framework: PyTorch
repo_url: https://aka.ms/ParetoSaddler-website
code_status: announced
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- paretosaddler
---

# ParetoSaddler

## Hardware & Environment Setup
- Official: `https://aka.ms/ParetoSaddler-website`.
- Project: `https://aka.ms/ParetoSaddler-website`.
- `code_status: announced` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def pareto_promote(parent, child, quality, cost):
    return (quality[child] > quality[parent]) or (cost[child] < cost[parent])
```

Do not retarget locked SOTA from this recipe.
