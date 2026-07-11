# Project 2 — AI-Driven 5G Network Slicing Allocation

**Module:** 4 (5G Core, Slicing, MEC)

## Problem statement
Given a fixed pool of 500 network resource units and three 5G slice types with different service
requirements — URLLC (ultra-reliable low-latency), eMBB (enhanced mobile broadband), and mMTC
(massive machine-type communication) — allocate the pool so each slice gets resources proportional
to its actual traffic profile rather than an even split.

## Methods and tools
Python, NumPy, Matplotlib. Each slice type carries a weighted demand profile (URLLC weighted heavily
toward latency-sensitivity rather than volume; eMBB weighted toward raw throughput; mMTC weighted
toward device count with low per-device demand); the allocator distributes the 500-unit pool
proportionally to those weights.

## Result

![Slice allocation](../assets/slicing.png)

| Slice | Units allocated | Share |
|---|---|---|
| URLLC | 139 | 27.8% |
| eMBB | 278 | 55.6% |
| mMTC | 82 | 16.4% |

## Interpretation
eMBB dominating makes sense given how bandwidth-hungry it is. What's more interesting is that URLLC
still gets a meaningfully larger share than mMTC despite carrying far less data overall — because
its binding constraint is latency, not throughput. A resource allocator that only reasoned about
data volume would badly under-serve URLLC; getting slicing right means keeping latency and
throughput as genuinely separate axes rather than collapsing them into a single "resource" number.
