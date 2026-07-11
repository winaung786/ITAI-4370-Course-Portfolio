# Skills I Improved and Where I Want to Grow

**What got stronger.** The clearest jump this term was going from "run the lab code and report the
metric" to "run the lab code and interrogate whether the metric means what it claims to." That shift
showed up repeatedly — catching the rolling-average leakage in the traffic-prediction lab, catching
that a distillation loss was defined but never optimized against, catching that a compression ratio
didn't hold at the file level once container overhead was accounted for. None of these were things
the assignment explicitly asked me to look for; they were things that turned up because I got in the
habit of reading code as a claim to verify rather than a black box to execute.

I also got noticeably more comfortable moving between simulation frameworks — SimPy for discrete-
event queueing, a hand-rolled agent-based model for load balancing, scikit-learn and PyTorch for the
prediction and compression work, and small optimization scripts for the energy modules. Going into
the course I could write a script that trained a model; by the end I could design a small simulation
from scratch to test a specific hypothesis (does load-aware routing actually beat random routing
under realistic contention?) and trust the result because I built the comparison myself.

**Where I still want to grow.** The ethics module made a gap in my own labs visible: none of the
models or allocators I built this term had anything resembling a fairness check across user groups.
A slicing allocator or a load-aware router is making real prioritization decisions, and I don't yet
have practical experience building the kind of fairness audit that should sit alongside a system
like that before it's trusted with production traffic. That's the concrete skill I'd want to build
next — not just knowing the frameworks (IEEE, OECD, EU AI Act) conceptually, but being able to
implement a bias check against a model the way I'd implement a unit test.

I'd also like to go deeper on reinforcement learning specifically. The Q-learning energy-saving
agent from Module 9/12 is the natural next step past the threshold-based sleep scheduler I built for
this portfolio — a fixed 25%-of-peak cutoff is an easy baseline to beat, and I'd like to actually
build and train the RL version that adapts the threshold itself rather than having it hand-set, to
see how much of a gap there really is between a simple rule and a learned policy on the same
problem.

Finally, digital twins are the piece of the course I understand the least deeply relative to how
central the reading made them to 6G. My SimPy and agent-based simulations are, at best, toy versions
of the pattern Sheraz et al. describe — a real digital twin needs continuous synchronization with
live network state, which is a much harder systems problem than anything I built this term. That's
the direction I'd want to take a follow-up project if I get the chance.
