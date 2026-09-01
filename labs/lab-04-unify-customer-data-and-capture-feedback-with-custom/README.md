# Lab 4 — Unify Customer Data and Capture Feedback with Customer Voice

> **Topic 04:** Customer Insights – Data and Customer Voice  ·  **Estimated time:** 45 minutes

**Objective:** Describe Dynamics 365 Customer Insights – Data and Dynamics 365 Customer Voice: unified profiles, measures, segments and enterprise feedback management.

## Scenario

Contoso's loyalty data, e-commerce orders and CRM contacts describe the same people under different keys. You walk the Customer Insights – Data unification pipeline to produce one profile per customer, define a lifetime-value measure and a high-value segment, then build and distribute a Customer Voice satisfaction survey and read the results. This gives you the customer insight LO4 asks you to draw.

## What you'll produce

A unified customer profile set from three sources, a customer lifetime-value measure, a high-value segment, and a published Customer Voice survey with a satisfaction metric.

**Tools:** Dynamics 365 Customer Insights – Data, Dataverse, Dynamics 365 Customer Voice, Power BI

## Workflow

1. Ingest the three source data sets
2. Map, match and merge to unified profiles
3. Define activities and a lifetime-value measure
4. Build a high-value segment from the measure
5. Create, send and analyse a Customer Voice survey

## Mock data

| File | Rows | Columns |
|---|---|---|
| [`data/ci-crm-contacts.csv`](data/ci-crm-contacts.csv) | 8 | ContactId, FullName, Email, Phone, City, SignupDate |
| [`data/ci-loyalty.csv`](data/ci-loyalty.csv) | 6 | LoyaltyId, FullName, Email, Phone, Tier, PointsBalance |
| [`data/ci-ecommerce-orders.csv`](data/ci-ecommerce-orders.csv) | 10 | OrderId, Email, OrderDate, OrderAmount, Channel |

## Step-by-step

1. Open Dynamics 365 Customer Insights – Data (https://home.ci.dynamics.com). If your tenant has no Customer Insights licence, use the guided demo environment or the trainer's shared environment — the pipeline stages are identical.
2. Select Data > Data sources > Add data source. Choose Text/CSV (or Upload file) and import data/ci-crm-contacts.csv. Name the source 'CRM contacts'. Review the inferred column data types and set ContactId as a text key.
3. Repeat the import for data/ci-loyalty.csv (name it 'Loyalty') and data/ci-ecommerce-orders.csv (name it 'Ecommerce orders'). You now have three sources describing overlapping people under different identifiers.
4. Select Data > Unify > Source fields (Map). Choose the tables to unify: CRM contacts and Loyalty. For each, select the primary key (ContactId, LoyaltyId) and map the shared semantic fields: FullName -> Person.Name, Email -> Person.Email, Phone -> Person.Phone.
5. Move to the Duplicate records step. For the CRM contacts table, add a deduplication rule on Email (Exact match) so the same email is never counted twice. Run it and review how many duplicates were collapsed.
6. Move to the Match conditions step. Set CRM contacts as the primary table. Create a match rule: CRM contacts.Email = Loyalty.Email, Exact match, normalised to lower case. Add a second, lower-precision rule on FullName + Phone as a fallback.
7. Move to the Merge (Unified customer fields) step. Where both sources supply a name, set the winner order to prefer CRM contacts. Exclude any field you do not want on the profile. Then select Save and Run to build the unified profiles.
8. When the run finishes, select Customers and open one unified profile. Confirm you can see the merged attributes and the source records that contributed to it. Record the total unified profile count versus the sum of the source rows — the difference is what unification removed.
9. Select Data > Activities > New activity. Choose the Ecommerce orders table, set the primary key to OrderId, set the relationship to the unified customer, set the Activity type to Purchase, and set the timestamp field to OrderDate and the value field to OrderAmount. Run the activity.
10. Select Insights > Measures > New > Build your own. Add the Ecommerce orders OrderAmount field, choose the Sum aggregation, and set the dimension to Customer ID so the result is per-customer. Name the measure 'Customer lifetime value - <your initials>' and Run it.
11. Select Insights > Segments > New > Build your own. Add the condition: your 'Customer lifetime value' measure is greater than 500. Name the segment 'High value customers - <your initials>', Save and Run, then record the member count.
12. Now capture feedback. Open Dynamics 365 Customer Voice (https://customervoice.microsoft.com) and select New project > From blank (or use the Customer satisfaction template).
13. Name the project 'Cold brew satisfaction - <your initials>'. In the survey designer add: (1) a Rating question 'How satisfied were you with your order?' using a 5-point scale, (2) a Net Promoter Score question, and (3) a free-text question 'What could we do better?'.
14. Apply survey best practice: keep it short, order the questions logically, and set clear expectations in the invitation text. Use Preview to test the survey on desktop and mobile before you distribute it.
15. Select Send. Review the four distribution options — Email, Link, QR code and Embed. Choose Link, copy the survey URL, and submit at least three responses yourself using different rating values so you have data to analyse.
16. Open the Report tab. Read the satisfaction metric summary and the NPS breakdown into Promoters, Passives and Detractors. Note where the responses are stored — the survey response is a Dataverse row, so it can trigger a journey or appear on a service dashboard.
17. Record in your worksheet: unified profile count, lifetime-value measure result for one customer, high-value segment size, and your survey's average satisfaction score and NPS.

## Test it

You can show a unified profile that merges at least two source records, a lifetime-value measure with a per-customer result, a high-value segment with a member count, and a Customer Voice report showing an average satisfaction score and an NPS from at least three responses.

---

**Printable instructions:** [`lab-04-instructions.pdf`](lab-04-instructions.pdf)

Part of [Microsoft Dynamics 365 Fundamentals (CRM) (MB-910)](https://www.tertiarycourses.com.sg/wsq-microsoft-dynamics-365-fundamentals-crm-mb-910.html) · WSQ Course Code TGS-2023040481 · Tertiary Infotech Academy Pte Ltd (UEN 201200696W)
