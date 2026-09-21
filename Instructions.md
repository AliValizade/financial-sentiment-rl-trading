# Master's Thesis Project Instructions

## 1. Project Identity

This project is for completing a Master's thesis in Computer Engineering / Artificial Intelligence and Robotics.

The thesis supervisor is Dr. Reza Shamsaee.

The selected base paper is:

**Financial sentiment analysis meets algorithmic trading: a performance-based approach**

Authors: Alberto Burchi and Leonardo Regni
Journal: Cogent Economics & Finance
Year: 2026
DOI: 10.1080/23322039.2026.2703376

Official paper:
https://www.tandfonline.com/doi/full/10.1080/23322039.2026.2703376

Official GitHub repository:
https://github.com/AlbertoBurchi/fsa_x

This paper is the primary scientific and technical reference for the thesis unless the supervisor explicitly changes the direction.

---

# 2. Main Thesis Direction

The thesis focuses on:

* Financial Sentiment Analysis
* Financial social-media/text data
* Transformer-based sentiment models
* Algorithmic trading
* Data-driven trading decisions
* Reinforcement Learning as the preferred development direction

The base paper evaluates:

**Tweets → Sentiment Models → Daily Sentiment → Trading Signal → Portfolio/Backtest**

The intended thesis extension is:

**Tweets → Financial Sentiment → Sentiment + Market Features → RL Agent → Trading Policy → Portfolio/Backtest**

The thesis should NOT be framed merely as stock-price prediction.

The main research focus is the improvement of the **trading decision layer** using Reinforcement Learning.

The exact RL algorithm must not be fixed prematurely. DQN is an initial candidate because the trading action space can naturally be represented as discrete actions such as BUY / HOLD / SELL, but the final algorithm must be selected after technical analysis of the base paper, environment design, state/action space, reward function, and computational constraints.

---

# 3. Core Working Principles

Throughout the project:

1. Prioritize scientific correctness over speed.
2. Prioritize reproducibility.
3. Never invent experimental results.
4. Never claim an improvement before experimentally demonstrating it.
5. Clearly distinguish:

   * facts from the base paper,
   * our interpretation,
   * proposed thesis modifications,
   * experimentally verified results.
6. Do not introduce unnecessary technologies or models.
7. Prefer the smallest technically sound solution that can produce a defensible thesis.
8. Avoid scope creep.
9. Every major technical decision must have a reason.
10. Every experiment must be reproducible.
11. Preserve the original paper's methodology when reproducing its baseline.
12. Do not modify the baseline in a way that makes comparison with the paper impossible.
13. When extending the paper, clearly separate the original method from the proposed method.
14. Always consider data leakage and look-ahead bias in financial experiments.
15. Never use future information when constructing a state, feature, signal, or reward.
16. Financial performance must be evaluated with appropriate risk-aware metrics, not only accuracy or F1.
17. Keep the thesis scope realistic for the available time and computing resources.
18. When uncertain about a scientific or methodological claim, verify it using the original paper or authoritative sources.

---

# 4. Phase 0 — Thesis Definition

Before implementation, establish:

* Final thesis title
* Problem statement
* Motivation
* Research gap
* Main research question
* Sub-research questions
* Objectives
* Contributions
* Scope
* Assumptions
* Dataset
* Base models
* Baseline trading strategy
* Proposed RL approach
* Evaluation methodology

The initial working title is:

**Enhancing Sentiment-Based Trading Decisions Using Reinforcement Learning**

Persian working title:

**بهبود تصمیم‌گیری معاملاتی مبتنی بر تحلیل احساسات مالی با استفاده از یادگیری تقویتی**

The title may be refined after the technical design is finalized.

Do not unnecessarily lock the title to a specific RL algorithm such as DQN until the experimental design is complete.

---

# 5. Phase 1 — Deep Study of the Base Paper

Read the paper completely and systematically.

Extract:

### Problem

* What problem does the paper solve?
* Why is the problem important?
* What gap does it address?

### Data

* Data source
* Dataset structure
* Date range
* Number of stocks
* Number of tweets
* Price data
* Features
* Preprocessing
* Missing values
* Filtering rules

### Sentiment Models

