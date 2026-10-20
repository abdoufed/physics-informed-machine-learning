# Physics-informed ML for quantum dynamics

PINN for a driven two-level (Rabi) system, benchmarked against the closed-form solution.

**`rabi-pinn-ablation-and-inverse.ipynb`**
- Complex-valued ansatz trained on the Schrödinger residual (no solution data),
  with norm-preservation and boundary losses.
- **Sampling ablation:** identical 434-parameter network, 10,000 epochs, uniform vs.
  adaptive residual collocation sampling. Uniform loses amplitude and drifts in phase;
  adaptive reproduces the exact trace over three Rabi periods.
- **Inverse problem:** a second network recovers the Hamiltonian parameters from a
  measured ⟨σz⟩ trace alone. Magnitudes recovered to 0.054 (δ) and 0.021 (Ω).
- **Identifiability:** the recovered signs are inverted, and ⟨σz⟩ is exactly invariant
  under independent sign changes of δ and Ω — so the sign is not identifiable from this
  measurement. A naive absolute error reports 0.65 / 1.98; on magnitudes it is
  0.054 / 0.021. The fit is correct; the naive metric is not.
