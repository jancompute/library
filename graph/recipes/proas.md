---
id: recipe:proas
type: recipe
title: 'ProAS'
method: method:proas
task: task:outcome-only-long-horizon-agent-rl
target_hardware: 'Paper: Qwen2.5-1.5B/7B-Instruct agent RL'
framework: PyTorch
repo_url: https://github.com/LINs-lab/ProAS
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- proas
---

# ProAS

## Hardware & Environment Setup
- Official: `https://github.com/LINs-lab/ProAS`.
- `code_status: released` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def mask_unreasonable(adv: float, structurally_ok: bool) -> float:
    return adv if structurally_ok else 0.0
```

Do not retarget locked SOTA from this recipe.
