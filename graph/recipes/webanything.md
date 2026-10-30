---
id: recipe:webanything
type: recipe
title: 'WebAnything'
method: method:webanything
task: task:hybrid-computer-use-agent-rl
target_hardware: 'Paper: 244 reconstructed websites'
framework: PyTorch
repo_url: https://github.com/china-qijizhifeng/Web-Anything
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- webanything
---

# WebAnything

## Hardware & Environment Setup
- Official: `https://github.com/china-qijizhifeng/Web-Anything`.
- `code_status: released` as of 2026-10-30.

## Quickstart Implementation

```python
from __future__ import annotations

def webanything_accept(verifier_ok, n_repair):
    return verifier_ok and n_repair == 0
```

Do not retarget locked SOTA from this recipe.
