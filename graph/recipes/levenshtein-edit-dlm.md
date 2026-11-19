---
id: recipe:levenshtein-edit-dlm
type: recipe
title: Levenshtein Editing (DLM)
method: method:levenshtein-edit-dlm
task: task:diffusion-lm-ar-delta-recycle
target_hardware: 'Paper: LLaDA2.1-Mini 16B insert/delete post-train'
framework: PyTorch
repo_url: https://github.com/inclusionAI/LLaDA2.X
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- levenshtein-edit-dlm
---

# Levenshtein Editing (DLM)

## Hardware & Environment Setup
- Official: `https://github.com/inclusionAI/LLaDA2.X`.
- `code_status: released` as of 2026-11-19 (LLaDA2.2). Post-train insert/delete on a masked dLLM. Distinct from `method:led`.

## Quickstart Implementation

```python
from __future__ import annotations


def levenshtein_ops() -> tuple[str, str, str]:
    return ("insert", "delete", "remask")
```

Do not retarget locked SOTA from this recipe.
