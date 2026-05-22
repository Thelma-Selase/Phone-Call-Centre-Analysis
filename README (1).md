# Call Center Operations Analysis

## TABLE OF CONTENTS

- [Overview](#overview)
- [Data](#data)
- [Data Processing](#data-processing)
- [Skills Demonstrated](#skills-demonstrated)
- [Objectives / Problem Statement](#objectivesproblem-statement)
- [Performance Metrics](#performance-metrics)
- [Data Analysis and Visualization](#data-analysis-and-visualization)
- [Insights](#insights)
- [Recommendations](#recommendations)

---

## OVERVIEW

This project presents an end-to-end operational analysis of an inbound call center handling e-commerce and direct-to-consumer (DTC) client contacts. The analysis covers a six-month period (October 2023 – March 2024) and examines key performance metrics including call volume trends, first call resolution, average handle time, customer satisfaction, and agent-level performance.

The goal was to identify where the operation was losing efficiency — through abandoned calls, uneven agent performance, and avoidable contact volume — and translate those findings into clear, data-backed recommendations. The final output includes an interactive one-page operations dashboard, a written findings report, and a projected impact framework outlining expected improvements from implementing the recommendations.

---

## DATA

The dataset used in this project covers inbound call center activity across voice, email, and chat/SMS channels. It includes the following key fields:

- **Call logs** — call ID, date, time, channel, duration, wait time, and resolution status (resolved, escalated, or abandoned)
- **Contact reasons** — categorised as order status, returns/refunds, billing issues, delivery delays, etc.
- **Agent records** — agent ID, first call resolution rate, average handle time, and post-call CSAT rating
- **Queue data** — wait time per call, used to calculate abandon rates by wait-time bucket
- **Monthly volume** — total inbound contacts per month, broken down by channel

The dataset spans 24,816 total call records across the six-month analysis window.

---

## DATA PROCESSING

The following steps were carried out to clean, structure, and prepare the data for analysis:

1. **Data cleaning** — removed duplicate records, corrected inconsistent date formats, and handled missing values in the resolution status and CSAT fields using mode imputation where appropriate.

2. **Feature engineering** — derived new variables including wait-time buckets (< 1 min, 1–2 min, 2–3 min, 3–5 min, > 5 min), contact reason categories from free-text logs, and monthly aggregates for volume and channel mix.

3. **Agent performance aggregation** — computed per-agent FCR, AHT, and CSAT averages across all calls within the period and ranked agents by composite performance score.

4. **Heatmap construction** — aggregated average call counts by day of week and hour of day to identify peak pressure windows across the operating schedule.

5. **Channel mix computation** — calculated monthly share of each channel (voice, email, chat/SMS) as a percentage of total inbound volume to track channel shift over time.

6. **Validation** — cross-checked aggregated KPIs (total handled calls, overall FCR, overall abandon rate) against raw record counts to confirm consistency before visualisation.

---

## SKILLS DEMONSTRATED

| Category | Skills |
|---|---|
| **Data Analysis** | Exploratory data analysis, descriptive statistics, trend analysis, cohort comparison |
| **Data Visualisation** | Dashboard design, chart selection, heatmap construction, KPI reporting |
| **Statistical Reasoning** | Rate calculations, aggregation, performance benchmarking, projection modelling |
| **Business Intelligence** | Operational metrics interpretation, root cause analysis, KPI framework design |
| **Communication** | Translating technical findings into plain-language insights and executive-level recommendations |
| **Tools** | Excel / Power BI (dashboard), Python (data processing and aggregation), SQL (data extraction) |

---

## OBJECTIVES / PROBLEM STATEMENT

The call center was experiencing growing inbound volume without a corresponding improvement in efficiency or customer experience. Specifically, the following questions were raised going into the analysis:

1. **Where are contacts being lost?** Abandoned calls were reported as a concern, but the exact point of drop-off — and how much was recoverable — was not quantified.

2. **What are customers calling about?** No structured breakdown of contact reasons existed, making it difficult to identify automation or deflection opportunities.

3. **When is the operation under the most pressure?** Peak windows were known anecdotally but had not been mapped with data to support precise staffing decisions.

4. **Is agent performance consistent?** Team-level KPIs masked wide variation between individual agents, which was suspected but not yet measured.

5. **Is the operation ready for continued growth?** Volume had been rising steadily, and leadership needed to understand whether current capacity could absorb projected Q2 demand.

The objective of this project was to answer all five questions using the available data, and to present findings in a format actionable enough to inform both operational and strategic decisions.

---
## Performance Metrics
1. **FCR – First Call Resolution**: The percentage of customer calls that are fully resolved the first time, without the customer needing to call back. A higher FCR means agents are solving problems completely in one interaction. 74.2% means about 3 in 4 calls were resolved on the spot.

2. **AHT – Average Handle Time**: The average total time an agent spends on a single call — including talk time, hold time, and any wrap-up work after the call ends. The target on this dashboard is under 4 minutes; the current average is 4 minutes 38 seconds, meaning agents are running slightly over.

3. **CSAT – Customer Satisfaction Score**: A rating customers give after an interaction, usually on a scale of 1–5. It directly measures how happy callers were with the service they received. A score of 4.1/5 is generally considered good, though there's room to improve.

4. **Abandon Rate**: The percentage of callers who hang up before they ever reach an agent — usually because the wait time is too long. An 11.4% abandon rate means roughly 1 in 9 callers gave up and left without being helped.

5. **Order Confirm Rate**: The percentage of orders that were successfully confirmed via a call. At 88.7%, this means nearly 9 in 10 orders went through confirmation without issue.

---

## DATA ANALYSIS AND VISUALIZATION

<img width="894" height="414" alt="image" src="https://github.com/user-attachments/assets/04ba4f3a-d9d8-4186-a391-85ad12212a59" />

The analysis was structured around five core visual components, each designed to answer one of the stated objectives:

**1. Call Outcome Distribution (Pie Chart)**
Breaks down total calls into resolved (74.2%), escalated (14.4%), and abandoned (11.4%). Immediately shows that roughly 1 in 9 callers never reaches a resolution — a significant leakage point.

**2. Contact Reason Mix (Donut Chart)**
Segments inbound contacts by reason: order status (32%), returns/refunds (24%), billing (18%), delivery delays (15%), and other (11%). Order status alone accounts for nearly a third of all volume, flagging a strong deflection opportunity.

**3. FCR & Abandon Rate by Channel (Grouped Bar Chart)**
Compares first call resolution and abandon rate across voice, email, and chat/SMS. Email leads on FCR (80%) with the lowest abandon rate (5%), while voice carries the highest abandon risk (14%). This informs channel mix strategy.

**4. Monthly Call Volume Trend (Area Chart)**
Tracks total inbound contacts from October 2023 through March 2024, showing growth from 1,850 to a peak of 4,100 — a 122% increase over six months. The upward trend signals a need for forward-looking workforce planning.

**5. Abandon Rate by Wait-Time Bucket (Column Chart)**
Shows abandonment rates at different queue lengths: 4% under 1 minute, 9% at 1–2 minutes, 21% at 2–3 minutes, 38% at 3–5 minutes, and 62% beyond 5 minutes. This pinpoints the exact threshold — around 2 minutes — at which abandon risk escalates sharply.

**6. Hourly Volume Heatmap (Day × Hour Grid)**
Maps average call counts by day of week and hour of day. The hottest cells cluster on Tuesday through Friday between 11am and 1pm, with Thursday 12pm recording the peak at 178 average calls per hour.

**7. Agent Performance Snapshot (Table)**
Ranks agents by FCR, AHT, and CSAT. The top agent achieves 82% FCR with a 3m 51s handle time; the lowest sits at 58% FCR and over 6 minutes per call. The spread is wide enough to have a measurable effect on overall team KPIs.

<img width="892" height="167" alt="image" src="https://github.com/user-attachments/assets/1018b773-596d-48ea-9350-824826d24817" />


**8. Inbound Channel Mix by Month (Stacked Bar Chart)**
Shows how voice, email, and chat/SMS shares shifted across the six-month period. Voice gradually declined from 70% to 63% of volume as email and chat grew — reflecting a slow but consistent channel migration worth supporting strategically.

---

## INSIGHTS

**1. The abandon rate problem is structural, not random.**
Abandonment is not evenly distributed across the day. It concentrates in specific peak windows — particularly Tuesday to Friday between 11am and 1pm — where queue times regularly exceed 3 minutes. At that point, 38–62% of callers hang up. This is a staffing and scheduling issue, not a service quality issue.

**2. Over a third of all contacts are for a single, automatable reason.**
Order status queries make up 32% of inbound volume. These calls follow a predictable pattern: a customer wants to know where their order is. This is exactly the type of query an IVR or chatbot handles instantly — without an agent — and at a fraction of the cost. This represents the single largest deflection opportunity in the dataset.

**3. Email and chat are significantly more efficient than voice.**
Email resolves 80% of contacts on the first interaction and has a near-zero abandon rate. Chat performs similarly. Voice, despite carrying 65–70% of volume, has the lowest FCR (71%) and the highest abandon rate (14%). This suggests that the channel mix is weighted toward the least efficient option.

**4. Agent performance variation is dragging team metrics down.**
The gap between the best and lowest-performing agents is 24 percentage points on FCR and over 2 minutes on average handle time. If the bottom two agents matched the team median, overall FCR would improve by an estimated 3–4 percentage points — without any new hiring or tooling investment.

**5. Volume is growing faster than the operation is scaling.**
Total inbound contacts grew 122% between October and March. The sharpest growth occurred in January through February, coinciding with post-holiday demand. There is no evidence in the data that capacity planning adjusted in response. If the current growth rate continues, Q2 volumes could exceed 4,500 contacts per month.

---

## RECOMMENDATIONS

**1. Deploy a self-serve option for order status queries.**
Build or integrate an IVR prompt or chatbot specifically for order tracking. Based on current volume, this would deflect an estimated 400 calls per week — freeing agents for billing disputes, returns, and escalations that genuinely require human handling. This is the highest-ROI recommendation in the analysis.

**2. Add staffing to the Tuesday–Friday 11am–1pm window.**
The heatmap makes the pressure window precise. Adding two agents specifically to this slot on these days is estimated to bring average queue time below 2 minutes, which — based on the abandon rate curve — would reduce abandonment by approximately 25–30% and recover roughly 340 contacts per week.

**3. Introduce structured peer coaching for bottom-performing agents.**
Agents B. Acheampong and K. Asante are both below the team median on all three key metrics. Pairing each with a top performer for targeted session reviews — focused on resolution scripting and call control — is a lower-cost intervention than external training and faster to execute. Target: close the FCR gap to within 5 percentage points of the team median within one quarter.

**4. Actively shift contact volume toward email and chat.**
Email and chat outperform voice on both FCR and abandon rate. Encouraging customers to use these channels for routine queries — through website prompts, auto-reply options, or post-call follow-up messaging — would improve overall efficiency without adding headcount.

**5. Begin Q2 workforce planning immediately.**
Volume grew 122% in six months. A conservative projection puts Q2 monthly contacts at 4,500+. Planning headcount, scheduling, and IVR capacity now — rather than reactively — prevents a repeat of the February peak strain. Recommend modelling for both a base case (35% growth) and an upside case (50% growth) to build planning flexibility.
