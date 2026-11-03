---
id: recipe:cua-master
type: recipe
title: 'CUA-Master'
method: method:cua-master
task: task:hybrid-computer-use-agent-rl
target_hardware: 'Paper: 27B GUI+CLI CUA'
framework: PyTorch
repo_url: https://github.com/xlyu0106/CUA-Master
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- cua-master
---

# CUA-Master

## Hardware & Environment Setup
- Official: `https://github.com/xlyu0106/CUA-Master`.
- `code_status: released` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def snapshot_retry(env, act, max_tries=3):
    snap = env.snapshot()
    for _ in range(max_tries):
        ok = env.step(act)
        if ok:
            return True
        env.rollback(snap)
    return False
```

Do not retarget locked SOTA from this recipe.