Study:

* BERTweet
* RoBERTa
* FinBERT

Understand:

* model architecture at the required level,
* pretrained model,
* input format,
* sentiment labels,
* output probabilities,
* aggregation method.

### Trading Layer

Understand exactly how sentiment is converted into:

* daily sentiment,
* buy signal,
* sell signal,
* long-only position,
* long-short position.

### Backtesting

Extract:

* execution timing,
* entry/exit rules,
* transaction costs,
* portfolio construction,
* benchmark,
* evaluation period,
* performance metrics.

### Reproducibility

Inspect the official GitHub repository file-by-file.

Do not immediately rewrite the code.

First understand:

* project structure,
* notebooks,
* data files,
* preprocessing,
* sentiment inference,
* portfolio construction,
* backtesting,
* output files,
* dependencies.

Produce a technical map of the repository before modifying it.

---

# 6. Phase 2 — Environment and Repository Reproduction

Create a clean thesis development environment.

Record:

* Python version
* OS
* package versions
* GPU/CPU availability
* CUDA version if applicable
* required libraries

Create a separate thesis repository rather than modifying the original research repository destructively.

Maintain clear separation between:

* original/base implementation,
* reproduced implementation,
* thesis extension.

Create reproducibility documentation.

At this stage the goal is:

**Run → reproduce → understand**

not:

**rewrite → improve**

---

# 7. Phase 3 — Dataset Verification

Verify the exact datasets used by the paper.

Document:

* source
* licensing/access conditions
* date range
* stock universe
* tweet count
* price data
* columns
* missing values
* duplicates
* timestamp format
* timezone
* stock identifiers

Verify that the dataset used in experiments is consistent with the paper.

If the original dataset cannot be reproduced exactly, document:

* what is unavailable,
* what alternative was used,
* why,
* what effect this may have on comparability.

Never silently substitute datasets.

---

# 8. Phase 4 — Baseline Reproduction

Reproduce the original pipeline before introducing RL.

The baseline must include, as far as practically possible:

1. Data preprocessing
2. Sentiment extraction
3. Daily sentiment aggregation
4. Trading signal generation
5. Portfolio construction
6. Backtesting
7. Performance evaluation

Reproduce the three sentiment models:

* BERTweet
* RoBERTa
* FinBERT

The main goal is to establish a reliable baseline.

Compare reproduced results with the paper.

Create a table:

| Component    | Paper | Reproduction | Difference |
| ------------ | ----- | ------------ | ---------- |
| Dataset      |       |              |            |
| BERTweet     |       |              |            |
| RoBERTa      |       |              |            |
| FinBERT      |       |              |            |
| Long-only    |       |              |            |
| Long-short   |       |              |            |
| Sharpe       |       |              |            |
| Max Drawdown |       |              |            |

Differences must be investigated rather than hidden.

---

# 9. Phase 5 — Reproduce the Original Trading Strategy

Implement the paper's rule-based strategy independently enough to serve as a baseline.

This is critical.

The thesis must be able to answer:

**Does RL improve the trading decision compared with the original decision mechanism?**

Therefore the original trading strategy becomes one of the principal baselines.

At minimum compare:

1. Buy & Hold
2. Original sentiment-based rule
3. RL without sentiment
4. RL with sentiment

The fourth configuration is the primary proposed approach.

---

# 10. Phase 6 — Research Gap and Thesis Contribution

After baseline reproduction, formally define the gap.

The base paper demonstrates that:

**sentiment → predefined trading rules → portfolio performance**

The thesis investigates:

**sentiment + market information → learned trading policy → portfolio performance**

The proposed contribution should therefore be formulated as an extension of the decision-making layer rather than claiming to invent financial sentiment analysis or RL trading.

A safe contribution statement is:

> The thesis extends the sentiment-based algorithmic trading framework of the selected base paper by replacing the predefined trading decision mechanism with a reinforcement-learning-based policy and evaluating whether the learned policy can improve risk-adjusted trading performance under controlled experimental conditions.

Do not claim:

* "the first study"
* "the first use of RL for sentiment trading"
* "a completely novel RL trading system"

unless a systematic literature review actually establishes such claims.

---

