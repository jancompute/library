---
id: recipe:cros
type: recipe
title: 'CRoS'
method: method:cros
task: task:math-code-rl-dense
target_hardware: 'Paper: Gemma-3-4B Reasoning Gym'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- cros
---

# CRoS

## Hardware & Environment Setup
- Official: `none found`. Project: `https://xxiaoyuuuu.github.io/CRoS-Page`.
- `code_status: none` as of 2026-11-02.

## Quickstart Implementation

```python
from __future__ import annotations
import random

def scramble_steps(steps, rng=None):
    order = list(steps)
    (rng or random).shuffle(order)
    return order

def cros_reward(answer_ok, scrambled_ok):
    return float(answer_ok) + float(answer_ok and not scrambled_ok)
```

Do not retarget locked SOTA from this recipe.
