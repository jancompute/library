---
id: paper:muon-first-moe-layer
type: paper
title: 'Muon Makes the First Mixture-of-Experts Layer Harder to Balance'
authors:
- 'Marcos Hernanz'
year: 2026
month: 10
arxiv_id: '2610.37914'
url: https://arxiv.org/abs/2610.37914
methods:
- method:muon2
- method:energycal
cites:
- paper:muon2
- paper:energycal
tags:
- muon
- moe
- gotcha
---

# Muon Makes the First Mixture-of-Experts Layer Harder to Balance

## Abstract Summary
At tuned LRs, Muon roughly doubles the routing-bias span of the first MoE layer at every seed. The rise comes from Muon on the rest of the net, whichever optimizer trains the router. First-router inputs share a direction; subtracting the batch mean removes overload with little loss change. Halving Muon LR removes most of the rise. Code marcoshernanz/muon-moe-routing.

## Key Contributions
1. First-MoE-layer routing-span gotcha under Muon; not a Muon2 retarget.

## Empirical Highlights
55M and 108M active MoE. Busiest expert 4-7x fair share after warmup. Complements method:energycal (spike damper, different failure).

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.37914`
- Code: `https://github.com/marcoshernanz/muon-moe-routing (`code_status: released`).`
