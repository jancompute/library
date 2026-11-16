---
id: recipe:acerl
type: recipe
title: ACE-RL
method: method:acerl
task: task:agent-memory
target_hardware: 'Paper: Qwen3-0.6B / Qwen3-4B-Instruct-2507 ACE-harness GRPO'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- acerl
---

# ACE-RL

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-16. Freeze the ACE harness. Co-optimize actor/reflector/curator with per-role GRPO groups. Reward handoff artifacts by a downstream actor rollout.

## Quickstart Implementation

```python
from __future__ import annotations

from typing import Mapping

import torch


def role_groups(rollouts: Mapping[str, torch.Tensor]) -> dict[str, torch.Tensor]:
    return {role: adv for role, adv in rollouts.items()}
```

Do not retarget locked SOTA from this recipe.
