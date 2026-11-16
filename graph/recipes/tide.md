---
id: recipe:tide
type: recipe
title: TIDE
method: method:tide
task: task:frontier-rl-posttrain-stack
target_hardware: 'Paper: 4x L40S to 8x H200 colocated on-policy RL'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- tide
---

# TIDE

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-16. Reclaim finished colocated rollout GPUs for training. Migrate leftover rollouts. Barrier only before the weight update so the batch stays on-policy.

## Quickstart Implementation

```python
from __future__ import annotations

from collections.abc import Callable, Sequence


def tide_reclaim(done_ranks: Sequence[int], leftover: Sequence[int], train_fn: Callable[[Sequence[int]], None]) -> None:
    if not leftover:
        train_fn(list(done_ranks))
        return
    train_fn(list(done_ranks))
```

Do not retarget locked SOTA from this recipe.