# 11. Phase 7 — RL Problem Formulation

Formulate trading as a Markov Decision Process.

Define:

### State

Possible state components:

* sentiment probabilities
* aggregated daily sentiment
* sentiment momentum/change
* price return
* volume
* volatility
* technical indicators
* current position
* cash/portfolio information

Only features available at decision time may be included.

### Action

Initial candidate:

* BUY
* HOLD
* SELL

Alternative action spaces may be considered only if justified.

### Reward

Reward should represent economic performance.

Possible formulation:

**Reward = portfolio return − transaction cost − risk penalty**

Potential risk terms:

* volatility
* drawdown
* excessive turnover

The reward function must be justified scientifically and experimentally.

### Environment

Define:

* observation/state
* action
* transition
* reward
* episode
* initial capital
* transaction costs
* position constraints
* execution timing.

---

# 12. Phase 8 — RL Algorithm Selection

Initially investigate:

### DQN

Because it naturally supports discrete actions.

Then evaluate whether another algorithm is more appropriate.

Possible alternatives:

* Double DQN
* Dueling DQN
* PPO

Do not implement many RL algorithms merely for quantity.

The default strategy is:

**one strong primary RL method + one optional secondary method if time permits.**

The selected algorithm must be justified by:

* action-space structure,
* state representation,
* training stability,
* computational feasibility,
* literature support,
* reproducibility.

---

# 13. Phase 9 — Experimental Design

The experiments should isolate the contribution of sentiment.

Minimum experimental matrix:

### Experiment A

Buy & Hold

### Experiment B

Original paper's sentiment-based rule

### Experiment C

RL + market/technical features without sentiment

### Experiment D

RL + sentiment + market/technical features

Experiment D is the primary proposed model.

If feasible:

### Experiment E

RL + FinBERT sentiment

### Experiment F

RL + BERTweet sentiment

### Experiment G

RL + RoBERTa sentiment

These additional experiments should only be performed if they materially contribute to the thesis.

---

# 14. Phase 10 — Temporal Evaluation

Financial experiments must use time-aware evaluation.

Avoid random train/test splits for sequential market prediction/trading.

Prefer:

* chronological train/validation/test split,
* walk-forward evaluation,
* rolling-window evaluation where practical.

Never allow information from the future test period to influence training, preprocessing, feature scaling, model selection, or hyperparameter tuning.

Document every split explicitly.

---

# 15. Phase 11 — Avoiding Data Leakage

Before every experiment, explicitly inspect for:

* look-ahead bias
* future price leakage
* timestamp leakage
* sentiment aggregation leakage
* normalization leakage
* train/test contamination
* duplicate tweets
* future market information
* same-day execution assumptions

If sentiment at day t is used to make a trade, define exactly when that information becomes available and execute the trade no earlier than justified.

The base paper already uses next-day execution to reduce look-ahead bias. Preserve this principle.

---

# 16. Phase 12 — Evaluation Metrics

Evaluate both machine-learning and financial performance.

### Sentiment/model metrics

Where applicable:

* Accuracy
* Precision
* Recall
* F1
* Confusion Matrix

### Trading metrics

At minimum:

* Cumulative Return
* Annualized Return
* Volatility
* Sharpe Ratio
* Sortino Ratio
* Maximum Drawdown
* Calmar Ratio
* Number of Trades
* Turnover

Where appropriate:

* transaction costs
* slippage
* exposure
* win rate

Do not treat cumulative return alone as sufficient evidence.

Risk-adjusted performance is particularly important.

---

# 17. Phase 13 — Statistical and Robustness Analysis

Where feasible:

* compare multiple stocks,
* compare multiple periods,
* compare multiple market conditions,
* test different transaction costs,
* test sensitivity to reward parameters,
* test sensitivity to RL hyperparameters,
* evaluate robustness across seeds.

Use statistical tests only when appropriate and justified.

Do not overstate significance from a small sample.

---

# 18. Phase 14 — Ablation Studies

The thesis should attempt to answer:

**What actually causes the improvement?**

Possible ablations:

* RL without sentiment
* RL with sentiment
* sentiment only
* technical features only
* sentiment + technical features
* different sentiment models
* different reward formulations

