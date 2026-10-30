---
id: recipe:ati-opd
type: recipe
title: 'ATI-OPD'
method: method:ati-opd
task: task:student-distillation
target_hardware: 'Paper: long-sequence OPD students'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- ati-opd
---

# ATI-OPD

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-30.

## Quickstart Implementation

```python
from __future__ import annotations

def ati_splice(student_ids, disagree_mask, teacher_span):
    i = int(disagree_mask.nonzero()[0])
    return student_ids[:i] + teacher_span + student_ids[i + len(teacher_span):]
```

Do not retarget locked SOTA from this recipe.
