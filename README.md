# Marketing-Analytics-Subscription-based-product-

# Title: A/B/C Experiment on Pricing Plan Order optimization for a Subscription-Based Product

## Overview
This project presents an anonymized A/B/C experiment for a **subscription-based digital product**. The goal was to evaluate whether changing the **display order of subscription plan durations** on a landing/pricing page influences user conversion outcomes.

### Variants Tested (Plan Order)
- **Variant A (Control):** 1 / 24 / 12  
- **Variant B:** 1 / 12 / 24  
- **Variant C:** 24 / 12 / 1  

## Business Objective
Improve conversion outcomes by optimizing how plan options are presented, with focus on:
- improving acquisition efficiency (signups), and/or  
- improving monetization (paid subscriptions and revenue quality).

## Selecting the Right KPIs (What to measure and why)
When choosing KPIs for experiments, the goal is to:
1) pick a **primary KPI** that best represents the business objective and is least ambiguous,  
2) add **secondary KPIs** that explain *why* results moved and capture downstream value,  
3) add **guardrail KPIs** to ensure no harmful side effects.

### Primary KPI (Decision KPI)
**Signup Conversion Rate (session-based)**  
- **Definition:** Sessions with ≥1 signup / Total sessions  
- **Why primary:** It represents top-of-funnel acquisition intent and usually has higher volume (faster statistical power).  
- **When it is appropriate:** When the experiment is expected to influence initial commitment (e.g., signup/start trial).

### Secondary KPIs (Monetization + Funnel Quality)
**Paid Conversion Rate (session-based)**  
- **Definition:** Sessions with ≥1 paid subscription / Total sessions  
- **Why:** Captures monetization impact. A variant may not increase signups but can improve paid outcomes.

**Subscription-to-Signup Ratio (Efficiency)**  
- **Definition:** Paid sessions / Signup sessions  
- **Why:** Measures funnel efficiency and quality of signups (conversion to paid).

### Guardrail KPIs (Experience/Quality Protection)
- **Bounce Rate**
- **Average Session Duration**
- (Optional) Refund/chargeback rate, cancellation within 7 days, support tickets (if available)

> Metric implementation note: signups and paid conversions were treated as **binary session flags** (a session converts if count > 0) to avoid overstating outcomes when multiple events occur in a single session.

## Method Summary
1. Data quality checks (missing values, duplicates, outliers, parsing complex fields).
2. KPI computation per variant and by key segments (country, device type).
3. Two-proportion z-tests for conversion metrics.
4. Insights + rollout recommendation (including risks and next steps).

## Key Results (High Level)
- **Signup Conversion Rate:** Differences between variants were not statistically significant.
- **Paid Conversion Rate:** Variant C delivered the strongest monetization outcome and showed a statistically significant uplift vs control.
- **Efficiency:** Variant C had the highest subscription-to-signup conversion efficiency.
- **Guardrails:** Engagement and bounce behavior remained stable.

## Recommendation
Roll out **Variant C (24/12/1)** as the default plan order because it improves monetization outcomes while maintaining stable acquisition and guardrail metrics.

## Disclaimer
This is an anonymized portfolio project for a subscription-based product. Company identifiers have been removed. Any published dataset should be synthetic or publicly shareable (no proprietary data).
