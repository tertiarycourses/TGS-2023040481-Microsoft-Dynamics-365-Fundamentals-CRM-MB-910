# Lab 1 — Navigate Dynamics 365 and Explore Dataverse

> **Topic 01:** Foundations of Dynamics 365 Customer Engagement Apps  ·  **Estimated time:** 45 minutes

**Objective:** Describe the foundations of Dynamics 365 customer engagement apps: Power Platform, Dataverse, the five CE apps and navigation.

## Scenario

You are a new CRM analyst at Contoso Coffee Singapore. Before you can advise on CRM investment you must know what is actually deployed. Sign in to the Power Platform admin centre, identify the environment and its Dataverse database, open the Sales Hub and Customer Service Hub apps, and map how the five customer engagement apps share one data store. You finish by recording an environment inventory your team can act on.

## What you'll produce

An environment inventory table (environment name, type, region, Dataverse URL, installed CE apps, security roles) plus an annotated navigation map screenshot set.

**Tools:** Power Platform admin center, make.powerapps.com, Dynamics 365 Sales Hub, Customer Service Hub, Dataverse

## Workflow

1. Sign in to the Power Platform admin center
2. Inspect the environment and its Dataverse database
3. Open the Sales Hub and switch apps from the app launcher
4. Explore Dataverse tables, columns and relationships
5. Record the environment inventory and navigation map

## Mock data

| File | Rows | Columns |
|---|---|---|
| [`data/environment-inventory.csv`](data/environment-inventory.csv) | 9 | Item, Value to record, Where to find it |

## Step-by-step

1. Open a browser and go to https://admin.powerplatform.microsoft.com. Sign in with the trainer-provided Microsoft 365 account (training<N>@tertiaryinfotech.onmicrosoft.com). Record your user name up to the @ symbol — this is your lab alias and you will prefix every record you create with it.
2. Select Environments in the left navigation. Note the environment Name, Type (Production / Sandbox / Trial), Region and State. Open the environment and copy its Environment URL — this is your Dataverse organisation URL.
3. In the environment detail page, look at the Dataverse section: note the database version, language and currency. Record the Dataverse database size. This one database is shared by every Dynamics 365 customer engagement app in the environment.
4. Select Resources > Dynamics 365 apps. List which customer engagement apps are installed (Sales, Customer Service, Field Service, Customer Insights, Project Operations) and their installed status. This is the deployment baseline for your inventory.
5. Go to https://make.powerapps.com and confirm the correct environment is selected in the top-right environment picker. Select Tables in the left navigation, then set the filter to All to see every Dataverse table, not just custom ones.
6. Open the Account table. Review the Columns tab: note the account name, primary contact, and the ownership model. Then open the Relationships tab and find the one-to-many relationship from Account to Contact — this is how a company links to its people.
7. Open the Contact table and find the Company Name (parentcustomerid) column. Confirm it is a Lookup to Account. Record this relationship: Account 1 -> N Contact.
8. Return to https://make.powerapps.com and select Apps. Note that the Dynamics 365 apps (Sales Hub, Customer Service Hub) are listed as Model-driven app types — Dynamics 365 CE apps ARE model-driven Power Apps.
9. Open the Dynamics 365 Sales Hub app. Explore the left navigation: note the area switcher at the bottom-left (Sales / Activities / Settings) and the groups within the Sales area (Customers, Sales, Collateral, Performance).
10. Select the app launcher (the waffle icon, top-left) and switch to the Customer Service Hub. Confirm that the Accounts and Contacts you see are the SAME records you saw in Sales Hub — one Dataverse, many apps.
11. In either app, select the Settings gear > Advanced Settings > Security > Users to view the security roles applied to your account. Record which roles you hold (e.g. Salesperson, Customer Service Representative).
12. Complete the environment inventory table in your lab worksheet (data/environment-inventory.csv) with the values you recorded, and save your navigation screenshots as evidence.

## Test it

You can state: the environment name and type, the Dataverse organisation URL, which CE apps are installed, at least two Dataverse tables and the Account-to-Contact relationship, and you can switch between two apps and show that the same Account record appears in both.

---

**Printable instructions:** [`lab-01-instructions.pdf`](lab-01-instructions.pdf)

Part of [Microsoft Dynamics 365 Fundamentals (CRM) (MB-910)](https://www.tertiarycourses.com.sg/wsq-microsoft-dynamics-365-fundamentals-crm-mb-910.html) · WSQ Course Code TGS-2023040481 · Tertiary Infotech Academy Pte Ltd (UEN 201200696W)
