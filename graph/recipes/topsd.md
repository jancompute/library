---
id: recipe:topsd
type: recipe
title: 'TOPSD'
method: method:topsd
task: task:privileged-teacher-opsd
target_hardware: 'Paper: Qwen3-1.7B/4B/8B, PolyMath High, completion 8k/12k'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- topsd
---

# TOPSD

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-09.

## Quickstart Implementation

```python
from __future__ import annotations

def topsd_keep_prefix(teacher_recovers, persist_k=4):
    return teacher_recovers and persist_k >= 4
```

Do not retarget locked SOTA from this recipe.
