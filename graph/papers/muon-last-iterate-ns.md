---
id: paper:muon-last-iterate-ns
type: paper
title: 'Last-Iterate Stationarity of Muon with Finitely Many Newton-Schulz Iterations'
authors:
- 'Ping Li'
- 'Vincent Y. F. Tan'
year: 2026
month: 10
arxiv_id: '2610.34158'
url: https://arxiv.org/abs/2610.34158
methods:
- method:muon2
cites:
- paper:muon2
- paper:muon-ns-bias
tags:
- optimizer
- gotcha
- muon
---

# Last-Iterate Stationarity of Muon with Finitely Many Newton-Schulz Iterations

## Abstract Summary
Practical Muon uses a fixed number of quintic Newton-Schulz steps, not an exact polar factor. Without input stabilization it can cycle even on a smooth convex quadratic. With positive stabilization, last-iterate gradient convergence holds for momentum below one and a small constant LR.

## Key Contributions
1. Last-iterate finite-NS Muon analysis; not a train kernel.

## Empirical Highlights
Does not retarget Muon2. Pair with paper:muon-ns-bias.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.34158`
- Code: `none found (`code_status: none`).`
