# Contact Centre Headcount Capacity Plan: When Do We Need to Hire?

![Python](https://img.shields.io/badge/Python-3-3776AB?logo=python&logoColor=white) ![pandas](https://img.shields.io/badge/pandas-150458?logo=pandas&logoColor=white) ![Planning](https://img.shields.io/badge/horizon-26%20weeks-e36209) ![Data](https://img.shields.io/badge/data-simulated-lightgrey) ![License: MIT](https://img.shields.io/badge/license-MIT-green)

A 26-week **long-term capacity plan** in Python. It turns a contact forecast into required FTE, projects available FTE after **attrition, hiring lead time, training and new-hire ramp**, and compares three hiring strategies for a festive peak.

> **Data note:** all data is **simulated**. No company or customer data is used.

```mermaid
---
config:
  xyChart:
    width: 900
    height: 400
---
xychart-beta
    title "Productive FTE vs required: required (line 1), reactive (line 2), planned (line 3), planned + flex (line 4)"
    x-axis ["W1","W2","W3","W4","W5","W6","W7","W8","W9","W10","W11","W12","W13","W14","W15","W16","W17","W18","W19","W20","W21","W22","W23","W24","W25","W26"]
    y-axis "FTE" 90 --> 160
    line [104,107,107,105,106,106,108,108,110,106,113,110,112,112,112,142,144,143,143,117,115,114,118,117,115,118]
    line [119,118,117,116,115,114,113,112,112,111,110,109,108,107,106,106,105,104,103,107,108,109,109,108,107,126]
    line [119,118,117,116,115,114,113,112,112,115,116,132,142,149,153,153,152,150,149,148,147,146,144,143,142,141]
    line [119,118,117,116,115,114,113,112,112,116,116,117,137,144,151,154,153,152,151,125,126,127,127,126,125,124]
```

## Assumptions

| Input | Value |
|---|---|
| Starting headcount | 120 agents |
| Contacts | ~24k/week, +0.6% weekly growth, **+25% festive peak in weeks 16–19** |
| AHT / occupancy / shrinkage | 360 s / 85% / 32% |
| Attrition | 0.8% per week (~3.4% per month) |
| Hiring lead time | 6 weeks (requisition → joining) |
| Training + ramp | 3 weeks classroom, then 50% → 70% → 90% productivity |

So a hire raised today is **not fully productive for 12 weeks**.

## Strategies compared

- **A. Reactive:** raise a hiring request when the gap shows up.
- **B. Planned:** raise requests 12 weeks ahead of need, including expected attrition.
- **C. Planned + flex:** plan permanent hiring to the *baseline* and cover the peak with a temporary batch trained ahead and released after the peak.

## Key findings (simulated)

| Strategy | Weeks understaffed | Worst gap (FTE) | Peak coverage | Hires | Avg overstaff after peak (FTE) |
|---|---:|---:|---:|---:|---:|
| A. Reactive | **15 of 26** | −40.6 | **73%** | 50 | 1.1 |
| B. Planned | 0 | +1.5 | 106% | 50 | **28.1** |
| C. Planned + flex | 0 | +1.5 | 107% | 60 (30 temp) | **9.5** |

- **Reactive hiring fails the peak.** With a 12-week pipeline, hires requested when the gap appears land after the peak is over. Peak coverage is only 73%, with a gap of up to 41 FTE.
- **Planning ahead fixes the peak but creates a hangover.** Hiring permanent staff for a 4-week peak leaves ~28 surplus FTE for the rest of the plan.
- **Planned + flex gets the best of both.** Same zero understaffed weeks, and post-peak surplus drops from ~28 to ~10 FTE.
- **Attrition is a silent hiring need.** At 3.4% per month, ~41 of 120 agents leave in a year. Every plan has to backfill before it grows.

Full tables: [`outputs/RESULTS.md`](outputs/RESULTS.md) · weekly plan: [`outputs/weekly_plan.csv`](outputs/weekly_plan.csv)

## Run it

```bash
pip install -r requirements.txt
python capacity_plan.py
```

## Skills shown

Long-term capacity planning · Headcount modelling · Attrition & backfill · Hiring lead time & ramp · Scenario analysis · Python (pandas, NumPy)


---

## About me

I'm Rahul, a Control Tower – WFM Analyst in Gurugram. I build these small projects to work through the planning problems I see on the job, using made-up data so nothing confidential leaves work. If you spot something I could do better, I'd like to hear it.

[LinkedIn](https://www.linkedin.com/in/rahul-219543159/) · [GitHub profile](https://github.com/mail4rahulwork-sketch)

**Other projects**
- [Contact Centre WFM Dashboard (Power BI, live demo)](https://github.com/mail4rahulwork-sketch/powerbi-contact-centre-wfm-dashboard)
- [WFM Forecast to Erlang C Staffing](https://github.com/mail4rahulwork-sketch/wfm-forecast-erlang-staffing)
- [Intraday RTA Early Warning](https://github.com/mail4rahulwork-sketch/intraday-rta-early-warning)
