# Project Guidelines

## 1. Project Identity

**Project:** Master's Thesis in Computer Engineering / Artificial Intelligence and Robotics

**Working Title:**
Enhancing Sentiment-Based Trading Decisions Using Reinforcement Learning

**Persian Title:**
بهبود تصمیم‌گیری معاملاتی مبتنی بر تحلیل احساسات مالی با استفاده از یادگیری تقویتی

**Supervisor:**
Dr. Reza Shamsaee

---

## 2. Research Direction

The thesis focuses on the intersection of:

* Financial Sentiment Analysis
* Algorithmic Trading
* Reinforcement Learning

The primary research focus is the **trading decision layer**, rather than stock-price prediction or sentiment classification.

---

## 3. Selected Base Paper

The thesis is based on:

> Burchi, A., & Regni, L. (2026).
> Financial sentiment analysis meets algorithmic trading: a performance-based approach.
> Cogent Economics & Finance.
> DOI: 10.1080/23322039.2026.2703376

Official paper:

https://doi.org/10.1080/23322039.2026.2703376

Official repository:

https://github.com/AlbertoBurchi/fsa_x

The selected paper is the fixed base paper for this thesis unless a serious scientific or reproducibility problem is identified or the supervisor requests a change.

---

## 4. Base Paper Concept

The base paper follows the general pipeline:

```text
Tweets
   ↓
Sentiment Models
   ↓
Daily Sentiment
   ↓
Trading Signal
   ↓
Portfolio / Backtest
```

The sentiment models investigated in the base paper include:

* BERTweet
* RoBERTa
* FinBERT

The thesis investigates an extension in which the trading decision layer is learned using reinforcement learning:

```text
Tweets
   ↓
Sentiment Models
   ↓
Daily Sentiment
   +
Market / Technical Features
   ↓
RL State
   ↓
RL Agent
   ↓
Trading Policy
   ↓
Portfolio / Backtest
```

---

## 5. Core Research Principle

The thesis should clearly separate:

1. **Baseline reproduction**
2. **Proposed methodological extension**
3. **Experimental comparison**

The original sentiment-analysis and rule-based trading framework should be reproduced as faithfully as practical before introducing the proposed RL-based decision layer.

---

## 6. Proposed Research Direction

The proposed extension investigates whether a reinforcement-learning-based decision layer can learn a trading policy from a combination of:

* Financial sentiment information
* Market information
* Technical information
* Portfolio state where justified

The RL algorithm, state representation, reward formulation, and other implementation details are not considered final until they have been technically analyzed and experimentally justified.

---

## 7. Candidate RL Formulation

The trading problem will initially be formulated as a Markov Decision Process:

$$
M = (S, A, P, R, \gamma)
$$

where:

* \(S\) represents the trading state
* \(A\) represents the available trading actions
* \(P\) represents state transitions
* \(R\) represents the reward function
* \(\gamma\) represents the discount factor

The initial action design is a discrete action space corresponding to:

```text
-1 → Short
 0 → Flat
+1 → Long
```

The final action semantics remain subject to the environment design and experimental analysis.

---

## 8. Candidate State Representation

The candidate state representation may combine:

```text
Sentiment Features
+
Market Features
+
Technical Features
+
Current Position
```

Possible sentiment information includes aggregated sentiment probabilities and, where justified, tweet-volume information.

Possible market and technical information includes recent returns, volatility, volume-related features, and selected technical indicators.

The final feature set must be determined without introducing future information or look-ahead bias.

---

## 9. Candidate Reward

The initial reward candidate is based on economic portfolio performance after transaction costs.

A risk-aware reward formulation may be investigated later if scientifically justified.

Reward design must not be finalized before the trading environment and evaluation protocol are defined.

---

## 10. Planned Baselines

The minimum planned comparison is:

1. Buy & Hold
2. Original sentiment-based trading rule
3. RL without sentiment
4. RL with sentiment and market / technical features

The fourth configuration is the primary proposed configuration.

The experiments must distinguish the contribution of reinforcement learning from the contribution of sentiment information.

---

