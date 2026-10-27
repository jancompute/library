---
id: recipe:swe-ladder
type: recipe
title: 'SWE-Ladder'
method: method:swe-ladder
task: task:privileged-teacher-opsd
target_hardware: 'Paper: Qwen3-4B SWE-bench Verified'
framework: PyTorch
repo_url: https://github.com/sekongger/SWE-Ladder
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- swe-ladder
---

# SWE-Ladder

## Hardware & Environment Setup
- Official: `https://github.com/sekongger/SWE-Ladder`.
- `code_status: released` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def stage_of(tool: str) -> str:
    if tool in {'find', 'grep', 'read'}:
        return 'localize'
    if tool in {'test', 'run'}:
        return 'reproduce'
    return 'patch'
```

Do not retarget locked SOTA from this recipe.
