---
id: recipe:booknavigator
type: recipe
title: BookNavigator
method: method:booknavigator
task: task:olympiad-math-posttrain
target_hardware: 'Paper: Intern-S2-Preview-35B textbook-study RL'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- booknavigator
---

# BookNavigator

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-12. Treat the textbook as an environment with page/section actions. Keep a downstream proof eval.

## Quickstart Implementation

```python
from __future__ import annotations


def study_reward(
    pages_read: int,
    pages_total: int,
    lemmas_cited: int,
    lemmas_needed: int,
    proof_ok: bool,
) -> float:
    coverage = pages_read / max(pages_total, 1)
    retrieval = lemmas_cited / max(lemmas_needed, 1)
    return 0.25 * coverage + 0.25 * retrieval + float(proof_ok)
```

Do not retarget locked SOTA from this recipe.
