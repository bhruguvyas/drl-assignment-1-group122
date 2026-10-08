# DRL Assignment I, Problem IV, Group 122

Paper reviewed: Bouneffouf, D. and Rish, I. (2019), *A Survey on Practical
Applications of Multi-Armed and Contextual Bandits*, arXiv:1904.10040.

BITS Pilani, AIML ZG512 Deep Reinforcement Learning.

| Contributor | BITS ID | Worked on |
|---|---|---|
| Keerthana R | 2025AG05043 | Problem formulation, the algorithms, the four-setting taxonomy |
| Adithya R | 2025AG05182 | Nine application domains, Table 1 |
| Putta Madhu Rani | 2025AG05144 | Six machine-learning tasks, Table 2, slide assembly |
| Vyas Bhrugu | 2025AG05883 | Experiments and code, limitations, references |

## Why there is code in a paper review

The survey reports no experiments. To check the algorithms it describes, we
implemented them and measured regret ourselves.

```
Open bandit_reproduction.ipynb and run all cells top to bottom
```

Writes `figures/regret_curves.png` and `results.txt`. Seed is 122, fixed per run,
so the output is identical every time.

### Experiment A, stochastic bandit

10 Bernoulli arms with true means drawn from U(0,1). Policies: epsilon-greedy
(eps = 0.1), UCB1 (c = sqrt 2), Thompson Sampling (Beta(1,1) prior).
2000 steps, averaged over 500 runs.

### Experiment B, contextual bandit

5-dimensional context x, reward = theta_a . x + N(0, 0.1). LinUCB (alpha = 0.6)
against context-free UCB1 and a uniform-random baseline on the same problem.
2000 steps, averaged over 120 runs.

### Numbers we got

| Experiment | Policy | Cumulative regret at 2000 steps |
|---|---|---|
| A | Thompson Sampling | 31.6 |
| A | epsilon-greedy | 120.3 |
| A | UCB1 | 184.0 |
| B | LinUCB, context used | 37.7 |
| B | UCB1, context ignored | 1328.8 |
| B | Uniform random, no learning | 1326.3 |

The clearest result is in Experiment B. Context-free UCB1 (1328.8) and uniform
random (1326.3) land within one standard error of each other, so on this problem
ignoring the context is no better than guessing. LinUCB, given the same data plus
the context vector, flattens at 37.7. Within Experiment A the gap between
algorithms was about a factor of six, so the choice of setting mattered more than
the choice of algorithm.

UCB1 doing worse than epsilon-greedy in Experiment A is not an error. Its bonus
with c = sqrt 2 explores more than a 2000-step horizon rewards, and its guarantee
is asymptotic.

Both environments are synthetic. They test how the algorithms behave. They do not
reproduce any domain result from the survey, because the survey reports none.

## Where each slide's claim comes from

| Slide | Claim | Source |
|---|---|---|
| 2 | Motivation: partial feedback, the cost of exploration | survey, Introduction |
| 3 | Objective and the two directions surveyed | survey, Introduction |
| 4 | The bandit problem; UCB, Thompson Sampling, LinUCB | Lai and Robbins 1985; Auer et al. 2002; Agrawal and Goyal 2012; Li et al. 2010 |
| 5 | The four settings; the boundary with full RL | survey, Introduction and 2.10 |
| 6 | Nine application domains | survey 2.1 to 2.9; Bastani and Bayati; Soemers et al. |
| 7 | Six machine-learning tasks; Hyperband | survey 3.1 to 3.6; Li, Jamieson et al.; Laroche and Feraud |
| 8 | Tables 1 and 2, reproduced | survey, Tables 1 and 2. See `notes/` |
| 9, 10, 11 | Our experiment design, results and reading | this repository |
| 12 | Significance for reinforcement learning | survey 2.10 and 3 |
| 13, 14 | Limitations, future scope and conclusion | survey 2.10 and 3.7, plus our own reading |
| 16 | Proof of work, references and links | this repository |

The figure on slide 10 is `figures/regret_curves.png`, produced by the notebook.

## Files

```
bandit_reproduction.ipynb     experiment notebook, outputs included
results.txt                   raw numeric output
figures/regret_curves.png     figure used on slide 10
notes/table1_check.md         row-by-row check of Table 1
notes/table2_check.md         cell-by-cell check of Table 2
references.md                 reference list with links
```
