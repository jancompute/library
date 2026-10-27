---
id: recipe:mirl
type: recipe
title: 'MiRL'
method: method:mirl
task: task:coding-agent-rl-environment-construction
target_hardware: 'Paper: terminal-agent error-targeted RL'
framework: PyTorch
repo_url: https://github.com/runchu-tian/MiRL
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- mirl
---

# MiRL

## Hardware & Environment Setup
- Official: `https://github.com/runchu-tian/MiRL`.
- `code_status: released` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def keep_error(name: str, still_fails: bool) -> bool:
    return still_fails and bool(name)
```

Do not retarget locked SOTA from this recipe.
