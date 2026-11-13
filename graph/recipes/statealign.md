---
id: recipe:statealign
type: recipe
title: StateAlign
method: method:statealign
task: task:agentic-async-rl
target_hardware: 'Paper: Qwen3-8B BFCL v4 multi-turn tool RL'
framework: PyTorch
repo_url: https://github.com/ZhexiLu/StateAlign
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- statealign
---

# StateAlign

## Hardware & Environment Setup
- Official: `https://github.com/ZhexiLu/StateAlign` (`code_status: released`).
- Contrast call vs ask/wait at the current task state. Do not treat a higher outcome reward as a hallucination win.

## Quickstart Implementation

```python
from __future__ import annotations

from typing import Literal


Action = Literal["call", "ask", "wait"]


def state_ok(action: Action, has_args: bool, tool_ready: bool) -> bool:
    if action == "call":
        return has_args and tool_ready
    if action == "ask":
        return not has_args
    return not tool_ready
```

Do not retarget locked SOTA from this recipe.
