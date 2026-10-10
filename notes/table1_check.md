# Table 1 check

Applications outside machine learning. Checked by Adithya R against the published
table in arXiv:1904.10040.

| Domain | MAB | NS-MAB | CMAB | NS-CMAB | Verified |
|---|:--:|:--:|:--:|:--:|:--:|
| Healthcare | x | | x | | ✓ |
| Finance | x | | | | ✓ |
| Dynamic pricing | x | | | | ✓ |
| Recommender systems | x | x | x | x | ✓ |
| Influence maximisation | x | | | | ✓ |
| Dialogue systems | | | x | | ✓ |
| Anomaly detection | | | x | | ✓ |
| Telecommunication | x | | | | ✓ |

All eight rows match the published Table 1.

## Notes

1. Information retrieval is covered in section 2.6 but has no row in the table.
2. Recommender systems is the only domain appearing in all four settings.
3. Healthcare is contextual and never non-stationary. Section 2.10 explains this:
   no change in the patient's state is assumed while the treatment decision is made.

