# Bank Loan Portfolio & Risk Analysis

**Analyst:** Austin  
**Date:** October 2025  
**Subject:** Solvency Stress Test of $435M Loan Portfolio  
**Tools:** Power BI · SQL (data prep) · CSV  
**Dataset:** ~38,600 loan applications  

---

## Executive Summary

This project analyzes a real-world bank loan portfolio containing approximately 38,600 loan applications to evaluate portfolio health, credit risk, and capital concentration.

Rather than relying on aggregate approval rates or single KPIs, the analysis intentionally segments the portfolio across:
- loan performance (good vs bad),
- credit grades,
- loan terms,
- borrower stability indicators,
- and loan purposes.

---

## Objective

The objective of this project was to build a decision-ready analytics layer that allows stakeholders to:
- Monitor overall loan portfolio health
- Identify concentration risk
- Compare good vs bad loan behavior
- Understand how credit grades explain outcomes
- Validate trends down to the individual loan level

---

## The Business Challenge

I was tasked with auditing a commercial loan portfolio of $435.8 Million (38,576 total loan applications). The bank is currently in a growth phase, but top-line revenue growth masked a critical underlying risk: a deteriorating credit quality in the unsecured lending sector.

Financial institutions process tens of thousands of loan applications, but raw application data alone does not clearly answer:
- how risky the loan portfolio is?
- which segments drive approvals vs rejections?
- Which loan purposes, terms, and borrower profiles carry higher risk?
- and where default exposure is concentrated?

Without a structured analytics layer, decision-makers lack visibility into loan quality, applicant risk, and portfolio health.

---

## Key Metrics (KPIs)

### Primary Portfolio KPIs (Baseline View)

- **Total Loan Applications:** 38.6K → Positive growth (MoM +6.9%)
- **Total Funded Amount:** $435.8M → Positive growth (MoM +13.0%)
- **Total Amount Received:** $473.1M → Positive growth (MoM +15.8%)
- **Average Interest Rate:** 12.05% → Increasing (MoM +3.5%)
- **Average DTI:** 13.33% → Increasing (MoM +2.7%)

### Risk & Customer Friction KPIs (External Context)

- **Total Financial Complaints:** 75,074
- **Disputed Complaints:** 9.71%
- **Complaints Resolved at No Cost:** 84.50%
- **Timely Response Rate:** 98.05%

---

### 2.1 Data Overview

- **Source:** Kaggle loan dataset
- **Records:** ~38,600 loan applications
- **Time-based:** Issue date available for trend analysis
- **Granularity:** One row per loan application
-	Standardizing Status: I grouped various loan statuses into a binary classification:
-	Good Loan: "Fully Paid" and "Current."
-	Bad Loan: "Charged Off" and "Default."

**Key attributes:**
- Loan amount, installment, interest rate
- Loan term (36 vs 60 months)
- Loan purpose
- Credit grade & sub-grade
- Borrower employment length
- Home ownership status
- Loan status (Fully Paid, Current, Charged Off)
- Amount collected

## Analytical Approach

The analysis was structured in four layers:

### 1. Portfolio Health
- Total applications, funded loans, and overall approval rate
- Distribution of loan statuses (fully paid, current, charged off)

### 2. Risk & Credit Quality
- Loan performance by credit grade and sub-grade
- Relationship between interest rates and loan outcomes
- Identification of high-risk segments based on default patterns

### 3. Applicant & Purpose Segmentation
- Loan behavior by income, employment length, and home ownership
- Risk comparison across loan purposes (e.g., debt consolidation, credit card, personal)

### 4. Trend & Distribution Analysis
- Changes in loan volume and performance over time
- Concentration of exposure by loan amount and term

<img width="1302" height="728" alt="aabf9705-3d07-40e9-800b-78c87264c922" src="https://github.com/user-attachments/assets/b745901e-dd46-427b-b001-6d97cef687b1" />

- **Charged-off loans show higher interest + DTI than fully paid loans**  
  “Higher-risk applicants are priced higher, yet still contribute disproportionately to defaults.”

- **Fully Paid loans dominate volume and dollars**
- **Charged-off loans are fewer in count but material in funded exposure**
- **Current loans exist but are not overstated**

