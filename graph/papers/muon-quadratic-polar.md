---
id: paper:muon-quadratic-polar
type: paper
title: 'A Quadratic Lens on Muon''s Polar Update: Benefits, Pitfalls, and the Role of Newton-Schulz'
authors:
- 'Egor Shulgin'
- 'Sam Laing'
- 'Antonio Orvieto'
- 'Peter Richtárik'
year: 2026
month: 10
arxiv_id: '2610.30280'
url: https://arxiv.org/abs/2610.30280
methods:
- method:muon2
cites:
- paper:muon2
tags:
- optimizer
- gotcha
- muon
---

# A Quadratic Lens on Muon's Polar Update

## Abstract Summary
PolarGD, the orthogonalized update inside Muon, is analyzed on matrix quadratics with line search so step size is not a confound. Orthogonalization helps only in some noise/curvature regimes; Newton-Schulz is not free.

## Key Contributions
1. Quadratic/polar analysis of Muon; not a train kernel.

## Empirical Highlights
- Does not retarget Muon2. Orthogonalization is not uniformly better than a rescaled Adam-style step on quadratics.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.30280`
- Code: `none found` (`code_status: none`).
