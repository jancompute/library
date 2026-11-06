---
id: recipe:evomemstate
type: recipe
title: 'EvoMemState'
method: method:evomemstate
task: task:agent-memory
target_hardware: 'Paper: Qwen3-8B / GPT-4o-mini, MemSyco / LoCoMo'
framework: PyTorch
repo_url: https://github.com/XMUDeepLIT/EvoMemState
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- evomemstate
---

# EvoMemState

## Hardware & Environment Setup
- Official: `https://github.com/XMUDeepLIT/EvoMemState`.
- `code_status: released` as of 2026-11-06.

## Quickstart Implementation

```python
from __future__ import annotations

def evomemstate_pack(facts, relational, reasoning):
    return {"facts": facts, "relational": relational, "reasoning": reasoning}
```

Do not retarget locked SOTA from this recipe.
