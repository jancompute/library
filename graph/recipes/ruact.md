---
id: recipe:ruact
type: recipe
title: 'RuACT'
method: method:ruact
task: task:outcome-only-long-horizon-agent-rl
target_hardware: 'Paper: Qwen3-1.7B/4B, verl, two A800, 200 steps'
framework: PyTorch
repo_url: https://github.com/ZJU-REAL/RuACT
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- ruact
---

# RuACT

## Hardware & Environment Setup
- Official: `https://github.com/ZJU-REAL/RuACT`.
- `code_status: released` as of 2026-11-09. Host: verl.

## Quickstart Implementation

```python
from __future__ import annotations

def ruact_role(pass_rate):
    if pass_rate <= 0:
        return "teacher"
    if pass_rate >= 1:
        return "critic"
    return "informative"
```

Do not retarget locked SOTA from this recipe.
