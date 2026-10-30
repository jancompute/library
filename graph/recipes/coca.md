---
id: recipe:coca
type: recipe
title: 'CoCA'
method: method:coca
task: task:outcome-only-long-horizon-agent-rl
target_hardware: 'Paper: open-ended rubric RL'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- coca
---

# CoCA

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-30.

## Quickstart Implementation

```python
from __future__ import annotations

def coca_gap(query_only, rubric_guided):
    return rubric_guided.mean() - query_only.mean()
```

Do not retarget locked SOTA from this recipe.
