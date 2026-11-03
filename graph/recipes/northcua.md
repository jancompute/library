---
id: recipe:northcua
type: recipe
title: 'NorthCUA'
method: method:northcua
task: task:hybrid-computer-use-agent-rl
target_hardware: 'Paper: NorthCUA Nano / Mini / Pro'
framework: PyTorch
repo_url: https://github.com/beipo-ai/NorthCUA
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- northcua
---

# NorthCUA

## Hardware & Environment Setup
- Official: `https://github.com/beipo-ai/NorthCUA`.
- `code_status: released` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def keep_verified(traj, ok):
    return traj if ok else None
```

Do not retarget locked SOTA from this recipe.
