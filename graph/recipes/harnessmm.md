---
id: recipe:harnessmm
type: recipe
title: 'HarnessMM'
method: method:harnessmm
task: task:agent-harness-runtime
target_hardware: 'Paper: tool-loop harness RSI'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- harnessmm
---

# HarnessMM

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-26.

## Quickstart Implementation

```python
from __future__ import annotations

def reuse(prev_action: str, obs_changed: bool) -> bool:
    if not prev_action:
        raise ValueError('action')
    return not obs_changed
```

Do not retarget locked SOTA from this recipe.
