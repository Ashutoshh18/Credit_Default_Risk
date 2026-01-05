# Credit Default Risk Analysis
- Application-Time Risk Scoring
 - Project Overview
   

## **Problem: Predict credit default risk at the time of loan application**

- Goal: Estimate how risky a customer is likely to be before loan approval

- Approach: Treat the problem as risk scoring & ranking, not binary classification

- Focus: Business-aligned decision making, not just model accuracy
  


## Business Context

- False Negative (missed defaulter): High financial loss

- False Positive (safe customer flagged risky): Can be handled via manual review

Key implication:

- Accuracy is misleading

- Recall for defaulters is prioritized

- Model acts as a decision-support system, not an auto-approval engine



## Dataset

- Source: Home Credit Default Risk

- Target Variable:

- 0 → Loan repaid

- 1 → Loan default

- Class Imbalance: ~92% non-defaulters, ~8% defaulters

- Initial Features: ~120

- Final Selected Features: 44

- Data Scope: Application-time features only (to avoid data leakage)

Note: Raw data not included due to size and licensing constraints.



## Analytical Strategy

- Features grouped using credit risk logic:

1. Identity & Demographics

2. Repayment Capacity & Income Stability

3. Assets & Wealth

4. Housing Quality & Living Conditions

5. Credit History & External Risk

6. Contactability & Digital Stability

7. Address & Work Location Consistency

- Outcome:

Identification of strong signals, supporting signals, and weak/noisy features



## Feature Engineering

- Focus on economically meaningful ratios:

- Repayment Burden Ratio → annuity / income

- Credit-to-Income Ratio

- Loan-to-Goods Value Ratio

Why ratios?

- Capture repayment stress

- More informative than raw monetary values

- Align with how banks assess affordability
  


## Modeling Approach

- Model Type: Interpretable baseline classifier

- Train-Test Split: Stratified

- Class Imbalance Handling: class_weight = 'balanced'

- No resampling (original distribution preserved)

Evaluation Metrics:

- Recall (Defaulters)

- ROC-AUC

- Risk Decile Analysis



## Key Results

- Recall (Defaulters): ~67%

- Precision: ~16% (expected trade-off)

- ROC-AUC: ~74%

Risk Deciles:

- Top Deciles: Default rate multiple times higher than average

- Bottom Deciles: Very low default rate

-  Confirms model effectiveness as a risk-ranking system



## How the Model Would Be Used

- Not for direct approval / rejection

Practical usage:

- High-risk applicants: Reject or strict manual review

- Medium-risk applicants: Detailed underwriting

- Low-risk applicants: Fast-track approval

Purpose:

- Prioritize attention

- Reduce costly mistakes

- Support human decision-making



## Key Takeaway

A good credit risk model is not defined by high accuracy,
but by how well it supports risk-aware, real-world decisions.

This project emphasizes feature understanding, business logic, and decision context
over complex algorithms or metric chasing
