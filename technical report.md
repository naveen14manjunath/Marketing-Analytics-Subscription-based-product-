# Technical Report — A/B/C Pricing Plan Order Experiment (Subscription Product)

## 1. Experiment Design

### 1.1 Business Problem
The product offers multiple subscription durations. Users may choose differently based on plan position (anchoring effect, attention bias, perceived value). This experiment tests whether changing plan order improves conversion outcomes.

### 1.2 Variants
- **Variant A (Control):** 1 / 24 / 12  
- **Variant B:** 1 / 12 / 24  
- **Variant C:** 24 / 12 / 1  

### 1.3 KPI Selection Framework (Primary, Secondary, Guardrails)

Selecting KPIs correctly determines whether the experiment leads to the right decision. The KPI framework used:

#### Primary KPI (Decision KPI)
**Signup Conversion Rate**
- **Definition:** Sessions with ≥1 signup / Total sessions
- **Why selected:** High-volume top-of-funnel signal; sensitive to changes in page clarity, friction, or perceived value.
- **When appropriate:** When the change is expected to influence initial intent (signup/start trial).
- **Success criteria example:** statistically significant uplift vs control without guardrail degradation.

#### Secondary KPIs (Explain + Monetize)
**Paid Conversion Rate**
- **Definition:** Sessions with ≥1 paid subscription / Total sessions
- **Why selected:** Captures monetization; many pricing page changes affect purchase behavior more than signups.

**Subscription-to-Signup Ratio**
- **Definition:** Paid sessions / Signup sessions
- **Why selected:** Measures the *quality* of signups and funnel efficiency (turning intent into revenue).

Optional secondary KPIs (if available)
- Average revenue per session (ARPS) / expected LTV uplift
- Refund/cancellation within 7 days (quality)

#### Guardrail KPIs (Protect Experience)
- Bounce Rate
- Avg Session Duration
- (Optional) customer support contact rate, payment failure rate, page load performance

**Implementation detail**
Conversion counts were transformed into binary session outcomes to prevent over-counting:
- `is_signup = 1 if signups > 0 else 0`
- `is_paid = 1 if subscriptionsTotal > 0 else 0`

---

## 2. Data Overview & Quality Checks

### 2.1 Fields
- Variant assignment, device type, country
- Signups, paid subscriptions
- Bounce indicator, session duration
- Plan-cycle breakdown field (dictionary-like)

### 2.2 Data Quality Issues Identified
- Missing/invalid country values
- Duplicate session IDs
- Session duration outlier(s)
- Complex field parsing
- Multiple conversion events per session

### 2.3 Cleaning (High Level)
- Standardized segmentation fields and handled missing values.
- Deduplicated sessions for accurate denominators.
- Treated extreme duration outliers carefully to avoid skewed averages.
- Parsed plan-cycle breakdown fields for plan-preference analysis.
- Converted signups/subscriptions to binary session flags.

---

## 3. Analysis Approach

### 3.1 KPI Computation
- Aggregated KPIs by variant.
- Computed segmented KPIs by device type and country.

### 3.2 Statistical Testing
Used **two-proportion z-tests** to compare conversion rates:
- Signup conversion: A vs B, A vs C
- Paid conversion: A vs B, A vs C

---

## 4. Results

### 4.1 Primary KPI — Signup Conversion Rate
Signup conversion rates were very close across variants and did not show statistical significance vs control (p > 0.05).  
**Conclusion:** Plan-order changes did not materially impact signup conversion.

### 4.2 Secondary KPI — Paid Conversion Rate
Paid conversion was highest for Variant C and showed statistical significance vs control (p < 0.05).  
**Conclusion:** Variant C improves monetization.

### 4.3 Secondary KPI — Subscription-to-Signup Ratio
Variant C produced the strongest subscription-to-signup efficiency.  
**Conclusion:** Variant C increases paid yield per signup.

### 4.4 Guardrails — Engagement/Bounce
Bounce rate and session duration were stable across variants.  
**Conclusion:** No evidence of negative user experience impact from Variant C.

---

## 5. Segmentation Insights
- **Device:** Desktop converts higher than phone. Variant ranking is consistent across devices.
- **Country:** Some regions respond differently; localized optimization may unlock additional gains.

---

## 6. Recommendation
Roll out **Variant C (24/12/1)** because it:
- improves monetization outcomes (paid conversion),
- increases funnel efficiency (paid per signup),
- maintains stable guardrail metrics.

---

## 7. Limitations & Next Steps
- Prefer user-level assignment and analysis to strengthen independence assumptions.
- Validate deduplication and instrumentation logic with tracking owners.
- Document power/MDE and minimum run time for future experiments.
- Follow-up tests: highlight “best value” plan, savings messaging, anchoring, personalization by region.
