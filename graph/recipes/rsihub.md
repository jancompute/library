---
id: recipe:rsihub
type: recipe
title: 'RSIHub'
method: method:rsihub
task: task:agent-harness-runtime
target_hardware: 'Paper: agent-evolution RSI recipes'
framework: PyTorch
repo_url: https://github.com/simple-agent-lab/RSIHub
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- rsihub
---

# RSIHub

## Hardware & Environment Setup
- Official: `https://github.com/simple-agent-lab/RSIHub`.
- `code_status: released` as of 2026-10-26.

## Quickstart Implementation

```python
from __future__ import annotations

def mutable(name: str, allowed: set) -> bool:
    if not name:
        raise ValueError('name')
    return name in allowed
```

Do not retarget locked SOTA from this recipe.
