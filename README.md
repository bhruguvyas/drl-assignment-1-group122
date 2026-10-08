# DRL Assignment I, Problem IV, Group 122

Paper reviewed: Bouneffouf, D. and Rish, I. (2019), *A Survey on Practical
Applications of Multi-Armed and Contextual Bandits*, arXiv:1904.10040.

BITS Pilani WILP, AIML ZG512 Deep Reinforcement Learning.

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
Run bandit_reproduction.ipynb top to bottom
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
| B | Uniform random (no learning) | 1326.3 |

Two things came out of this. Context-free UCB1 (1328.8) and uniform random (1326.3)
land within one standard error of each other, so on this problem ignoring the context
is no better than guessing. LinUCB, given the same data plus the context vector,
flattens at 37.7. Within Experiment A the gap between algorithms was about a factor
of six, so the choice of setting mattered more than the choice of algorithm.

UCB1 doing worse than epsilon-greedy in Experiment A is not an error. Its bonus
with c = sqrt 2 explores more than a 2000-step horizon rewards, and its guarantee
is asymptotic.

Both environments are synthetic. They test how the algorithms behave. They do not
reproduce any domain result from the survey, because the survey reports none.

## Where each slide's claim comes from

| Slide | Claim | Source |
|---|---|---|
| 2 | What kind of paper this is; the boundary with RL | survey, Introduction and 2.10 |
| 3 | Clinical trial framing, partial feedback | survey, Introduction |
| 4 | UCB, Thompson Sampling, LinUCB | Lai and Robbins 1985; Auer et al. 2002; Agrawal and Goyal 2012; Li et al. 2010 |
| 5 | The four settings | survey, Introduction and 2.10 |
| 6 | Nine application domains | survey 2.1 to 2.9; Bastani and Bayati; Soemers et al. |
| 7 | Six machine-learning tasks; Hyperband | survey 3.1 to 3.6; Li, Jamieson et al.; Laroche and Feraud |
| 8 | Tables 1 and 2 | survey, reproduced. See notes/ |
| 10, 11, 12 | Experiment design, results, reading | this repository |
| 13, 14 | Limitations and future scope | survey 2.10 and 3.7, plus our own reading |

## Files

```
bandit_reproduction.ipynb     experiment notebook
results.txt                   raw output
figures/regret_curves.png     figure used on slide 11
notes/table1_check.md         row-by-row check of Table 1
notes/table2_check.md         cell-by-cell check of Table 2
references.md                 reference list with links
```
