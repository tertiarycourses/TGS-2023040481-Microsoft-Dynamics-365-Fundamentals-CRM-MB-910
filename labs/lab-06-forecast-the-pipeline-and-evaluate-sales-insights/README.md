# Lab 6 — Forecast the Pipeline and Evaluate Sales Insights

> **Topic 06:** Dynamics 365 Sales Capabilities and Related Apps  ·  **Estimated time:** 45 minutes

**Objective:** Describe Dynamics 365 Sales capabilities and related apps: pipeline and forecasting, Sales Insights standard vs premium, LinkedIn Sales Navigator, the mobile app and Copilot for Sales.

## Scenario

Your sales director wants to know whether to buy the Sales Insights premium add-on. You build the pipeline view and a forecast, work the sales accelerator list, examine which Sales Insights features are included versus licensed, review the LinkedIn Sales Navigator and mobile experiences, and produce a written investment recommendation — exactly the evidence LO5 requires.

## What you'll produce

A pipeline chart and forecast for the current period, a sales accelerator work list with a sequence applied, a completed standard-vs-premium feature comparison, and a one-page investment recommendation.

**Tools:** Dynamics 365 Sales Hub, Sales Insights, forecasting, sales accelerator, LinkedIn Sales Navigator, Copilot for Sales, Power BI

## Workflow

1. Import the pipeline data and open the pipeline chart
2. Configure and read a sales forecast
3. Work the sales accelerator list and apply a sequence
4. Compare Sales Insights standard vs premium features
5. Write the investment recommendation

## Mock data

| File | Rows | Columns |
|---|---|---|
| [`data/opportunities.csv`](data/opportunities.csv) | 8 | Topic, Account, Est. Revenue (SGD), Est. Close Date, Rating, Probability, Sales Stage |
| [`data/sales-insights-comparison.csv`](data/sales-insights-comparison.csv) | 10 | Feature, Standard (included), Premium (licensed), Business value, Needed by us? (Y/N) |

## Step-by-step

1. Open the Dynamics 365 Sales Hub. Import data/opportunities.csv into the Opportunity table (Opportunities > Import from Excel) so you have a pipeline to analyse. Map Topic, Account, Est. Revenue, Est. Close Date and Rating.
2. Under Performance in the left navigation select Sales Pipeline (or open the Sales Manager dashboard). Read the pipeline chart: opportunities plotted by estimated close date, colour-coded by rating and sized by deal value.
3. Change the chart's time filter to This Quarter, then Next Quarter, and note how pipeline coverage changes. Record the total open pipeline value for each period in your worksheet.
4. Open Forecasts (Performance > Forecasts). If a forecast is already configured, open it. If not, go to App Settings (or Sales Insights settings) > Forecast configuration > New, choose the Org chart forecast template, set the fiscal period to the current quarter, and set the roll-up entity to Opportunity.
5. In the forecast configuration, review the forecast categories — Pipeline, Best Case, Committed, Won and Omitted — and confirm which opportunity field drives them. Activate the forecast.
6. Open the activated forecast grid. Read the columns for each seller: Quota, Committed, Best Case, Pipeline and Won. Drill into one seller's row to see the underlying opportunities. Adjust one value and note that the adjustment is tracked separately from the system roll-up.
7. Record the forecast accuracy question in your worksheet: what would you compare (forecast committed vs actual won, by period) to prove the forecast is trustworthy?
8. Open the sales accelerator work list: in the left navigation select Sales accelerator (or My Work > Sales accelerator). If it is not enabled, enable it under App Settings > Sales accelerator and choose the record types to include.
9. Review the prioritised work list. Note the up-next widget, the record context and the multi-channel action buttons (call, email, SMS, LinkedIn message) available without leaving the workspace.
10. Create a sequence: App Settings > Sequences > New sequence. Name it 'New lead follow-up - <your initials>'. Add these steps in order: (1) Phone call, (2) Wait 1 day, (3) Send email, (4) Wait 2 days, (5) LinkedIn connection request. Activate the sequence.
11. Connect the sequence to a record: open one of your imported leads or opportunities, select Connect sequence on the command bar, and choose your sequence. Confirm the steps now appear in the seller's up-next widget.
12. Examine Sales Insights. Open App Settings > Sales Insights (or Settings > Sales Insights). List which features are switched on and which report that they require a premium licence.
13. Complete the comparison table in data/sales-insights-comparison.csv. Standard (included with Sales Enterprise): Assistant, auto capture, email engagement, sequences. Premium (separate licence): Assistant with Studio, auto capture premium, relationship analytics, predictive lead scoring, predictive opportunity scoring, notes analysis, conversation intelligence, who-knows-whom.
14. Open one opportunity and look at the Assistant cards in the right pane (or the Up next widget). Note what each card is telling the seller to do and where the signal came from.
15. Review the LinkedIn Sales Navigator controls. On a lead or contact form, note where the LinkedIn Sales Navigator Lead control would appear and what it surfaces: top card, news/icebreakers, connections (get introduced), related leads. On an account, the Account control adds recommended leads. If your tenant has no Sales Navigator licence, review the Microsoft documentation and record the capabilities.
16. Review the mobile experience. Install or open the Dynamics 365 Sales mobile app (or use the documentation walkthrough) and note the four seller scenarios it optimises: plan your day, prepare for meetings, capture post-meeting notes by voice, and join online meetings.
17. Review Microsoft 365 Copilot for Sales: note that it works inside Outlook and Teams to summarise email threads and meetings, draft replies, and save CRM updates without opening Dynamics 365. Record which of your team's tasks it would remove.
18. Write your recommendation in data/investment-recommendation.md (a template is provided): state the business problem, the pipeline and forecast evidence you gathered, the standard-vs-premium gap, the licence cost implication, and a clear recommend / do-not-recommend with three supporting reasons.

## Test it

You can show the pipeline chart with a stated total value, an activated forecast with roll-up columns, an active sequence connected to at least one record, a completed standard-vs-premium comparison table, and a one-page written investment recommendation with three supporting reasons.

---

**Printable instructions:** [`lab-06-instructions.pdf`](lab-06-instructions.pdf)

Part of [Microsoft Dynamics 365 Fundamentals (CRM) (MB-910)](https://www.tertiarycourses.com.sg/wsq-microsoft-dynamics-365-fundamentals-crm-mb-910.html) · WSQ Course Code TGS-2023040481 · Tertiary Infotech Academy Pte Ltd (UEN 201200696W)
