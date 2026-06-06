# Model Results

Original results as reported. `set.seed(42)` used throughout; minor variation across R versions is expected.

## Test MSE — 70/30 Train-Test Split (n = 1,030)

| Method | Configuration | Trees | Test MSE |
|--------|--------------|-------|----------|
| Bagging | m = 8 (all features) | 900 | 27.57 |
| Random Forests | m = 5 | 150 | 27.78 |
| Gradient Boosting | λ = 0.01, d = 10 | 5,000 | **17.14** |

Gradient Boosting achieves a **38% reduction** in MSE relative to the Bagging baseline (10.43 unit improvement on a 2.3–82.6 MPa target range).

## Variable Importance Summary

Consistent ranking across all three methods:

| Rank | Feature | Notes |
|------|---------|-------|
| 1 | Age | Removing Age increases Bagging MSE by > 200% |
| 2 | Cement | Substantially more important than third-ranked |
| 3–4 | Blast Furnace Slag, Superplasticizer | Secondary tier |
| 5 | Water | Mid-tier contributor |
| 6–7 | Fine Aggregate, Coarse Aggregate | Lower importance |
| 8 | Fly Ash | Least important |

## Interaction Depth Effect (Boosting, λ = 0.01)

| Interaction Depth (d) | Test MSE |
|-----------------------|----------|
| 1 (stumps) | 29.02 |
| 5 | 18.53 |
| 10 | **17.14** |

Progressive improvement confirms that compressive strength involves genuine higher-order ingredient interactions, not just additive effects.
