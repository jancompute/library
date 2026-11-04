---
id: recipe:rsi-dojo
type: recipe
title: 'RSI-Dojo'
method: method:rsi-dojo
task: task:agentic-rsi-routing-posttrain
target_hardware: 'Paper: Qwen3.5-9B / Qwen3.6-35B-A3B SFT'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- rsi-dojo
---

# RSI-Dojo

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-04.

## Quickstart Implementation

```python
from __future__ import annotations

def rsi_dojo_task(env_id, checkpoint):
    return {"env": env_id, "ckpt": checkpoint}
```

Do not retarget locked SOTA from this recipe.
