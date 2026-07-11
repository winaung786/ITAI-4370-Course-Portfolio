# Project 1 — Free-Space Path Loss Simulation

**Module:** 2 (RF Propagation)

## Problem statement
Model how signal strength degrades with distance for a 2.4 GHz link using the log-distance free-
space path loss (FSPL) equation, and use the result to reason about why higher-frequency bands (5G
mmWave, 6G terahertz) need denser infrastructure.

## Methods and tools
Python, NumPy, Matplotlib. FSPL computed directly from the standard log-distance formula:

```python
d = np.linspace(0.1, 20, 100)       # distance, km
f = 2400.0                          # frequency, MHz
fspl = 20*np.log10(d) + 20*np.log10(f) + 32.44   # dB
```

## Result

![FSPL vs distance](../assets/fspl.png)

Path loss rises roughly 6 dB every time distance doubles, consistent with the squared-distance term
in the model.

## Interpretation
Because both the distance and frequency terms are squared inside the log, moving from 2.4 GHz to a
mmWave or terahertz band multiplies the path-loss penalty for the same distance dramatically. That
single relationship is the physical reason 6G designs lean so heavily on RIS (reconfigurable
intelligent surfaces) and dense small-cell deployment — there's no way around the physics, only ways
to compensate for it architecturally.
