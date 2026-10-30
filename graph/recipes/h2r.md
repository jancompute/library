---
id: recipe:h2r
type: recipe
title: 'H2R'
method: method:h2r
task: task:math-code-rl-dense
target_hardware: 'Paper: hierarchical math RLVR / HiMath'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- h2r
---

# H2R

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-30.

## Quickstart Implementation

```python
from __future__ import annotations

def h2r_reward(solved_subqs, n_subqs, final_ok):
    return 0.5 * (solved_subqs / max(n_subqs, 1)) + 0.5 * float(final_ok)
```

Do not retarget locked SOTA from this recipe.
