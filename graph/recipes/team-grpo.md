---
id: recipe:team-grpo
type: recipe
title: 'Team-GRPO'
method: method:team-grpo
task: task:math-code-rl-dense
target_hardware: 'Paper: 9B theory plus GlobalOpinionQA / NoveltyBench'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- team-grpo
---

# Team-GRPO

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def team_alpha(k):
    return 1.0  # GRPO uses -1/(k-1)
```

Do not retarget locked SOTA from this recipe.