Ablation studies are preferable to adding many unrelated models.

---

# 19. Phase 15 — Results Analysis

For every major experiment, report:

1. Configuration
2. Dataset
3. Time period
4. Features
5. Model
6. Hyperparameters
7. Transaction costs
8. Evaluation metrics
9. Results
10. Interpretation
11. Limitations

Never interpret a result beyond what the experiment supports.

Example:

Do not write:

> RL is superior.

Prefer:

> Under the specified experimental conditions, the RL-based strategy achieved higher/lower X compared with the baseline.

---

# 20. Phase 16 — Thesis Writing

The thesis should gradually be written during the research rather than postponed until the end.

Recommended structure:

## Chapter 1 — Introduction

* Background
* Problem statement
* Motivation
* Research gap
* Objectives
* Research questions
* Contributions
* Scope
* Thesis structure

## Chapter 2 — Literature Review

Cover:

* Financial Sentiment Analysis
* NLP in finance
* BERT/transformers
* BERTweet
* RoBERTa
* FinBERT
* Sentiment-based trading
* Algorithmic trading
* Reinforcement Learning
* RL for financial trading
* Risk-aware trading
* Relevant recent studies

## Chapter 3 — Methodology

Describe:

* Dataset
* Preprocessing
* Sentiment models
* Feature engineering
* Baseline strategy
* RL formulation
* State
* Action
* Reward
* Environment
* Training
* Validation
* Testing
* Evaluation metrics

## Chapter 4 — Experiments and Results

Include:

* Baseline reproduction
* Experimental setup
* RL experiments
* Ablation studies
* Performance comparison
* Statistical/robustness analysis

## Chapter 5 — Discussion

Discuss:

* Findings
* Interpretation
* Comparison with prior work
* Practical implications
* Limitations
* Threats to validity

## Chapter 6 — Conclusion and Future Work

Include:

* Summary
* Contributions
* Main findings
* Limitations
* Future research

---

# 21. Phase 17 — Proposal

The proposal should be written after the base paper has been deeply understood but before excessive implementation.

The proposal should contain:

* Title
* Introduction
* Problem statement
* Importance
* Research gap
* Objectives
* Research questions
* Hypotheses where appropriate
* Methodology
* Dataset
* Models
* Proposed RL extension
* Evaluation metrics
* Expected contribution
* Preliminary references
* Timeline

Do not fabricate expected results.

Use phrases such as:

* "will be investigated"
* "will be evaluated"
* "the study will examine whether..."

instead of claiming improvement before experimentation.

---

# 22. Phase 18 — Implementation Quality

The thesis code should be structured as a research project rather than a collection of notebooks.

Prefer modules such as:

* data/
* preprocessing/
* sentiment/
* features/
* trading/
* environments/
* rl/
* evaluation/
* experiments/
* configs/
* notebooks/
* tests/

Keep:

* configuration separate from code,
* experiment parameters reproducible,
* random seeds recorded,
* outputs versioned,
* results stored systematically.

Every important experiment should be reproducible from configuration.

---

# 23. Phase 19 — Git and Research Tracking

Use Git throughout the project.

Maintain meaningful commits.

Suggested milestones:

* thesis initialization
* base paper analysis
* dataset preparation
* baseline reproduction
* sentiment pipeline
* rule-based trading baseline
* RL environment
* first RL experiment
* final experiments
* thesis results
* final thesis

Do not commit:

* private credentials
* huge raw datasets unless permitted
* API keys
* personal information
* unnecessary generated files.

---

# 24. Phase 20 — Final Validation

Before writing the final conclusion, perform a complete audit.

### Scientific audit

* Are research questions answered?
* Is the research gap addressed?
* Is the contribution clearly defined?
* Are claims supported by experiments?

### Data audit

* Is the dataset documented?
* Is there leakage?
* Are temporal splits correct?
* Are timestamps handled correctly?

### Code audit

* Can the main experiments be reproduced?
* Are dependencies documented?
* Are configurations recorded?
* Are seeds recorded?

### Results audit

* Are all tables reproducible?
* Are metrics calculated correctly?
* Are baselines included?
* Are negative results reported?

### Thesis audit

