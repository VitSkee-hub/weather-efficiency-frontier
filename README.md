# Finding the Efficiency Frontier in Bounded Weather Prediction

## Overview

This project investigates a practical question in applied machine learning:

**What is the most accurate, least resource-intensive approach to predicting next-day weather outcomes within a bounded climate region?**

Rather than optimizing for maximum theoretical accuracy, this work focuses on identifying the point at which additional model complexity no longer produces meaningful performance gains relative to its computational cost. This framing reflects real-world constraints common in operational and commercial settings, where forecasts must be fast, reliable, interpretable, and inexpensive to deploy.

---

## Motivation

Weather-dependent decisions in sectors such as agriculture, energy, logistics, and insurance are often short-horizon and location-specific. In these contexts, highly complex or computationally expensive models may offer limited practical benefit over simpler alternatives, while introducing additional cost, latency, and maintenance burden.

This project explores whether increased model expressiveness genuinely improves predictive performance for next-day rainfall prediction, or whether most usable signal is captured by a small set of physically meaningful variables.

---

## Approach

Using a large, real-world Australian rainfall dataset, multiple model families were evaluated under controlled conditions:

- A naïve baseline classifier  
- Regularized logistic regression (minimal and expanded feature sets)  
- Shallow decision trees with increasing depth  
- A constrained random forest ensemble  

To ensure fair comparison:
- All models were evaluated on the same train/test split  
- A shared preprocessing pipeline handled missing values and categorical variables  
- Performance was assessed using accuracy, recall, precision, F1 score, and training time  

This design isolates the effect of **model complexity** from **information availability**, allowing performance gains to be attributed to model capacity rather than data handling bias.

---

## Key Findings

Across all experiments, results consistently showed that:

- A regularized linear model using a small number of high-coverage, physically interpretable variables achieved near-optimal performance.
- Increasing model complexity produced diminishing—or negative—returns relative to added computational cost.
- Ensemble methods favored precision at the expense of recall, reducing their usefulness for event detection.
- Feature relevance and interpretability mattered more than model expressiveness in this bounded climate setting.

These findings suggest that for short-horizon, local weather prediction tasks, **predictive efficiency is maximized through careful feature selection rather than increasingly complex models**.

---

## Why This Matters

The results have direct implications for commercial and operational forecasting systems, where simplicity, cost, reliability, and explainability are often more valuable than marginal accuracy gains. In many cases, lightweight models can deliver comparable decision value while remaining easier to deploy, audit, and maintain.

## Repository Contents

- Data exploration and preprocessing notebooks  
- Model comparison experiments  
- Performance evaluation and efficiency analysis  
- Final conclusions and discussion  

---

## Notes

This project prioritizes methodological clarity and real-world applicability over leaderboard optimization. Results are intended to inform model selection decisions under practical constraints rather than establish state-of-the-art benchmarks.