While the majority of loans perform well, a small subset of charged-off loans accounts for a disproportionate share of unrecovered capital, emphasizing the importance of segmentation by loan status, interest rate, and applicant debt burden.

<img width="1301" height="732" alt="2" src="https://github.com/user-attachments/assets/01cc61e0-0e90-46e3-95d6-5e187c906655" />

- **Total funded amount increases steadily month-over-month, ending around $54M in December.**
- **Loan demand and funding activity ramp up over the year**
- **No sharp volatility → portfolio growth is stable, not erratic**

“Loan funding shows consistent growth across the year, indicating stable demand and predictable capital deployment.”

The state-level map shows funding concentrated in a subset of states rather than evenly distributed.

- **Geographic exposure is clustered**
- **Enables regional risk monitoring and policy tuning**

“The portfolio is skewed toward longer-tenure loans, increasing duration risk but potentially improving yield.”

- **Borrowers with 10+ years employment account for the largest funded amount (~$116M)**
- **Shorter tenures (<1–3 years) still receive material funding but at lower volumes**
- **Employment stability correlates with higher funded exposure**
- **Indicates underwriting preference toward longer employment histories**

**Top funded purposes:**
- **Debt consolidation:** $232.5M
- **Credit card:** $58.9M
- **Home improvement:** $33.4M

A single purpose category dominates funded exposure, creating concentration risk even if performance is strong.

- **Mortgage holders:** $219.3M
- **Renters:** $185.8M
- **Portfolio is split between asset-backed and non-asset-backed borrowers**

While the majority of loans perform well, the analysis reveals that funded exposure is concentrated across longer loan terms, specific purposes (notably debt consolidation), stable employment segments, and select geographies. The dashboard enables stakeholders to move beyond aggregate approval rates and identify where capital, duration risk, and potential loss exposure are most concentrated.

### Time Trends
- **Funded amount increases steadily throughout the year**
- **Indicates consistent demand and stable capital deployment**

### Loan Term
- **60-month loans:** ~63% of funded exposure
- **Longer tenures increase duration risk despite higher pricing**

### Purpose Concentration
- **Debt consolidation alone accounts for ~$232.5M**
- **Creates concentration exposure even if performance is strong**

### Borrower Profile
- **Largest funded exposure comes from borrowers with 10+ years employment**
- **Portfolio spans both mortgage holders and renters, enabling ownership-based risk comparison**

## Key Insights 

- **Portfolio risk is not evenly distributed; it clusters by loan purpose, term length, and credit grade.**
- **Higher-risk loans are priced with higher interest rates, yet still contribute disproportionately to charge-offs.**
- **A small subset of loans accounts for a large share of unrecovered capital, reinforcing the importance of segmentation over averages.**
- **Stable growth masks underlying concentration and duration risk, which becomes visible only through multi-dimensional analysis.**


<img width="1308" height="729" alt="3" src="https://github.com/user-attachments/assets/ab5b39ca-dea1-4e0e-b0dd-0136bf89f039" />
The majority of portfolio value and cash flow comes from good-performing loans.

### Pricing & Risk Signals
- **Avg Interest Rate:** 11.76%  
  (↓ from 12.05% portfolio average)
- **Avg DTI:** 13.22%
- **Better-performing loans are priced lower**
- **DTI alone is not a sufficient discriminator; credit quality matters**

### Loan Status Composition (Good Loans)
- **Fully Paid loans dominate volume and dollars**
- **Small share of “Current” loans**
- **No charged-off loans (as expected under this filter)**

When isolating good loans, the portfolio shows lower average interest rates, strong recovery performance, and predictable cash flow. Nearly all funded capital in this segment is either fully paid or actively performing, confirming that pricing and underwriting effectively capture low-risk borrowers.

<img width="1298" height="730" alt="4" src="https://github.com/user-attachments/assets/80f8f358-3f60-452e-900e-06051bfc262e" />
- **Loan applications increase steadily month-over-month**
- **No sharp spikes or drops**
- **Indicates predictable demand and stable underwriting**

