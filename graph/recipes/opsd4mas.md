---
id: recipe:opsd4mas
type: recipe
title: OPSD4MAS
method: method:opsd4mas
task: task:student-distillation
target_hardware: 'Paper: multi-agent GRPO/DAPO on verl; MATH plus FW4 six-bench'
framework: PyTorch
repo_url: https://github.com/Camel-Prince/OPSD4MAS
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- opsd4mas
---

# OPSD4MAS

## Hardware & Environment Setup
- Official: `https://github.com/Camel-Prince/OPSD4MAS` (`code_status: released`; verl).
- Extract facts from future messages, associate them to tokens, drop LOO-uninformative spans, anneal the OPSD term with GRPO.

## Quickstart Implementation

```python
from __future__ import annotations

from typing import Sequence


def anneal_opsd_weight(step: int, warmup: int, peak: float = 0.3) -> float:
    if warmup <= 0:
        return peak
    return peak * min(1.0, step / warmup)


def keep_loo(token_ids: Sequence[int], useful: Sequence[bool]) -> list[int]:
    return [tid for tid, ok in zip(token_ids, useful) if ok]
```

Do not retarget locked SOTA from this recipe.
