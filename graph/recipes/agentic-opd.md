---
id: recipe:agentic-opd
type: recipe
title: 'Agentic-OPD'
method: method:agentic-opd
task: task:student-distillation
target_hardware: 'Paper: Qwen2.5-3B/7B, Qwen3-4B GRPO host'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- agentic-opd
---

# Agentic-OPD

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-10.

## Quickstart Implementation

```python
from __future__ import annotations

def hcn_score(entropy, kl_to_init, alpha=1.0, beta=1.0):
    return alpha * entropy - beta * kl_to_init
```

Do not retarget locked SOTA from this recipe.
