# Crossmodal-Bayesian-Attention
Leaky Bayesian model of crossmodal attention in an oddball task
# Crossmodal Bayesian Attention Model

This project models how humans dynamically reweight sensory modalities using a leaky Bayesian belief-updating process in a crossmodal oddball task.

---

## Overview

In a crossmodal oddball paradigm, participants respond to rare (deviant) stimuli presented in auditory and/or visual modalities. The probability structure reverses across phases, requiring adaptation. Instead of relying on static comparisons, this project implements a **trial-by-trial computational model** to explain behavioral dynamics.

---

## Key Questions

- How do humans adapt to changing stimulus probabilities?
- Do participants track modality-specific reliability over time?
- Can reaction times be explained by an internal belief-updating process?

---

## Behavioral Results

- Reaction times were significantly faster in Phase 2 compared to Phase 1  
- No significant changes in hit rate or false alarm rate  
- Visual deviants became faster than auditory deviants after reversal  
- Double deviants (both auditory + visual) produced the fastest responses  

These results suggest dynamic reweighting of attention across modalities.

---

## Computational Model

We implemented a **leaky Bayesian belief-updating model**:

- Each modality (auditory, visual) is tracked separately  
- Beliefs are updated trial-by-trial using a Beta-Bernoulli framework  
- A forgetting factor (λ) discounts older observations  

### Belief update

At each trial:

- Estimate current belief:
  - `belief_visual = alpha_v / (alpha_v + beta_v)`
  - `belief_auditory = alpha_a / (alpha_a + beta_a)`

- Apply decay:
  - `alpha *= λ`
  - `beta *= λ`

- Update with new observation

---

## Evidence Model

Reaction time is modeled as a function of **belief-weighted sensory evidence**:

- Visual deviant → uses visual belief  
- Auditory deviant → uses auditory belief  
- Double deviant → sum of both  

```python
total_evidence = belief_visual * visual_deviant + belief_auditory * auditory_deviant
