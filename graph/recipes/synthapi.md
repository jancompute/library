---
id: recipe:synthapi
type: recipe
title: 'SynthAPI'
method: method:synthapi
task: task:coding-agent-rl-environment-construction
target_hardware: 'Paper: 849-model tool-use scaling sweep'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- synthapi
---

# SynthAPI

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-28.

## Quickstart Implementation

```python
from __future__ import annotations

def diversity_mix(n_tools, n_dbs, n_tasks):
    return (n_tools * n_dbs) / max(n_tasks, 1)
```

Do not retarget locked SOTA from this recipe.