* References complete?
* Figures numbered?
* Tables numbered?
* Acronyms defined?
* Equations consistent?
* Persian/English terminology consistent?
* Formatting according to university requirements?

---

# 25. Phase 21 — Pre-Defense Preparation

Prepare:

1. Final thesis
2. Presentation
3. Executive summary
4. Research contribution summary
5. Methodology diagram
6. System architecture diagram
7. Experimental pipeline diagram
8. Dataset description
9. Baseline comparison
10. Main results
11. Ablation results
12. Limitations
13. Future work

Prepare answers to likely questions:

* Why this problem?
* Why sentiment analysis?
* Why social media?
* Why these models?
* Why FinBERT/BERTweet/RoBERTa?
* Why reinforcement learning?
* Why this RL algorithm?
* Why this state?
* Why this action space?
* Why this reward?
* How was leakage prevented?
* Why these metrics?
* Why not ordinary supervised learning?
* Why not another RL method?
* What is the actual contribution?
* What are the limitations?
* Can the experiment be reproduced?

---

# 26. Phase 22 — Final Defense

The defense preparation should focus on explaining the thesis as a logical chain:

**Problem → Gap → Base Paper → Limitation/Opportunity → Proposed Extension → Method → Experiments → Results → Contribution → Limitations**

The presentation must not become a generic explanation of AI, NLP, or reinforcement learning.

The majority of the presentation should demonstrate:

* what was done,
* why it was done,
* how it was evaluated,
* what was found.

---

# 27. Final Deliverables

The project is considered complete only when all of the following exist:

* Approved thesis proposal
* Literature review
* Reproducible dataset pipeline
* Reproduced baseline
* Original paper's trading strategy implementation
* RL trading environment
* Proposed RL model
* Experimental results
* Ablation/robustness analysis
* Final thesis
* Source code
* Reproducibility documentation
* Final presentation
* Defense preparation

---

# 28. How the Assistant Should Work With the Student

For every thesis task:

1. First identify the exact current phase.
2. Do not jump ahead unnecessarily.
3. Use the selected paper and official repository as primary technical references.
4. Search the web when current or paper-specific verification is necessary.
5. Prefer original scientific sources over secondary summaries.
6. When discussing the base paper, distinguish its actual methodology from proposed thesis modifications.
7. When writing scientific text, avoid unsupported claims.
8. When proposing experiments, explain what research question each experiment answers.
9. When reviewing code, prioritize correctness, reproducibility, leakage prevention, and maintainability.
10. Challenge weak assumptions instead of simply agreeing.
11. If a proposed idea increases scope without clear thesis value, explicitly point this out.
12. Prefer one well-designed experiment over many superficial experiments.
13. Never fabricate experimental numbers, citations, datasets, or results.
14. Keep a running record of important decisions.
15. When a major decision is reached, state:

* decision,
* reason,
* alternatives rejected,
* consequence for the next phase.

---

# 29. Current Project Status

Current status:

**Base paper: APPROVED AND SELECTED**

Selected paper:

**Financial sentiment analysis meets algorithmic trading: a performance-based approach**

Current intended development:

**Sentiment-based algorithmic trading + Reinforcement Learning**

Supervisor status:

* Candidate paper approved by Dr. Reza Shamsaee.
* Supervisor considers this paper clearer and more promising than the previously considered paper.
* Data and code accessibility are important positive factors.

Immediate next tasks:

1. Deeply analyze the selected paper.
2. Inspect the official GitHub repository.
3. Inspect and verify the dataset.
4. Map the complete baseline pipeline.
5. Identify exactly where the RL extension should be introduced.
6. Finalize the research questions.
7. Prepare the thesis proposal.
8. Only then begin the full implementation.

Do not search for another base paper unless the supervisor explicitly requests it or a serious reproducibility/scientific problem is discovered.

---

# 30. Golden Rule

The objective is not simply to "add RL" to an existing paper.

The objective is to build a scientifically defensible thesis in which:

**Financial Sentiment Analysis → Information Representation → Trading Decision → Reinforcement Learning → Risk-Aware Evaluation**

forms one coherent research problem.

Every component must have a clear scientific reason for being there.
