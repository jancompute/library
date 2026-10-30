---
id: recipe:scope-agent-opsd
type: recipe
title: 'SCOPE (agent critical-step OPSD)'
method: method:scope-agent-opsd
task: task:outcome-only-long-horizon-agent-rl
target_hardware: 'Paper: Qwen2.5-3B / Qwen3-32B ALFWorld WebShop'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- scope-agent-opsd
---

# SCOPE (agent critical-step OPSD)

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-30.

## Quickstart Implementation

```python
from __future__ import annotations

def scope_step_mask(error_steps, coef):
    w = coef.clamp(-1.0, 1.0)
    return error_steps.float() * w
```

Do not retarget locked SOTA from this recipe.
