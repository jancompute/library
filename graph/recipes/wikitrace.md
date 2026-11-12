---
id: recipe:wikitrace
type: recipe
title: WikiTrace
method: method:wikitrace
task: task:agent-memory
target_hardware: 'Paper: text-world and tool-use agent rollouts; memory is files plus terminal descent'
framework: PyTorch
repo_url: https://github.com/yukyeongleee/wikitrace
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- wikitrace
---

# WikiTrace

## Hardware & Environment Setup
- Official: `https://github.com/yukyeongleee/wikitrace` (`code_status: released`).
- Construct memory offline. Keep insights linked to compilations and raw trajectories. Do not rewrite insights at test time.

## Quickstart Implementation

```python
from __future__ import annotations

from dataclasses import dataclass


@dataclass(frozen=True)
class Insight:
    text: str
    compilation_id: str
    trajectory_id: str
    source_succeeded: bool


def should_descend(insight: Insight, missing_detail: bool, conflict: bool) -> bool:
    return missing_detail or conflict or (not insight.source_succeeded)
```

Do not retarget locked SOTA from this recipe.
