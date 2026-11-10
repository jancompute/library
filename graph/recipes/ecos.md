---
id: recipe:ecos
type: recipe
title: 'ECOS'
method: method:ecos
task: task:outcome-only-long-horizon-agent-rl
target_hardware: 'Paper: Qwen2.5-3B/7B ALFWorld/WebShop'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- ecos
---

# ECOS

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-10.

## Quickstart Implementation

```python
from __future__ import annotations

def ecos_teacher_context(command: str, env_token: str) -> str:
    return f"{command}{env_token}"
```

Do not retarget locked SOTA from this recipe.
