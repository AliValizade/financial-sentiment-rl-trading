# Research Gap

Previous studies have investigated the integration of financial sentiment information and reinforcement learning in various algorithmic trading frameworks. Therefore, the research gap of this thesis is not based on the absence of sentiment-aware reinforcement learning approaches.

The selected base paper provides a structured and reproducible framework for extracting financial sentiment from Twitter data and translating aggregated sentiment information into trading signals. However, its trading decision layer relies on predefined sentiment-to-action rules.

This thesis investigates a specific extension of the base framework in which the fixed decision layer is replaced by a reinforcement learning policy. The proposed framework incorporates sentiment features together with market information and selected technical features into the agent's decision state. The agent then learns a trading policy rather than relying exclusively on a predefined mapping between sentiment and trading actions.

The proposed extension will be evaluated through controlled baselines, including Buy & Hold, the original sentiment-based trading rule, and reinforcement learning without sentiment information. Evaluation will use chronological data splits and leakage-aware experimental procedures, with financial return, risk, risk-adjusted performance, and trading-behavior metrics.

The central research gap addressed by this thesis is therefore the **empirical evaluation of a learned trading decision layer as a controlled extension of the selected sentiment-based trading framework**, particularly in terms of whether combining sentiment information with market and technical information provides measurable value for reinforcement-learning-based trading decisions.
