---
id: recipe:modharness-rl
type: recipe
title: ModHarness-RL
method: method:modharness-rl
task: task:agent-harness-runtime
target_hardware: 'Paper: 1.5B–8B GRPO on CodeSearch / ALFWorld / BIRD'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- modharness-rl
---

# ModHarness-RL

## Hardware & Environment Setup
- Official: `none found`. Project: `https://zlhe0.github.io/ModHarness-RL/`.
- `code_status: none` as of 2026-11-16. Propose/verify/replay Compression and Steering over typed State blocks during GRPO. Install Steering only for failures that persist.

## Quickstart Implementation

```python
from __future__ import annotations

from typing import Literal


def install_program(kind: Literal["compression", "steering"], persistent_fail: bool) -> bool:
    if kind == "steering":
        return persistent_fail
    return True
```

Do not retarget locked SOTA from this recipe.
