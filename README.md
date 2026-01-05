Project Title

Credit Default Risk Analysis (Application-Time Risk Scoring)

📌 Problem Statement

Banks need to decide whether a loan applicant is likely to default before the loan is approved.
The cost of making a wrong decision is not equal:

Missing a defaulter (false negative) is costly

Flagging a safe customer (false positive) can still be handled through manual review

This project focuses on application-time credit risk, using customer profile data to estimate how risky a new applicant is likely to be.

📊 Dataset

Source: Home Credit Default Risk dataset

Target variable: TARGET

0 → Loan repaid

1 → Loan default

Class imbalance: ~92% non-defaulters, ~8% defaulters

Initial features: ~120

Final features after analysis: 44

Only application-time features are used to avoid data leakage.

🧠 Approach & Key Ideas

Instead of treating this as a simple classification problem, the project is approached as a risk scoring problem.

Key ideas:

Accuracy is misleading due to class imbalance

Recall on defaulters is more important than precision

The model should rank customers by risk, not make hard approve/reject decisions

Feature Understanding

Features were grouped based on domain logic:

Identity & demographics

Repayment capacity & income stability

Assets & wealth

Housing quality & living conditions

Credit history & external risk

Contactability & digital stability

Address & work location consistency

This made EDA more structured and helped identify strong vs weak risk signals.

🔑 Feature Engineering

Key ratio-based features were created to capture repayment stress:

Repayment burden ratio (annuity / income)

Credit-to-income ratio

Loan-to-goods value ratio

These ratios exposed risk patterns that were not visible using raw features alone.

🤖 Modeling & Evaluation

Model type: Interpretable baseline classifier

Class imbalance handling:

Stratified train-test split

class_weight = 'balanced'

Evaluation focus:

Recall (defaulters)

ROC-AUC

Risk decile analysis

Key Results

Recall (defaulters): ~67%

Precision: ~16% (expected trade-off)

ROC-AUC: ~74%

Risk deciles show clear monotonic separation

🏦 How This Model Would Be Used

This model is not meant for direct loan approval.
It works best as a decision-support tool:

High-risk applicants → rejection or strict manual review

Medium-risk applicants → detailed underwriting

Low-risk applicants → fast-track approval

The model helps banks prioritize attention, not automate decisions blindly.

⚠️ Limitations

No time-based validation

Historical approvals may contain policy bias

No transactional or post-loan behavior data

📁 Repository Structure
├── notebook/
│   └── credit_risk_analysis.ipynb
├── summary/
│   └── project_summary.pdf
├── README.md

📌 Key Takeaway

A good credit risk model is not the one with the highest accuracy,
but the one that helps avoid costly mistakes and supports real decision-making.
