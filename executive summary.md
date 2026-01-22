# Executive Summary — Pricing Plan Order A/B/C Experiment (Subscription Product)

## Business Context
A subscription-based product offers multiple billing cycles (e.g., 1-month, 12-month, 24-month). The pricing page displays these options in a specific order. Since plan positioning can influence user choice (attention bias and value anchoring), an A/B/C experiment was launched to evaluate whether reordering plans improves conversions.

## Objective
Select the best plan-display order to improve conversion outcomes while maintaining a healthy user experience.

## Variants Tested
- **Variant A (Control):** 1 / 24 / 12  
- **Variant B:** 1 / 12 / 24  
- **Variant C:** 24 / 12 / 1  

## KPI Framework (Selecting Primary + Secondary KPIs)

### Primary KPI (Decision KPI)
**Signup Conversion Rate (session-based)**  
- Chosen because it reflects top-of-funnel success and typically has sufficient volume to reach statistical significance faster.
- Used as the main “success/fail” indicator for acquisition-oriented experiments.

### Secondary KPIs (Monetization + Funnel Quality)
**Paid Conversion Rate (session-based)**  
- Captures monetization impact. A change in plan order may influence purchase decisions more than signups.

**Subscription-to-Signup Ratio**
- Measures how efficiently signups turn into paying customers (quality of acquisition).

### Guardrail KPIs (Risk Control)
- **Bounce Rate** and **Avg Session Duration**
- Used to ensure the variant does not degrade user experience or attract lower-quality traffic.

> Conversion metrics were implemented using binary session flags:
- signup session if signups > 0
- paid session if subscriptionsTotal > 0

### Key KPI Comparison

| KPI | Variant A (Control) | Variant B | Variant C |
|---|---:|---:|---:|
| Signup Conversion Rate (%) | 26.16 | 25.90 | 26.24 (+0.08 pp) |
| Paid Conversion Rate (%) | 2.08 | 2.06 | 2.17 (+0.09 pp) |
| Subscriptions-to-Signup Ratio (%) | 5.82 | 5.80 | 6.12 (+0.30 pp) |
| Avg Session Duration (sec) | 256.36 (4.27 min) | 255.18 (4.25 min) | 256.21 (4.27 min) |
| Bounce Rate (%) | 6.08 | 6.24 | 6.17 |


## Key Findings
- **Signup Conversion Rate:** No statistically significant difference across variants (p > 0.05).
- **Paid Conversion Rate:** Variant C produced the strongest outcome and showed a statistically significant uplift versus control (p < 0.05).
- **Funnel Efficiency:** Variant C had the best subscription-to-signup efficiency.
- **Guardrails:** Engagement and bounce behavior were stable across variants.

## Recommendation
Roll out **Variant C (24/12/1)** as the default plan order.  
Rationale: Even though signup conversion was unchanged, Variant C improves monetization outcomes and converts signups into paid subscriptions more efficiently without harming guardrail metrics.

## Next Steps
1. Validate results using user-level metrics if available (preferred over session-level).
2. Consider country-level personalization for high-impact regions.
3. Run follow-up tests (e.g., default highlight, savings messaging, price anchoring) to maximize gains.
