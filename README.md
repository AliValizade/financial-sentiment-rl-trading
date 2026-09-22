# Enhancing Sentiment-Based Trading Decisions Using Reinforcement Learning

Master's Thesis — Computer Engineering / Artificial Intelligence and Robotics

## Overview

This repository contains the research materials and implementation for a
Master's thesis investigating reinforcement-learning-based trading decisions
within a financial sentiment analysis framework.

The thesis is based on:

> Burchi, A., & Regni, L. (2026).
> Financial sentiment analysis meets algorithmic trading:
> a performance-based approach.
> Cogent Economics & Finance.
> DOI: 10.1080/23322039.2026.2703376

## Research Direction

The base paper follows:

Tweets
→ Sentiment Models
→ Daily Sentiment
→ Trading Signal
→ Portfolio / Backtest

The thesis investigates an extension:

Tweets
→ Sentiment
→ Sentiment + Market Features
→ RL Agent
→ Trading Policy
→ Portfolio / Backtest

The main research focus is the trading decision layer rather than
stock-price prediction or sentiment classification.

## Base Models

The baseline sentiment models include:

- BERTweet
- RoBERTa
- FinBERT

## Proposed Research

The proposed approach investigates reinforcement learning as a
decision-making layer for sentiment-based algorithmic trading.

The exact RL algorithm, state representation, reward formulation,
and other implementation details remain subject to technical analysis
and experimental validation.

## Baselines

The planned experimental comparison includes:

1. Buy & Hold
2. Original sentiment-based trading rule
3. RL without sentiment
4. RL with sentiment and market/technical features

## Scientific Principles

The project prioritizes:

- Reproducibility
- Temporal evaluation
- Data-leakage prevention
- Explicit execution timing
- Risk-aware financial evaluation
- Separation of baseline reproduction and thesis extension
- Experimental validation before claiming improvement

## Repository Structure

```text
docs/          Research documentation
paper/         Base-paper materials
references/    Bibliography
```

Implementation directories will be added after the proposal and baseline-analysis stages.

## Thesis Status

Current phase:
Proposal Preparation

Completed:
- Base paper selection
- Research gap definition
- Methodology design
- Proposal draft

Next:
- Baseline reproduction
- Dataset verification
- RL environment implementation

---
###### Author: Ali Valizade
Master's Student — Computer Engineering / AI & Robotics
