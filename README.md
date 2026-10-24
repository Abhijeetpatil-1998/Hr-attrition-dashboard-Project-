# Workforce-Attrition-Dashboard (Interactive HR Dashboard using HTML + Chart.js)

## Project Objective
The HR / leadership team wants a single attrition report so that the CEO, CHRO and Board can track headcount and exits, see where and when people are leaving, check manager and department performance, and focus retention efforts on the right teams.

## Dataset used
- Employee-level HR data (171 employees, hiring cohorts 2020 to 2025, data as of 19-Jul-2025)
- Fields: Emp Id, Name, Status (On-Board / Attrition / Transfer), Movement (IJP / OnRoll), Date of Joining, Date of Relieving, Reporting Manager, Employment Type, Gender, Marital Status, Grade, Department, Total Experience, Hiring Cohort
- Dataset: embedded inside `hr_attrition_dashboard.html` (no external data file needed)

## Questions (KPIs)
1. What is the total number of employees, and how many are active vs. have left?
2. What is the overall attrition rate and retention rate?
3. Which department has the highest attrition?
4. How do hiring cohorts (2020 to 2025) compare on survival?
5. Which year had the most exits, and how long do leavers stay before exiting?
6. How do Contract and Permanent staff compare, and which grade loses the most people?
7. How is each reporting manager's team performing on attrition?
8. What is the internal mobility rate (IJP, OnRoll and transfers)?

## Dashboard Interaction
Open `hr_attrition_dashboard.html` in any browser (internet needed once to load Chart.js).
- Filters: Department, Grade, Manager, Emp Type, Gender, Marital, Status, Movement, cohort range, joining date, name / Emp Id search
- Click any bar, slice, cell or column to filter the whole dashboard; active filters appear as removable pills
- Light / dark theme, Print / PDF, sortable employee table, and CSV export of the filtered rows
- Filter state is saved in the URL so a view can be shared

## Process
1. Verified data for missing values, inverted dates and anomalies. Flagged them (not dropped) and excluded them only from tenure calculations.
2. Made sure data is consistent with respect to data type, date format and values used (Emp Id kept as text, dates parsed to UTC).
3. Built the data model and metrics in JavaScript (Total Employees, Active, Attrition, Attrition %, Retention %, Tenure at exit, Mobility %).
4. Created visuals according to the questions asked: KPI cards, department and manager bars, cohort survival chart, exits-over-time chart, grade vs. type chart, tenure histogram, gender donut, department x cohort heatmap and an employee table.
5. Merged all visuals into one dashboard with filters and cross-chart click filtering, plus auto-generated leadership insights (finding, why it matters, action, owner).

## Dashboard
![Workforce & Attrition Dashboard](images/dashboard.png)

## Project Insight
- Total of **171 employees** on record: **118 active**, **47 have left** and **6 were transferred**, giving an overall attrition rate of **27.5%** (retention 72.5%).
- **Accounting** has the highest attrition at **50%** (9 of 18), while **Sales** is the healthiest at **8.7%** (2 of 23). **Operations** (14 leavers) and **HR** (12 leavers) together account for **55%** of all exits.
- Earlier cohorts are leaking: **41.6%** of 2020 to 2022 joiners have left (42 of 101), versus 7.1% for 2023+ joiners, which are still maturing and should not be read as success. The worst pocket is **HR joiners of 2020**, where 8 of 11 (73%) have left.
- Exits peaked in **2023 with 18 leavers**. Median tenure at exit is **15 months** (average 20.5), and **66%** of leavers (29 of 44 with valid dates) go within 24 months.
- **Contract** staff leave at **43.5%** (10 of 23) versus **25.0%** for permanent staff (37 of 148), about **1.7x** as often.
- Among managers with 10+ reports, **Janelle Wiley** (36.6%, 15 of 41) and **Jefferson Perry** (36.4%) have the highest attrition, while **Ryan Simmons** has the lowest at **19.0%** (11 of 58), despite leading the largest team.
- Internal mobility (IJP, OnRoll and transfers) is **18.1%** (31 of 171). Gender (female 29.7% vs male 26.2%) and marital status gaps are modest and not conclusive.

## Final Conclusion
To improve retention, a focused plan should be implemented for Accounting, HR and Operations, which hold most of the exits, especially the 2020 to 2022 joiners with 3 to 5 years of service. Contract staff need a conversion pathway and better renewal practice, and onboarding plus 90-day and 12-month check-ins should be strengthened since most people leave within two years. Teams under Janelle Wiley and Jefferson Perry need a manager-effectiveness review, and practices from Ryan Simmons' team and the Sales function can be shared across the company. Data quality should also be fixed (1 leaver with no relieving date, 2 with relieving before joining, unusable Date of Birth) so that tenure analysis is reliable.

## Tools Used
- HTML, CSS and JavaScript (data model, metrics, filters)
- Chart.js 4.4.1 (visuals)
- Microsoft Excel (source data cleaning)