Good-performing loans follow a smooth, consistent growth pattern, suggesting stable borrower demand and disciplined credit approval.
- **60-month loans dominate (~76%)**
- **36-month loans ~24%**
- **Longer tenures are not inherently risky when credit quality is strong**
- **Risk comes from who receives long-term loans, not the term alone**
- **10+ years:** ~7.5K applications
- **<1–3 years also significant but smaller**
- **Stable employment strongly correlates with good loan outcomes**
- **Confirms underwriting preference toward borrower stability**
- **Debt consolidation is dominant**
- **Credit card and “other” follow at much lower levels**
Debt consolidation is not inherently risky — risk emerges when combined with weaker credit profiles.
- **Renters and mortgage holders are nearly evenly split**
- **Ownership alone does not determine loan quality**

<img width="1301" height="731" alt="5" src="https://github.com/user-attachments/assets/30d86591-0373-45c5-9235-052443c321bc" />
- **5,333 applications (only ~14% of total volume)**
- **$65.5M funded**
- **$37.3M collected**
A relatively small portion of loans accounts for a disproportionately large share of unrecovered capital.
- **Funded:** $65.5M
- **Collected:** $37.3M
- **~43% of funded capital not recovered**
Bad loans exhibit a substantial recovery gap compared to good loans, despite representing a minority of total applications.
- **Avg Interest Rate:** 13.88%
  - ↑ ~2.1 pts vs good loans (11.76%)
- **Avg DTI:** 14.00%
  - Higher than both good loans and portfolio average
Higher-risk borrowers are priced higher, yet pricing alone does not fully offset default risk.  
This shows analytical maturity.

| Metric | Good Loans | Bad Loans |
|------|-----------|----------|
| Applications | 33.2K | 5.3K |
| Funded Amount | $370.2M | $65.5M |
| Amount Collected | $435.8M | $37.3M |
| Avg Interest | 11.76% | 13.88% |
| Avg DTI | 13.22% | 14.00% |

Aggregate portfolio metrics mask material differences in pricing, recovery, and risk concentration. Segmenting loans by performance reveals that bad loans, while limited in volume, drive a disproportionate share of recovery shortfall.

<img width="1310" height="729" alt="6" src="https://github.com/user-attachments/assets/35648db5-cdb6-4e25-877a-4be3f59b3746" />

- **Bad loan applications increase steadily over the year**
- **Growth is not random or spiky**
Bad loans do not occur as isolated anomalies; they follow a consistent intake pattern, indicating structural risk rather than one-off events.
- **60-month loans:** ~57%
- **36-month loans:** ~43%
- **Good loans:** ~76% 60-month
- **Bad loans:** shorter terms are over-represented
Risk in this portfolio is not driven purely by loan duration; borrower quality and purpose play a larger role.
**Top bad-loan segments:**
- **10+ years still present (important nuance)**
- **<1 year, 1–3 years represent a larger share than in good loans**
While long employment history does not eliminate risk, shorter employment tenures appear more frequently among bad loans, suggesting stability reduces—but does not remove—default exposure.
- **Debt consolidation dominates bad loans**
- **Credit card and “other” follow**
Debt consolidation is the largest driver of both good and bad loans, making it the single most important category to monitor for risk drift.
- **Renters (~2.7K) exceed mortgage holders (~2.2K) in bad loans**
Renters are modestly over-represented in bad loans, suggesting ownership status contributes incremental risk signal when combined with other factors.

<img width="1300" height="724" alt="7" src="https://github.com/user-attachments/assets/a5c7d080-1b74-4bc2-9101-b26d42c65032" />

This is a small-volume segment, but with material recovery gap.  
Even small, low-grade segments can generate disproportionate recovery shortfalls relative to their size.
- **Avg Interest Rate:** 21.50%
- **This is nearly double the portfolio average (~12%)**
Credit risk is explicitly priced into Grade G loans through significantly higher interest rates.
- **~46% of funded capital not recovered**
Despite aggressive pricing, recovery remains substantially lower than funded exposure in the lowest credit tier.
- **Avg DTI:** 13.95%
- **Comparable to bad-loan average**
DTI alone does not explain default behavior; credit grade captures additional borrower risk beyond debt burden.
- **Monthly applications fluctuate between ~3–16**
Even the lowest credit tier shows consistent intake rather than isolated spikes, indicating that high-risk lending is systematic rather than accidental.
- **60-month loans:** ~79%
- **36-month loans:** ~21%
- **Grade G is more long-tenure skewed than bad loans overall**
The riskiest credit tier is disproportionately exposed to long-duration loans, amplifying recovery risk despite higher pricing.
- **Largest segment:** 10+ years (28 loans)
- **But short-tenure segments (<1–3 years) remain significant**
Employment longevity alone does not eliminate credit risk; grade captures factors beyond tenure stability.
- **Debt consolidation dominates**
- **Small business appears next**
Debt consolidation remains the dominant risk driver even within the lowest credit tier, making it the most critical category to monitor for underwriting drift.
Ownership status provides limited separation power within the highest-risk credit tier.

