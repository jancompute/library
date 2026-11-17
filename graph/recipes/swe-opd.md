---
id: recipe:swe-opd
type: recipe
title: SWE-OPD
method: method:swe-opd
task: task:student-distillation
target_hardware: 'Paper: Qwen3.5-9B student, cached teacher logp'
framework: PyTorch
repo_url: https://github.com/ernie-research/SWE-OPD
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- swe-opd
---

# SWE-OPD

## Hardware & Environment Setup
- Official: `https://github.com/ernie-research/SWE-OPD` (`code_status: released`).
- Cache teacher logp offline. Do not treat a falling top-K reverse-KL as a resolve-rate signal; monitor repetition.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def swe_opd_repeat_flag(tokens: list[int], ngram: int = 8, thresh: int = 4) -> bool:
    if len(tokens) < ngram * thresh:
        return False
    grams = [tuple(tokens[i:i + ngram]) for i in range(len(tokens) - ngram + 1)]
    return max(grams.count(g) for g in set(grams)) >= thresh
```

Do not retarget locked SOTA from this recipe.
