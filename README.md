# W5-Credit-Scoring-Business-Understanding
## Credit Scoring Business Understanding

### 1. Influence of Basel II Accord on Model Requirements
The Basel II Accord emphasizes the need for robust, interpretable, and risk-sensitive credit models. Financial institutions must estimate risk parameters such as **Probability of Default (PD)**, **Loss Given Default (LGD)**, and **Exposure at Default (EAD)**. To comply, models must:
- Be **transparent** and explainable for audits and regulatory review.
- Produce **quantifiable risk estimates**, not just classification labels.
- Be well-documented and support **backtesting and monitoring**.

This compels us to favor **interpretable models**, or supplement black-box models with explanation layers (e.g., SHAP, LIME).

---

### 2. Importance of Proxy Variable for Default
The dataset lacks a direct `default` label. Therefore, we engineer a **proxy target variable** using RFM segmentation to identify disengaged customers (high risk). This allows us to:
- Create training labels aligned with business intuition.
- Simulate credit risk using customer behavior.

**Risks:**
- Label leakage: Poorly defined proxy may mislabel good customers as risky.
- Bias: Historical purchase behavior may not always reflect creditworthiness.
- Regulation: Proxy-based labels may not be defensible in audits.

---

### 3. Trade-offs: Simple vs. Complex Models
**Simple Models (e.g., Logistic Regression + WoE):**
- Pros: Interpretable, regulatory-friendly, easier to debug.
- Cons: May underperform on complex patterns.

**Complex Models (e.g., Gradient Boosting, Random Forest):**
- Pros: Higher accuracy, non-linear interactions.
- Cons: Black-box nature; requires additional interpretability layers.

In regulated environments, a **hybrid approach** (e.g., using complex models with explainability tools or interpretable post-processing) is often ideal.
