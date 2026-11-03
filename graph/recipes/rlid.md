---
id: recipe:rlid
type: recipe
title: 'RLiD'
method: method:rlid
task: task:outcome-only-long-horizon-agent-rl
target_hardware: 'Paper: ALFWorld 12.7 H100-h; ARC / Countdown / Sokoban'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- rlid
---

# RLiD

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def rlid_select(logits, action_ids):
    return action_ids[logits.argmax()]
```

Do not retarget locked SOTA from this recipe.
