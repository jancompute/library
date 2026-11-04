---
id: recipe:toolspace
type: recipe
title: 'ToolSpace'
method: method:toolspace
task: task:coding-agent-rl-environment-construction
target_hardware: 'Paper: Qwen3.6-35B-A3B / GLM-5.2 SFT then RL'
framework: PyTorch
repo_url: https://github.com/dongguanting/ToolSpace
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- toolspace
---

# ToolSpace

## Hardware & Environment Setup
- Official: `https://github.com/dongguanting/ToolSpace`.
- `code_status: released` as of 2026-11-04.

## Quickstart Implementation

```python
from __future__ import annotations

def toolspace_env(mcp_trace):
    return {"tools": mcp_trace["tools"], "task": mcp_trace["task"]}
```

Do not retarget locked SOTA from this recipe.
