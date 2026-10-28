---
id: recipe:coharl
type: recipe
title: 'CoHARL'
method: method:coharl
task: task:agent-harness-runtime
target_hardware: 'Paper: SWE-rebench / TB2.0 harness RL'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- coharl
---

# CoHARL

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-28.

## Quickstart Implementation

```python
from __future__ import annotations

def pick_harness(scores):
    return max(range(len(scores)), key=lambda i: scores[i])
```

Do not retarget locked SOTA from this recipe.
