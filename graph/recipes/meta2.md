---
id: recipe:meta2
type: recipe
title: 'Meta2'
method: method:meta2
task: task:agent-harness-runtime
target_hardware: 'Paper: GPT-5.6-Terra harness control'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- meta2
---

# Meta2

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-04.

## Quickstart Implementation

```python
from __future__ import annotations

def meta2_gate(skill_fail_rate, threshold):
    return "evolve" if skill_fail_rate > threshold else "keep"
```

Do not retarget locked SOTA from this recipe.
