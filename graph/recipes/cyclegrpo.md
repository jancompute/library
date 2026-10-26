---
id: recipe:cyclegrpo
type: recipe
title: 'CycleGRPO'
method: method:cyclegrpo
task: task:mllm-finegrained-perception-rl
target_hardware: 'Paper: fine-grained multimodal understand + ground'
framework: PyTorch
repo_url: https://github.com/devinxzhang/CycleGRPO
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- cyclegrpo
---

# CycleGRPO

## Hardware & Environment Setup
- Official: `https://github.com/devinxzhang/CycleGRPO`.
- `code_status: released` as of 2026-10-26.

## Quickstart Implementation

```python
from __future__ import annotations

def cycle(understand_ok: bool, local_ok: bool) -> bool:
    return understand_ok and local_ok
```

Do not retarget locked SOTA from this recipe.
