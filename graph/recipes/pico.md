---
id: recipe:pico
type: recipe
title: 'PICO'
method: method:pico
task: task:all-zero-verifier-groups
target_hardware: 'Paper: hard-problem RLVR'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- pico
---

# PICO

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-28.

## Quickstart Implementation

```python
from __future__ import annotations

def topk_budget(student_probs, expert_id, k=16):
    keep = set(student_probs.argsort()[-k:].tolist())
    keep.add(int(expert_id))
    return keep
```

Do not retarget locked SOTA from this recipe.
