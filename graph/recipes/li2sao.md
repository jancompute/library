---
id: recipe:li2sao
type: recipe
title: 'Li2SAO'
method: method:li2sao
task: task:agentic-async-rl
target_hardware: 'Paper: slime async RL'
framework: PyTorch
repo_url: https://github.com/jd-cc-coder/Li2SAO
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- li2sao
---

# Li2SAO

## Hardware & Environment Setup
- Official: `https://github.com/jd-cc-coder/Li2SAO`.
- `code_status: released` as of 2026-11-02.

## Quickstart Implementation

```python
from __future__ import annotations

def li2sao_bootstrap(rewards, values, cold):
    centered = rewards - rewards.mean()
    if cold:
        actor_adv = centered
        critic_target = centered
        return actor_adv, critic_target
    return rewards - values, rewards
```

Do not retarget locked SOTA from this recipe.
