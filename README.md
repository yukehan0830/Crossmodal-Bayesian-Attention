# Crossmodal Bayesian Attention: Leaky Bayesian model of crossmodal attention in an oddball task
This project investigates how humans adapt to changing sensory statistics in a crossmodal oddball task. In this paradigm, the probability of auditory and visual deviants reverses across phases, requiring participants to continuously update their expectations.

Behaviorally, participants respond faster to stimuli that are more likely under the current environment, and show rapid adaptation following the reversal. However, standard analyses alone do not explain *how* these expectations are formed and updated over time.

To address this, I implemented a simple computational model based on Bayesian updating. Importantly, I compared a full accumulation model (λ = 1.0) with a leaky updating model that discounts older evidence. Model comparison shows that a leaky Bayesian learner (λ ≈ 0.90) provides a substantially better fit to reaction time data, suggesting that participants rely more on recent evidence rather than integrating information uniformly over time.

Further analysis shows that a belief-weighted measure of sensory evidence strongly predicts trial-by-trial reaction times, linking the latent internal model to observable behavior. Additionally, estimated belief trajectories reveal a gradual shift in modality weighting around the reversal point, consistent with adaptive updating rather than abrupt switching.

Together, these results suggest that human crossmodal attention can be understood as a dynamic, recency-weighted inference process, rather than a static or fully optimal accumulator.

---

## Figures
<img width="2550" height="1500" alt="figure_lambda_tuning" src="https://github.com/user-attachments/assets/ec2154fb-1a11-4fb7-9fa5-b3346964b21f" />

---

## Approach

To understand how expectations are formed and updated, I modeled behavior using a leaky Bayesian framework. Separate belief states were maintained for auditory and visual streams and updated trial-by-trial under a Beta-Bernoulli scheme. A forgetting factor (λ) controls the influence of past observations, allowing the model to weight recent evidence more strongly.

Reaction time was then modeled as a function of belief-weighted sensory evidence. For each trial, evidence is computed from the current belief of the relevant modality (or both modalities for double deviants), linking latent expectations to observable behavior.

---

## Behavioral Summary

Participants adapted rapidly after the probability reversal. Reaction times decreased in Phase 2, while accuracy (hit and false alarm rates) remained stable. After reversal, visual deviants became faster than auditory deviants, and double deviants produced the fastest responses, consistent with dynamic reweighting across modalities.

---

## Key Finding

Model comparison shows that a leaky Bayesian learner (λ ≈ 0.90) fits the data substantially better than a full accumulation model (λ = 1.0). In addition, belief-weighted evidence strongly predicts trial-by-trial reaction times, suggesting that behavior reflects a recency-weighted internal inference process rather than uniform evidence accumulation.