<img width="1293" height="727" alt="8" src="https://github.com/user-attachments/assets/2af32340-d8ab-4fc3-bb72-fbcdcbbed29c" />

- **Avg Interest Rate:** 7.63%
- **This is ~⅓ of Grade G (21.5%)**
High-quality borrowers are priced significantly lower, reflecting strong confidence in repayment ability.
- **Even high-grade loans can charge off**
- **But exposure is smaller and pricing is conservative**
Loss exposure in high-grade loans is materially lower due to both reduced pricing risk and lower funded concentration.
- **Avg DTI:** 13.26%
- **Nearly identical to:**
  - Portfolio avg (~13.3%)
  - Grade G (~13.95%)
Debt-to-income alone does not explain credit outcomes; credit grade captures additional behavioral and financial risk factors.
##  Structural Contrast vs Grade G

| Dimension | Grade A | Grade G |
|---------|--------|--------|
| Avg Interest | 7.63% | 21.50% |
| Funded | $4.4M | $1.8M |
| Collected | $2.5M | $983K |
| Recovery Profile | Higher efficiency | Large gap |
| Risk Pricing | Conservative | Aggressive |

Credit grade is the strongest explanatory variable in the portfolio, driving pricing, exposure limits, and recovery outcomes more than any single borrower attribute.

By analyzing loans across the full credit spectrum—from Grade A to Grade G—the dashboard demonstrates how underwriting strategy, pricing, and risk concentration interact. While lower grades are priced aggressively, recovery gaps persist, especially when long tenures and high-risk purposes overlap. Conversely, higher grades show efficient pricing and controlled exposure, even when defaults occur. This confirms that segmentation by credit quality is essential for understanding true portfolio risk.

## Key Findings

My analysis revealed a **"Bad Loan" (Default) rate of 13.8%**, which is significantly higher than the industry standard benchmark of **3–5%**.

- **Capital at Risk:** $65.5 Million in funded capital has defaulted.
- **Root Cause:** We are approving high-risk borrowers (Grade F/G) and high-risk loan types (Debt Consolidation) without charging sufficient interest premiums to cover the potential losses.
- Loan performance varies significantly by credit grade, with lower grades showing higher default concentration.
- Interest rates increase with risk, indicating pricing aligns with applicant credit quality.
- Certain loan purposes carry higher default exposure, even at similar loan sizes.
- A small subset of applications contributes disproportionately to portfolio risk, highlighting the importance of segmentation rather than averages.

## Strategic Solution

By implementing a **Tiered Risk Filter**—specifically eliminating Grade G originations and increasing interest rates on Debt Consolidation loans—the bank can reduce its Bad Loan exposure by an estimated **$12M – $15M annually** while only reducing total loan volume by **~3%**.

## Questions Answered (Questions Only)

1. What are baseline portfolio KPIs and their MTD/MoM values?
2. What is the portfolio split between Good vs Bad loans (applications, funded, received)?
3. How do KPIs differ when filtered to Good loans vs Bad loans?
4. What do loan statuses show at baseline (Current, Fully Paid, Charged Off) across applications, funded, received, MTD, interest, DTI?
5. What are monthly baseline funded amounts (Jan–Dec)?
6. What is the baseline funded split by term (36 vs 60 months)?
7. What are baseline funded amounts by purpose?
8. What is the baseline funded distribution by home ownership?
9. Under Bad loans, what do monthly applications, term split, employment length counts, and home ownership counts look like?
