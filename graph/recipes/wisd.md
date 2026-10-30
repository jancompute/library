---
id: recipe:wisd
type: recipe
title: 'WISD'
method: method:wisd
task: task:teacher-free-on-policy-self-adaptation
target_hardware: 'Paper: Qwen3.5-4B / Qwen3.6-35B-A3B reasoning'
framework: PyTorch
repo_url: https://github.com/jet-ai-projects/WISD
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- wisd
---

# WISD

## Hardware & Environment Setup
- Official: `https://github.com/jet-ai-projects/WISD`.
- `code_status: released` as of 2026-10-30.

## Quickstart Implementation

```python
from __future__ import annotations

def wisd_advantage(strong_logp, weak_logp):
    return (strong_logp - weak_logp).detach()
```

Do not retarget locked SOTA from this recipe.
