---
id: recipe:rlvb
type: recipe
title: RLVB
method: method:rlvb
task: task:outcome-only-long-horizon-agent-rl
target_hardware: 'Paper: three VLMs on Pro-Worlds plus two OOD benches'
framework: PyTorch
repo_url: https://github.com/declare-lab/RLVB
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- rlvb
---

# RLVB

## Hardware & Environment Setup
- Official: `https://github.com/declare-lab/RLVB`
- `code_status: released` as of 2026-11-25. Simulator posterior over a hidden answer; never read the agent-written belief. Does not replace CANOPY or CISPO.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def rlvb_reward(
    posterior: torch.Tensor,
    committed: bool,
    tau: float = 0.9,
) -> torch.Tensor:
    mass = posterior.max(dim=-1).values
    if committed:
        return mass - tau
    return tau - mass
```
