# Applying AI to Telecommunications Problems

The most useful habit I built this term was treating every lab's starter code as something to check
rather than something to trust. That habit is the actual throughline of how I applied AI concepts
across the course, more than any single algorithm.

The clearest example was the traffic-prediction work. A Random Forest regressor on network traffic
data hit a test R² of 0.893 — a solid result on its own — but the more important moment came later,
in a time-series assignment, when I found a genuine data-leakage bug in a rolling-average feature:
the window included the current timestep, so the model could partially see the answer it was
supposed to predict. I fixed it and reported both versions honestly rather than quietly using the
inflated number. When I rebuilt a lag-1 predictor for the Final Exam Portfolio, I deliberately kept
the feature strictly backward-looking and got an R² of 0.884 — lower than the leaked version, but
real.

![Random Forest traffic prediction](../assets/rf_traffic.png)

Model compression was the other place this mattered. Starting from a 51.3 KB IoT classifier
baseline, I ran pruning, INT8 quantization, and distillation, and ended up with a 4.9 KB distilled
model at 91.70% accuracy — a 10.49× compression with a small accuracy cost. But two things in the
provided lab code didn't hold up under inspection: the claimed 4× quantization compression didn't
survive at the file level for a model this small, because TFLite's container overhead eats into the
theoretical saving, and the "distillation" code defined a temperature-scaled loss that was never
actually applied during training. I implemented real distillation myself to compare, and it
performed slightly worse (90.95%) — a useful reminder that soft targets don't automatically help,
especially when a small student network can already learn well from hard labels alone.

![Compression trade-off](../assets/compression.png)

Applying AI to routing decisions in Module 10 made the same point from a different angle. I
simulated three routers with different service rates and compared random packet routing against a
simple load-aware policy that just sends each packet to whichever router currently has the shortest
queue. Under near-saturation traffic, random routing let the mean queue climb to 60.4 with a peak of
278; the load-aware policy held it at a mean of 1.0. That's about as simple as an "AI" decision rule
gets, and it was still the difference between a stable system and a runaway one — which is a good
corrective against thinking AI in telecom always means something as heavy as a deep network.

Across all of these, the consistent thing I applied wasn't a specific model so much as a discipline:
run the code myself, check what it's actually doing against what it claims to do, and report the
real number even when it's less impressive than the one I was handed.
