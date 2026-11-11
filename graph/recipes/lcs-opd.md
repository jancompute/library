---
id: recipe:lcs-opd
type: recipe
title: 'LCS-OPD'
method: method:lcs-opd
task: task:outcome-only-long-horizon-agent-rl
target_hardware: 'Paper: Qwen2.5-3B/7B ALFWorld; Qwen3.5-2B/4B τ³-bench'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- lcs-opd
---

# LCS-OPD

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-11. Host is a multi-turn reverse-KL OPD trainer.

## Quickstart Implementation

```python
from __future__ import annotations

def lcs_len(a: list, b: list) -> int:
    n, m = len(a), len(b)
    dp = [0] * (m + 1)
    for x in a:
        prev = 0
        for j, y in enumerate(b, 1):
            cur = dp[j]
            dp[j] = prev + 1 if x == y else max(dp[j], dp[j - 1])
            prev = cur
    return dp[m]


def pick_reference(failed_actions: list, successes: list[list]) -> list:
    return max(successes, key=lambda s: lcs_len(failed_actions, s) / max(len(failed_actions), len(s), 1))
```

Do not retarget locked SOTA from this recipe.
