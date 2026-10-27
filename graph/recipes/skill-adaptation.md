---
id: recipe:skill-adaptation
type: recipe
title: 'Skill Adaptation'
method: method:skill-adaptation
task: task:agent-harness-runtime
target_hardware: 'Paper: harness skill rewrite'
framework: PyTorch
repo_url: https://zhihaoyang30.github.io/skill-adaptation/
code_status: announced
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- skill-adaptation
---

# Skill Adaptation

## Hardware & Environment Setup
- Official: `https://zhihaoyang30.github.io/skill-adaptation/`.
- `code_status: announced` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def too_hard(skill: str, failed_req: str) -> bool:
    return failed_req in skill
```

Do not retarget locked SOTA from this recipe.
