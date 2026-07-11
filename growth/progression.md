# Growth Evidence — From Basic Concepts to Advanced AI Applications

A module-by-module map of how my competencies moved from telecom fundamentals to applied AI, with
concrete before/after evidence rather than a general claim of "I learned a lot."

## Stage 1 — Foundations (Modules 1–2)
**Before:** Telecom was a black box — phones and Wi-Fi that either worked or didn't.
**After:** I could compute and plot free-space path loss myself, and explain why higher frequencies
need denser infrastructure.
**Evidence:** [FSPL simulation](../projects/01-fspl-rf-propagation.md)

## Stage 2 — Systems thinking (Modules 3–5)
**Before:** "The network" was a single undifferentiated pipe.
**After:** I could design a resource allocator that treats latency and throughput as genuinely
separate constraints across three 5G slice types, and explain why an intelligent controller (RIC)
changes what's possible in a RAN.
**Evidence:** [Network slicing allocation](../projects/02-network-slicing.md) — 139/278/82 unit
split across URLLC/eMBB/mMTC

## Stage 3 — Applied ML, and learning to check my own work (Module 6)
**Before:** I would run a provided script and report whatever metric it printed.
**After:** I caught a genuine data-leakage bug in a rolling-average feature, diagnosed why it
inflated R² to a fabricated 1.0, and reported the corrected, honest number instead.
**Evidence:** [Traffic prediction and the leakage catch](../projects/03-traffic-prediction.md)

## Stage 4 — Auditing techniques, not just applying them (Modules 6–7)
**Before:** Compression was "magic" — apply pruning or quantization, get a smaller model.
**After:** I could show that an advertised 4× quantization gain didn't hold at the file level, and
that a "distillation" script never actually applied its own loss function — then implement the real
version myself and compare honestly.
**Evidence:** [Edge AI compression](../projects/04-edge-ai-compression.md)

## Stage 5 — Building and testing my own simulations (Module 10)
**Before:** I could train a model on a fixed dataset someone else prepared.
**After:** I could design a discrete-event simulation and an agent-based model from scratch to test
a specific hypothesis (does load-aware routing beat random routing under contention?), and trust the
comparison because I built both sides of it myself.
**Evidence:** [Digital-twin-style routing simulations](../projects/05-digital-twin-labs.md) — mean
queue 60.4 (random) vs. 1.0 (load-aware)

## Stage 6 — Systems-level architecture and responsibility (Modules 11–13)
**Before:** AI in a network meant "a model that makes a prediction."
**After:** I could place that model inside a full reference architecture (REASON's layered AI-native
design), quantify a real operational trade-off (42.9% energy savings from sleep scheduling), and
identify a concrete gap in my own work — none of my labs this term included a fairness audit, which
is a genuine limitation, not a hypothetical one.
**Evidence:** [Energy/sustainability lab](../projects/06-energy-sustainability.md); reflections on
[ethics and future growth](../reflections/03-skills-and-future-growth.md)

## The throughline
Every stage above involved the same underlying move: don't just run the code, check what it's
actually doing. That's the competency that compounded the most across the term — it's the same
instinct whether I'm looking at a rolling-average feature, a distillation loss, a compression ratio,
or, going forward, a fairness check I haven't built yet.
