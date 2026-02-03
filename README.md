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

---

## Problem

Financial institutions process tens of thousands of loan applications, but raw application data alone does not clearly answer:
- how risky the loan portfolio is,
- which segments drive approvals vs rejections,
- and where default exposure is concentrated.

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
