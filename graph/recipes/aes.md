---
id: recipe:aes
type: recipe
title: 'AES'
method: method:aes
task: task:math-code-rl-dense
target_hardware: 'Paper: DeepSeek-R1-Distill-Qwen 1.5B/7B'
framework: PyTorch
repo_url: https://github.com/MobiusDai/AES
code_status: announced
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- aes
---

# AES

## Hardware & Environment Setup
- Official: `https://github.com/MobiusDai/AES` (`code_status: announced`; 404 as of 2026-11-10).
- Host is GRPO-family.

## Quickstart Implementation

```python
from __future__ import annotations

def aes_keep_entropy(correct: bool, token_entropy: float, thresh: float) -> bool:
    if not correct:
        return True
    return token_entropy < thresh
```

Do not retarget locked SOTA from this recipe.
