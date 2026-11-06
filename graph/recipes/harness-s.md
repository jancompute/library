---
id: recipe:harness-s
type: recipe
title: 'Harness-S'
method: method:harness-s
task: task:agent-harness-runtime
target_hardware: 'Paper: Qwen3.5-4B/9B GRPO, AppWorld / SWE-Gym / DBBench'
framework: PyTorch
repo_url: https://github.com/DeepExperience/Harness-S
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- harness-s
---

# Harness-S

## Hardware & Environment Setup
- Official: `https://github.com/DeepExperience/Harness-S`.
- `code_status: released` as of 2026-11-06.

## Quickstart Implementation

```python
from __future__ import annotations

def harness_s_rescue(group_rewards, sibling_rewards, sibling_ok):
    if any(r > 0 for r in group_rewards) or not sibling_ok:
        return group_rewards
    return sibling_rewards
```

Do not retarget locked SOTA from this recipe.
