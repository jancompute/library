---
id: recipe:b-opsd
type: recipe
title: B-OPSD
method: method:b-opsd
task: task:privileged-teacher-opsd
target_hardware: 'Paper: Qwen3 1.7B/4B/8B OPSD without GT'
framework: PyTorch
repo_url: https://github.com/ZevineXu/B-OPSD
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- b-opsd
---

# B-OPSD

## Hardware & Environment Setup
- Official: `https://github.com/ZevineXu/B-OPSD` (`code_status: released`).
- Generate a brief from the question (no answer). Condition the frozen teacher on the brief. Reverse-KL the student onto that teacher on live rollouts.

## Quickstart Implementation

```python
from __future__ import annotations

BRIEF_PROMPT = "List principles, applicability conditions, and pitfalls. Do not give a final answer.\nQuestion: {q}\nBrief:"
```

Do not retarget locked SOTA from this recipe.
