# Thesis Decision Log

## Decision 001
Date:
2026-09-21

Topic:
RL Integration Point

Decision:
RL will replace the rule-based trading decision layer,
not the sentiment extraction layer.

Reason:
The base paper already provides sentiment models.
The research contribution should focus on adaptive trading decisions.

Alternatives:
- Training a new sentiment model
- Price prediction approach

Rejected because:
They shift the contribution away from trading decision optimization.

Consequence:
The RL component will be designed as a trading decision layer,
while the sentiment extraction pipeline remains part of the baseline.