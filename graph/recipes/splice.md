---
id: recipe:splice
type: recipe
title: SPLICE
method: method:splice
task: task:outcome-only-long-horizon-agent-rl
target_hardware: 'Paper: SWE-bench Verified and BrowseComp-Plus vs GRPO'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- splice
---

# SPLICE

## Hardware & Environment Setup
- `code_status: none` as of 2026-11-26. Branch-point splice of bounded proposal options into learner continuations. Distinct from GRAFT / Harness-S / PICO / VeriGate. Does not replace CANOPY.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def splice_target(
    option_logp: torch.Tensor,
    continuation_return: torch.Tensor,
) -> torch.Tensor:
    weight = continuation_return - continuation_return.mean()
    return -(weight.detach() * option_logp).mean()
```
