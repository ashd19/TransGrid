# TransGrid — Project Context

## 1. What We Are Building

An interactive analytics platform for **adaptive electricity-demand and transformer-condition forecasting** in smart grids.

Smart grids continuously generate load and grid-health data. Accurate forecasting supports demand monitoring, asset monitoring, predictive maintenance, and energy planning.

- Forecasts (electricity demand + transformer/grid condition)
- Scenario-based simulation
- Risk alerts
- Decision support for energy planning and predictive maintenance

### Target Users
Grid operators, electricity distributors, maintenance teams, energy planners.

## 2. The Problem / Research Gap

We combine the ideas of two research papers to solve a specific problem:

| Paper | Strength | Limitation |
|---|---|---|
| **2. AutoCon** (Self-Supervised Contrastive Learning for Long-Term Forecasting, ICLR 2024) | Captures **long-term/similarity patterns** — builds contrastive positive/negative pairs between temporally distant windows using **global autocorrelation**, so it learns yearly/seasonal similarities beyond the sliding window. | Uses **one fixed global autocorrelation** pattern. Correlation is static, so it **misses recent demand shifts** (electricity patterns drift/change over time). Autocorrelation mainly captures **linear** relationships. |
| **3. mr-Diff** (Multi-Resolution Diffusion Models for Time Series Forecasting, ICLR 2024) | **Accuracy** — generates forecasts coarse-to-fine via seasonal-trend decomposition (easy-to-hard denoising); very accurate, better than/on par with other diffusion and top forecasting models. | Falls short at **finding similarities** across windows — it reconstructs from noise per-window and does not exploit the similarity/long-term structure between distant, correlated windows. |

### The Gap We Solve
- Electricity patterns **change over time** -> a fixed, static global autocorrelation misses recent demand shifts.
- We want the **accuracy** of the multi-resolution diffusion approach (paper 3) combined with the **long-term similarity-aware representation learning** of AutoCon (paper 2).
- The correlation/similarity signal must be **adaptive** — balancing recent and long-term temporal patterns — instead of one frozen global autocorrelation.

## 3. Proposed Solution

An adaptive forecasting approach built on top of the **AutoCon model** as the starting base (per teacher guidance: start with AutoCon), improved to:

1. Keep AutoCon's strength: learning long-term dependencies between distant, similar windows via contrastive learning.
2. Fix its limitation: make the autocorrelation/similarity **adaptive to recent demand shifts** instead of one global fixed pattern.
3. Borrow the multi-resolution / generative accuracy ideas so the short-term (recent) and long-term (seasonal) components are both forecast accurately.

## 4. Datasets

### ECL Dataset
- Measures: Consumer electricity demand
- Features: Load profiles of 370+ consumers
- Target: Electricity Consumption (kW)
- Interval: Every 15 minutes

### India Energy Atlas
- Provides: Live smart grid operational data
- Features: Electricity Demand, Grid Frequency, Grid Stress Index
- Purpose: Real-time forecasting & predictive monitoring
- Source: API-based live operational data

## 5. Notes / Roadmap
- Teacher-directed path: start with the **AutoCon model**, then adapt/extend it, then build the analytics platform around it.
- `/docs/planning/` contains planning drafts (mind dumps for the app flow).
- Research paper texts live in `/docs/RESEARCH-PAPERS/` (AutoCon, mr-Diff, and a general DL time-series forecasting survey).