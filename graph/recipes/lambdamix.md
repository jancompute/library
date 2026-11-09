---
id: recipe:lambdamix
type: recipe
title: 'LambdaMix'
method: method:lambdamix
task: task:multi-reward-rlvr
target_hardware: 'Paper: four instruct models including Qwen3.5-9B; 500 GRPO updates'
framework: PyTorch
repo_url: https://github.com/ckarouzos/lambdamix
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- lambdamix
---

# LambdaMix

## Hardware & Environment Setup
- Official: `https://github.com/ckarouzos/lambdamix`.
- `code_status: released` as of 2026-11-09. Host: group-relative online RL with per-objective LoRA.

## Quickstart Implementation

```python
from __future__ import annotations

def lambdamix_weights(pref, adapters):
    w = [p / sum(pref) for p in pref]
    return [(wi, a) for wi, a in zip(w, adapters)]
```

Do not retarget locked SOTA from this recipe.
