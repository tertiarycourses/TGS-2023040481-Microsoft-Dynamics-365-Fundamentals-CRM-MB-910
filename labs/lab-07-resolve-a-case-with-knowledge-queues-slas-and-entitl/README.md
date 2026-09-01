# Lab 7 — Resolve a Case with Knowledge, Queues, SLAs and Entitlements

> **Topic 07:** Explore Dynamics 365 Customer Service  ·  **Estimated time:** 60 minutes

**Objective:** Explore Dynamics 365 Customer Service: the case lifecycle, SLAs and entitlements, queues and routing, business process flows and knowledge management.

## Scenario

Alpine Ski House has received a damaged espresso machine. You author and publish the knowledge article that answers it, create the case, route it through a queue, watch the SLA clock, apply an entitlement, work the Phone to Case business process flow, attach the article and resolve the case. This is the complete service lifecycle behind LO1 and LO3.

## What you'll produce

A published knowledge article, a case routed through a queue with an SLA and an entitlement applied, advanced through all three BPF stages and resolved with the article linked.

**Tools:** Dynamics 365 Customer Service Hub, Dataverse, knowledge management, queues, routing rules, SLAs, entitlements

## Workflow

1. Author and publish the knowledge article
2. Create the case and set its customer and origin
3. Route it to a queue and apply the SLA and entitlement
4. Work the Phone to Case BPF and attach the article
5. Resolve the case and check the resolution record

## Mock data

| File | Rows | Columns |
|---|---|---|
| [`data/cases.csv`](data/cases.csv) | 5 | Case Title, Customer, Contact, Origin, Priority, Case Type, Subject, Description |
| [`data/knowledge-articles.csv`](data/knowledge-articles.csv) | 5 | Title, Keywords, Subject, Summary |

## Step-by-step

1. Open the Dynamics 365 Customer Service Hub. In the left navigation, switch the area to Service and select Knowledge Articles, then choose New on the command bar.
2. Author the article using row 1 of data/knowledge-articles.csv: Title 'Item Broken on Arrival - <your initials>', Keywords 'damaged, broken, shipping, replacement'. In the Content tab write the resolution steps: inspect and photograph the damage, log the courier reference, raise a replacement within 48 hours, and arrange collection of the damaged unit.
3. Save the article. Note the Article Public Number generated and the article's status (Draft) and stage on the knowledge lifecycle: Author -> Review -> Publish.
4. Open the Summary tab and set the Language. Then select Publish on the command bar. Set Publish Status to Published, choose to publish immediately, and confirm. Verify the article status is now Published — only published articles can be found by agents and customers.
5. Create the case. Select Cases from the Service section of the left navigation, then New Case on the command bar.
6. Complete the case from row 1 of data/cases.csv: Case Title 'Item arrived Damaged - <your initials>', Customer 'Alpine Ski House' (or Marina Bay Roasters if Alpine Ski House does not exist in your environment), Origin 'Phone', Priority 'High'. Select Save and leave the record open.
7. Examine the SLA. On the case form open the Related tab > SLA KPI Instances (or look for the First Response By and Resolve By fields on the form header). Note the countdown timer and the target time. If no SLA is applied, create one: Advanced Settings > Service Management > Service Level Agreements > New, add a First Response KPI with a 1-hour target, activate it and set it as the default.
8. Apply an entitlement. Open the Related tab > Entitlements on the customer account, or create one: Service Management > Entitlements > New, set the Customer, a Start and End date, Allocation Type 'Number of cases', Total Terms '10', and Activate it. Return to the case and set the Entitlement field. Note that the Remaining Terms decrement when the case is resolved.
9. Route the case to a queue. On the command bar select Save & Route (or Add to Queue). Choose an existing queue, or create one first: Service Management > Queues > New, name it 'Tier 1 support - <your initials>', type Private. Confirm the case now appears in that queue's items.
10. Open the queue (Service > Queues, and select your queue in the view picker). Select your case and choose Pick on the command bar to assign it to yourself — this is how an agent takes ownership of queued work.
11. Review the routing options in the environment: Service Management > Routing Rule Sets shows basic routing (rule items that direct cases to queues by criteria). Note where unified routing is configured instead (Customer Service admin center > Routing) and record the difference: basic routing sends to a queue; unified routing assigns to an agent using skills, capacity and presence.
12. Work the business process flow. On the case, note the Phone to Case Process across the top with its three stages: Identify, Research, Resolve. Select the Identify stage and set Find Contact to the account's primary contact. Close the flyout with the X.
13. On the case Timeline select the + icon > Phone Call. Set the Subject to 'Return call to customer - <your initials>' and leave the rest as is. Select Save and Close.
14. Select the Identify stage and choose Next Stage to advance to Research. Close the flyout.
15. On the right side of the case form, select the Knowledge (book) icon to open the knowledge search pane. Note that the case title is used automatically as the search text. Locate the 'Item Broken on Arrival' article you published.
16. Open the article in the pane and select the Link this article to the current record icon. Verify the text 'Linked to Case' appears. Note the other options: email the article to the customer, or copy its link.
17. Complete the phone call activity: on the Timeline hover over 'Return call to customer' and select the check-mark icon, then Close on the dialog. Verify it shows as Closed.
18. Select the Research stage and choose Next Stage to advance to Resolve. Close the flyout, then select Finish on the Resolve stage to complete the process flow.
19. On the command bar select Resolve Case. On the dialog set Resolution Type to 'Knowledge Article' (or Problem Solved), enter a Resolution description, note the Billable Time, and select Resolve.
20. Confirm the case status is now Resolved, that a Case Resolution activity appears on the timeline, and that the entitlement's Remaining Terms decreased by one. Record the SLA outcome (met or breached) in your worksheet.

## Test it

Your knowledge article is Published; your case was routed to a queue, picked, had an SLA and an entitlement applied, advanced through Identify -> Research -> Resolve, has the article shown as 'Linked to Case', and is Resolved with a Case Resolution activity on its timeline.

---

**Printable instructions:** [`lab-07-instructions.pdf`](lab-07-instructions.pdf)

Part of [Microsoft Dynamics 365 Fundamentals (CRM) (MB-910)](https://www.tertiarycourses.com.sg/wsq-microsoft-dynamics-365-fundamentals-crm-mb-910.html) · WSQ Course Code TGS-2023040481 · Tertiary Infotech Academy Pte Ltd (UEN 201200696W)
