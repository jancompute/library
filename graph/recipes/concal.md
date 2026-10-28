---
id: recipe:concal
type: recipe
title: 'ConCal'
method: method:concal
task: task:outcome-only-long-horizon-agent-rl
target_hardware: 'Paper: Qwen2.5-1.5B-Instruct ALFWorld/WebShop'
framework: PyTorch
repo_url: https://github.com/Yingjian-Chen/ConCal
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- concal
---

# ConCal

## Hardware & Environment Setup
- Official: `https://github.com/Yingjian-Chen/ConCal`.
- `code_status: released` as of 2026-10-28.

## Quickstart Implementation

```python
from __future__ import annotations

def pool_continuations(values_by_transition):
    return {k: sum(v) / len(v) for k, v in values_by_transition.items() if v}
```

Do not retarget locked SOTA from this recipe.
