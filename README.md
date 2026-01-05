Credit Default Risk Analysis
Application-Time Risk Scoring

1. Overview
This project focuses on credit default risk analysis at the time of loan application.
The objective is to estimate how risky a new applicant is likely to be, based only on information available before loan approval.

Rather than treating this as a pure classification problem, the project is approached as a risk scoring and ranking problem, which better reflects how credit models are used in practice.

2. Business Context
In credit lending, not all mistakes have the same cost:
False Negative (missed defaulter): High financial loss
False Positive (safe customer flagged risky): Can be handled via manual review

Because of this cost asymmetry:
Accuracy is not a reliable metric
Recall on defaulters is prioritized
The model is evaluated as a decision-support tool, not a final decision-maker

3. Dataset
Source: Home Credit Default Risk dataset
Target variable:
0 → Loan repaid
1 → Loan default

Class distribution: ~92% non-defaulters, ~8% defaulters
Initial features: ~120
Final selected features: 44
Only application-time features are used to avoid data leakage.

Note: Raw data is not included in this repository due to size and licensing constraints.

4. Analytical Approach
To manage the high dimensionality of the dataset, features were grouped based on risk logic and domain understanding:
Identity & demographics
Repayment capacity & income stability
Assets & wealth
Housing quality & living conditions
Credit history & external risk
Contactability & digital stability
Address & work location consistency

This grouping allowed focused EDA and helped identify strong, weak, and noisy signals before modeling.

5. Feature Engineering
Instead of relying only on raw monetary values, ratio-based features were created to capture repayment stress:
Repayment burden ratio (annuity / income)
Credit-to-income ratio
Loan-to-goods value ratio

These ratios provided clearer economic meaning and exposed risk patterns not visible in raw features.

6. Modeling Strategy
Model type: Interpretable baseline classifier

Train-test split: Stratified
Class imbalance handling: class_weight = 'balanced'

Evaluation focus:
Recall (defaulters)
ROC-AUC
Risk decile analysis
Resampling techniques were intentionally avoided to preserve the original data distribution.

7. Key Results
Recall (defaulters): ~67%
Precision: ~16% (expected trade-off)
ROC-AUC: ~74%

Risk decile analysis shows clear monotonic separation:
Top deciles have default rates multiple times higher than average
Bottom deciles show very low default rates

This confirms the model’s ability to rank applicants by risk.

8. How the Model Would Be Used
This model is not designed for direct loan approval.
A realistic usage would be:

High-risk applicants: rejection or strict manual review

Medium-risk applicants: detailed underwriting

Low-risk applicants: fast-track approval

The model helps prioritize attention and reduce costly mistakes, rather than automate decisions blindly.


11. Key Takeaway
A strong credit risk model is not defined by high accuracy,
but by how well it supports risk-aware, real-world decision-making.
