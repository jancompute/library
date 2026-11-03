---
id: recipe:swe-trail
type: recipe
title: 'SWE-Trail'
method: method:swe-trail
task: task:coding-agent-rl-environment-construction
target_hardware: 'Paper: 124B student trained on collected SWE trajectories'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- swe-trail
---

# SWE-Trail

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def choose_route(candidates, scores):
    return candidates[max(range(len(scores)), key=scores.__getitem__)]
```

Do not retarget locked SOTA from this recipe.
