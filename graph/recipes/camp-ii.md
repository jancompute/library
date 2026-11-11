---
id: recipe:camp-ii
type: recipe
title: 'CAMP-II'
method: method:camp-ii
task: task:agent-memory
target_hardware: 'Paper: Qwen3.5-4B/9B, fully asynchronous OPD, CAMG-II five envs'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- camp-ii
---

# CAMP-II

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-11. Memory is ordinary files plus a bounded continuation file written before context replacement. Do not introduce a dedicated memory tool.

## Quickstart Implementation

```python
from __future__ import annotations

def camp_ii_context_replace(workspace, write_continuation, clear_context):
    path = write_continuation(workspace)
    clear_context()
    return path
```

Do not retarget locked SOTA from this recipe.
