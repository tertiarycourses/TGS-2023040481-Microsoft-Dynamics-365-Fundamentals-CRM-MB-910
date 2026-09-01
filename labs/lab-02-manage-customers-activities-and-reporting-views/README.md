# Lab 2 — Manage Customers, Activities and Reporting Views

> **Topic 02:** Shared Activities and Integration Options  ·  **Estimated time:** 60 minutes

**Objective:** Describe shared activities and integration options: accounts and contacts, activities, search and filters, views, charts and dashboards.

## Scenario

Contoso Coffee Singapore is onboarding a new B2B customer. You create the account and its contacts, log the full set of activities on the timeline, then build the reporting layer your manager needs: a filtered personal view via Advanced Find, a chart from that view, and a dashboard combining both. Finally you export to Excel and confirm the Outlook and Teams integration points.

## What you'll produce

An Account with 3 related Contacts, 4 completed/open activities on the timeline, a saved personal view, a chart, a personal dashboard, and a dynamic Excel export.

**Tools:** Dynamics 365 Sales Hub, Dataverse, Advanced Find, Excel, Microsoft Teams, Outlook

## Workflow

1. Create the account and its related contacts
2. Log phone, task, email and appointment activities
3. Build a filtered personal view with Advanced Find
4. Create a chart and a personal dashboard from that view
5. Export to Excel and check Teams/Outlook integration

## Mock data

| File | Rows | Columns |
|---|---|---|
| [`data/accounts.csv`](data/accounts.csv) | 3 | Account Name, Main Phone, Website, Street 1, City, Postal Code, Country, Industry, Annual Revenue (SGD) |
| [`data/contacts.csv`](data/contacts.csv) | 3 | First Name, Last Name, Job Title, Business Phone, Email, Company Name |

## Step-by-step

1. Open the Dynamics 365 Sales Hub. In the left navigation under Customers, select Accounts, then choose New on the command bar.
2. Create the account using row 1 of data/accounts.csv: Account Name 'Marina Bay Roasters - <your initials>', Main Phone '+65 6555 0181', Website 'marinabayroasters.example.sg', Address 1: Street 1 '12 Marina Boulevard', City 'Singapore', ZIP/Postal Code '018980', Country/Region 'Singapore'. Select Save.
3. With the account open, find the Contacts sub-grid on the form (or the Related tab > Contacts). Select the + (New Contact) icon and create the three contacts from data/contacts.csv, ensuring Company Name is set to your new account each time.
4. Contact 1: First Name 'Priya', Last Name 'Raman', Job Title 'Procurement Manager', Business Phone '+65 6555 0182', Email 'priya.raman@marinabayroasters.example.sg'. Save and Close. Repeat for contacts 2 and 3 from the CSV.
5. Return to the account record and open the Timeline. Select the + icon > Phone Call. Set Subject to 'Discovery call - <your initials>', set the Call To field to Priya Raman, and choose Save and Close.
6. On the Timeline, hover over the phone call and select the check-mark icon to mark it complete, then select Close on the Close Phone Call dialog. Confirm the activity now shows as Closed.
7. Add a Task from the Timeline: Subject 'Send wholesale price list - <your initials>', Due date = 3 days from today. Save and Close. Leave this one open so you have both open and completed activities.
8. Add an Appointment from the Timeline: Subject 'On-site tasting session - <your initials>', set a Start Time next week and a 1-hour Duration, and add Priya Raman as a Required Attendee. Save and Close.
9. Add an Email activity from the Timeline: Subject 'Welcome to Contoso Coffee - <your initials>', To = Priya Raman. Note that you can save it as a draft without sending. Save and Close.
10. Test filtering versus search. In the Accounts list, use the column header filter on City to show only Singapore accounts. Then use the global search box at the top and search for 'Marina' — note it returns matches across multiple tables (accounts, contacts, activities). Record the difference between filter and search in your worksheet.
11. Open Advanced Find (the funnel icon on the command bar, or Settings > Advanced Find). Set Look for = Accounts. Add the criteria: City equals Singapore AND Created On is Last 7 Days. Select Results to preview.
12. In Advanced Find, choose Save As and name the view 'Singapore accounts this week - <your initials>'. This becomes a personal view available in the Accounts view selector.
13. Go to Accounts and switch the view selector to your saved personal view. On the command bar select Show Chart, then choose an existing chart such as Accounts by Industry. Note the chart is interactive: click a segment and the list filters to it.
14. Create your own chart: from the Accounts list select the chart pane, then New Chart. Set the legend (series) to Count of Account and the horizontal axis to City. Name it 'Accounts by city - <your initials>' and Save.
15. Build a dashboard. In the left navigation select Dashboards, then New > Dynamics 365 Dashboard, and choose a 2-column layout. Add one chart component (your new chart) and one list component (your saved personal view). Name it 'CRM overview - <your initials>' and Save, then Close.
16. Export to Excel. Return to Accounts with your personal view selected, choose Export to Excel > Dynamic Worksheet, select the columns to include and download. Open the file and note it keeps a live link back to Dataverse — a static worksheet would not.
17. Confirm the integration points: in Settings > Advanced Settings > Dynamics 365 App for Outlook, note the deployment status. In Microsoft Teams, note that the Dynamics 365 app can pin a record or view into a channel tab. Record both in your worksheet — no configuration change is required.

## Test it

Your account shows 3 contacts and 4 timeline activities (one completed phone call, one open task, one appointment, one email). Your personal view returns the account, your chart renders from that view, your dashboard shows both the chart and the list, and your dynamic Excel export opens with the account row present.

---

**Printable instructions:** [`lab-02-instructions.pdf`](lab-02-instructions.pdf)

Part of [Microsoft Dynamics 365 Fundamentals (CRM) (MB-910)](https://www.tertiarycourses.com.sg/wsq-microsoft-dynamics-365-fundamentals-crm-mb-910.html) · WSQ Course Code TGS-2023040481 · Tertiary Infotech Academy Pte Ltd (UEN 201200696W)
