---
id: recipe:copd
type: recipe
title: COPD
method: method:copd
task: task:student-distillation
target_hardware: 'Paper: Qwen3.5-4B/9B CAMG-II plus TB 2.1 / SWE-Bench Pro V2 transfer'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- copd
---

# COPD

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-19 (project https://liruiluo.github.io/communicative-opsd/). Student-initiated NL consult of a black-box teacher, then privileged OPSD on adviser-free rollouts plus task-reward RL.

## Quickstart Implementation

```python
from __future__ import annotations


def copd_keep_consult(success: bool, consulted: bool) -> bool:
    return success and consulted
```

Do not retarget locked SOTA from this recipe.
