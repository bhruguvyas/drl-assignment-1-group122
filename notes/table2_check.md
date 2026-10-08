# Table 2 check

Bandits inside machine learning. Checked by Putta Madhu Rani against the published
table in arXiv:1904.10040.

| Task | MAB | NS-MAB | CMAB | NS-CMAB | Verified |
|---|:--:|:--:|:--:|:--:|:--:|
| Algorithm selection | | x | | | ✓ |
| Parameter optimisation | x | | | | ✓ |
| Feature selection | x | x | | | ✓ |
| Active learning | x | x | | | ✓ |
| Clustering | | x | | | ✓ |
| Reinforcement learning | x | x | x | | ✓ |

All six rows match the published Table 2.

## Notes

1. Reinforcement learning is the only row with a mark in the contextual column.
2. Section 3.7 lists contextual bandits for feature selection and hyperparameter
   optimisation as directions nobody has taken, which matches the empty cells.
3. Most of these tasks are treated as non-stationary but context-free. Drift is
   assumed; the side information that would explain the drift is not used.

Checked on 9 October 2026 by Putta Madhu Rani (2025AG05144).