## 11. Financial Evaluation

The trading strategies should be evaluated using multiple financial metrics rather than return alone.

Planned metrics include:

* Cumulative Return
* Annualized Return
* Volatility
* Sharpe Ratio
* Sortino Ratio
* Maximum Drawdown
* Calmar Ratio
* Number of Trades
* Turnover

Transaction costs and, where appropriate, slippage should be incorporated into the evaluation.

---

## 12. Temporal Evaluation and Leakage Prevention

Financial experiments must use time-aware evaluation.

The planned approach is:

```text
Chronological Training
        ↓
Validation
        ↓
Test
```

Walk-forward or rolling evaluation may be considered where practical.

Future information must not be used in:

* preprocessing
* normalization
* feature engineering
* model selection
* hyperparameter tuning
* training
* trading decisions

Execution timing must be explicitly defined.

The baseline and proposed strategy should not use information that would not have been available at the time of the simulated decision.

---

## 13. Reproducibility Principles

The project should record, where applicable:

* Data sources
* Dataset versions or retrieval information
* Software and package versions
* Random seeds
* Model configurations
* Hyperparameters
* Transaction-cost assumptions
* Experimental configurations
* Evaluation procedures

Raw or restricted datasets should not be committed to the repository unless their licensing and redistribution conditions explicitly permit it.

---

## 14. Scientific Integrity

The project must follow these principles:

* Do not fabricate results, datasets, citations, or experimental findings.
* Do not claim improvement before experiments demonstrate it.
* Distinguish documented facts from interpretation and proposed methodology.
* Report negative or inconclusive results when they occur.
* Explicitly document methodological deviations from the base paper.
* Investigate discrepancies between reproduced and published results.
* Treat data leakage and look-ahead bias as critical threats to validity.
* Prefer a technically justified and reproducible solution over unnecessary methodological complexity.

---

## 15. Scope Control

The thesis should prioritize:

```text
One strong research contribution
        >
Many superficial model comparisons
```

The project should avoid unnecessary expansion into:

* stock-price prediction as the primary task
* development of new sentiment models without research justification
* excessive RL algorithm comparisons
* unrelated financial datasets
* unnecessary feature engineering
* overly complex portfolio optimization

The main contribution should remain the learned trading decision layer.

---

## 16. Research Workflow

The planned research workflow is:

```text
1. Paper Analysis
        ↓
2. GitHub Reverse Engineering
        ↓
3. Dataset Verification
        ↓
4. Baseline Reproduction
        ↓
5. Research Gap Refinement
        ↓
6. RL Formulation
        ↓
7. Environment Design
        ↓
8. Implementation
        ↓
9. Experiments
        ↓
10. Analysis
        ↓
11. Thesis Writing
        ↓
12. Defense Preparation
```

The proposal phase intentionally uses a smaller scope than the full implementation phase.

---

## 17. Proposal-Phase Principle

Before proposal approval, the project should establish:

* the research problem
* the research gap
* the objectives
* the research questions
* the proposed methodology
* the experimental framework
* the expected contribution

Full repository reverse engineering, complete baseline reproduction, final RL algorithm selection, and detailed implementation decisions will be performed after proposal approval.

---

## 18. Decision Management

Major methodological decisions should be recorded in:

```text
docs/decision_log.md
```

Each decision should document, where applicable:

* Decision
* Reason
* Alternatives considered
* Consequences
* Status

Decisions that have not yet been experimentally validated should remain explicitly marked as provisional.

---

## 19. Current Project Phase

The current project phase is:

**Proposal Preparation**

Current priority:

```text
Methodology
→ Proposal
→ Proposal Review / Defense
```

After proposal approval:

```text
Reverse Engineering
→ Dataset Verification
→ Baseline Reproduction
→ RL Design
→ Implementation
→ Experiments
```

---

## 20. Final Principle

The objective of this project is to produce a scientifically defensible, reproducible, and experimentally validated Master's thesis.

The thesis should demonstrate not merely that an RL trading system can be implemented, but that its design, assumptions, evaluation, and conclusions are supported by appropriate experimental evidence.
