# Section 1 check

Problem formulation and algorithms. Checked by Keerthana R against Section 1 of
arXiv:1904.10040 and the original sources it cites. Covers slides 4 and 5.

## Algorithm citations on slide 5

| Algorithm | Deck credits | Verified |
|---|---|:--:|
| Epoch-Greedy | Langford and Zhang, 2008 | ✓ |
| LinUCB | Li et al., 2010 | ✓ |
| Contextual Thompson Sampling | Agrawal and Goyal, 2013 | ✓ |
| Neural Bandit | Allesiardo et al., 2014 | ✓ |

## Citations on slide 4

| Claim | Deck credits | Verified |
|---|---|:--:|
| Thompson Sampling regret analysis | Agrawal and Goyal, 2012 | ✓ |
| LinUCB, introduced for news recommendation | Li et al., 2010 | ✓ |
| UCB finite-time analysis | Auer, Cesa-Bianchi and Fischer, 2002 | ✓ |
| Asymptotically efficient allocation rules | Lai and Robbins, 1985 | ✓ |

## Formulas on slide 4

| Item | As shown on the slide | Verified |
|---|---|:--:|
| Cumulative regret | Rn = n·Q* minus E[ sum of Xt ] | ✓ |
| Classical UCB | UCBk(t) = Qk(t) + sqrt( 2·log t / Tk(t) ) | ✓ |
| LinUCB | pk(t) = theta_k^T xt + alpha · sqrt( xt^T Ak^-1 xt ) | ✓ |

## The linearity caveat on slide 5

The survey states in Section 1 that for the general case a linear dependency is
typically assumed between the expected reward of an action and its context. Our
slide reports this and notes the paper does not return to how often it holds.
Confirmed against the text.

## Notes

1. Both solution families in Section 1 predate context. Neither UCB nor Thompson
   Sampling takes side information into account, which is what motivates the
   contextual version.
2. A bandit has no state transition caused by the action. Section 2.10 uses this to
   explain why healthcare is treated as contextual and never non-stationary.
3. The clinical trial running example maps directly onto context, action and reward:
   the patient record, the treatment given, and the outcome observed.

All citations, formulas and the caveat match the sources.

