---
id: paper:speculative-diffusion-tradeoffs
type: paper
title: 'Speculative Diffusion is a Tale of Two Tradeoffs'
authors:
- 'Aaron Zorel'
- 'Guy Van den Broeck'
- 'Aditya Grover'
- 'Daniel Israel'
year: 2026
month: 10
arxiv_id: '2610.31819'
url: https://arxiv.org/abs/2610.31819
methods:
- method:uno
cites:
- paper:uno
tags:
- serving
- gotcha
- speculative-decoding
---

# Speculative Diffusion is a Tale of Two Tradeoffs

## Abstract Summary
Speculative decoding is lossless wrt the verifier; diffusion LMs are not. Treating speculative diffusion as a drop-in speedup hides a quality/speed tradeoff the AR spec decoder does not pay.

## Key Contributions
1. Speculative vs diffusion speed/quality tradeoff; not a serving default.

## Empirical Highlights
- Does not retarget Uno. Do not score dLLM speed as if it were lossless speculative decoding.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.31819`
- Code: `none found` (`code_status: none`).
