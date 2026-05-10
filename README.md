# 📉 Firm-Level Supply Chain Elasticity Analysis

## Tungsten Supply Chain Resilience & Economic Shock Propagation

This module performs a high-granularity Elasticity Analysis on the synthetic firm-level trade network. It simulates supply shocks to individual upstream firms and measures the resulting economic impact on Italian industrial importers.

---

# 🚀 Key Improvements(Based on Francesco's Feedback) and Core Idea of the Code 

Following the latest methodological review by Francesco, the following core enhancements were implemented to ensure the model's high reliability:

## 💰 Shift to Economic Value (USD)

- The entire analysis has been transitioned from physical mass (KG/Tonnes) to strictly economic value (Raw USD).
- This ensures alignment with global trade financial monitoring and removes distortions caused by weight-based calculations.

---

## ⚖️ Automated Value-Balance Check

A new validation script verifies that the sum of firm-to-firm flows ($A \rightarrow B$) matches exactly with the official COMTRADE country-level statistics.

This "Mass-Balance" equivalent for value ensures the synthetic network is a perfect statistical mirror of empirical reality.

---

## 📐 Explicit Pareto-HHI Logic

The methodology for firm share generation is now clearly defined.

Shares follow a Pareto distribution with an alpha parameter calibrated directly from the observed Herfindahl-Hirschman Index (HHI).

This includes the integration of Anchor Companies (real-world giants) to provide a realistic "heavy-tail" to the market distribution.

---

# 🔬 Methodology: The Elasticity Engine

The analysis utilizes a Fixed-Point Iteration algorithm to propagate supply shocks through the dependency matrix ($P$).

## Dependency Matrix ($P$)

Calculated as:

$$
P_{ij} = \frac{W_{ij}}{\sum_i W_{ij}}
$$

representing the share of firm $j$'s imports provided by firm $i$.

---

## 1% Shock Simulation

We apply a microscopic (1%) supply cut to a specific upstream firm and iterate until the system reaches a new equilibrium.

---

## Elasticity Calculation

The final result represents the percentage loss in Italian import value per 1% shock applied to the supplier.

---

# 📊 Visualizing Risks

The script generates a Vertical Elasticity Bar Chart that highlights the most critical suppliers for the Italian market.

- **Red Bars ($E \ge 1$):** High-risk suppliers where a shock is amplified through the chain.
- **Blue Bars ($E < 1$):** Suppliers where shocks are attenuated before reaching Italy.

---

# 📂 File Structure

## `firm_nodes.json`

Contains firm metadata, Pareto shares, and "Anchor" flags.

## `firm_edges.json`

Contains the bilateral USD trade flows between firms.

## `firm_level_analysis.ipynb`

The primary analysis and simulation engine.
