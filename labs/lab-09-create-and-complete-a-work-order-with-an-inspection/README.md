# Lab 9 — Create and Complete a Work Order with an Inspection

> **Topic 09:** Explore Dynamics 365 Field Service  ·  **Estimated time:** 55 minutes

**Objective:** Explore Dynamics 365 Field Service: field service use cases, the work order lifecycle, inspections and the Field Service mobile app.

## Scenario

A Contoso customer's espresso machine has failed on site. You create the work order with its incident type, products and services, attach a digital inspection the technician must complete, then drive the work order through its full status lifecycle from Open–Unscheduled to Closed–Posted, reviewing the mobile experience the technician would actually use.

## What you'll produce

A work order with an incident type, service tasks, products and services, a published inspection attached and completed, driven through every lifecycle status to Closed–Posted.

**Tools:** Dynamics 365 Field Service, Dataverse, incident types, inspections, Field Service mobile app

## Workflow

1. Create the work order and set its incident type
2. Add service tasks, products and services
3. Build and attach the digital inspection
4. Progress the work order through its statuses
5. Review the mobile technician experience

## Mock data

| File | Rows | Columns |
|---|---|---|
| [`data/work-orders.csv`](data/work-orders.csv) | 5 | Work Order Summary, Service Account, Primary Incident Type, Work Order Type, Priority, Service Territory, Promised From, Promised To |
| [`data/work-order-tasks.csv`](data/work-order-tasks.csv) | 8 | Work Order, Service Task, Estimated Duration (min), Sequence |
| [`data/inspection-questions.csv`](data/inspection-questions.csv) | 5 | Question, Type, Required, Notes |

## Step-by-step

1. Open the Dynamics 365 Field Service application. Select Work Orders from the Scheduling section of the left navigation, then choose New on the command bar.
2. Complete the work order from row 1 of data/work-orders.csv: Service Account 'Marina Bay Roasters' (or Adventure Works in the Microsoft sample data), Primary Incident Type 'Espresso machine not powering on', Work Order Type 'Service', Price List 'Default price list', Taxable 'No'. Select Save.
3. If the incident type does not exist, create it first: Settings > Incident Types > New. Name it 'Espresso machine not powering on', set an Estimated Duration of 2 hours, and add the required Characteristics (skills) 'Espresso equipment certified'. Save, then return to the work order and select it.
4. Note the Work Order Number the system generated and write it down — you will need it in Lab 10. Note also that the System Status is 'Open - Unscheduled': the work is defined but nobody is booked to do it yet.
5. Open the Settings tab of the work order. Set the Service Territory (for example 'Singapore Central' or 'WA' in the sample data). Under Preferences set Time From Promised to today at 9:00 AM and Time To Promised to today at 11:00 AM — this is the window you promised the customer.
6. Confirm the Service Address on the work order carried across from the service account, and that the geo-coded Latitude and Longitude are populated — the schedule board and the schedule assistant need them to calculate travel.
7. Open the Tasks tab and add the service tasks from data/work-order-tasks.csv: 'Verify mains power and RCD', 'Inspect boiler pressure switch', 'Test power-on sequence'. Set an estimated duration on each. These tell the technician what to do.
8. Open the Products tab and add one product the technician may need (for example a replacement pressure switch), setting its Quantity and marking it as Estimated. Open the Services tab and add a labour service with its estimated duration and unit price.
9. Build the inspection. Go to Settings > Inspections (or Field Service Settings > Inspections) and select New. Name it 'Espresso machine safety inspection - <your initials>'.
10. In the inspection designer, drag in these questions from data/inspection-questions.csv: (1) 'Is the mains supply within tolerance?' as a Yes/No question, (2) 'Boiler pressure reading (bar)' as a Number question, (3) 'Photograph of the damaged component' as a File/Photo question, (4) 'Is the unit safe to return to service?' as a Yes/No question, and (5) 'Technician notes' as a Text question.
11. Save the inspection and select Publish. Note that an inspection must be published before it can be attached to work — and that publishing creates a version, so later edits produce a new version rather than changing history.
12. Attach the inspection to the work: open the incident type you used and add the published inspection to it, so every work order of this incident type carries the inspection automatically. Alternatively add it directly to the work order's service task.
13. Now drive the lifecycle. On the work order set the System Status to 'Open - Scheduled' (in Lab 10 you will do this properly by booking a resource — for now set it manually to observe the status behaviour).
14. Set the System Status to 'Open - In Progress' to represent the technician arriving and starting work. Note that the Actual Arrival Time is recorded.
15. Complete the inspection as the technician would: open the work order's service task, open the attached inspection, answer all five questions, and Save. Confirm the responses are stored against the work order.
16. Set the System Status to 'Open - Completed'. Record the Actual Duration and mark the service tasks as complete. Note that 'Completed' means the work is done but not yet reviewed and invoiced.
17. Set the System Status to 'Closed - Posted'. This is the final state: the work order is reviewed, its products and services are posted, and it becomes read-only. Record all six statuses and what each means in your worksheet.
18. Review the mobile experience. Open the Dynamics 365 Field Service mobile app (or the documentation walkthrough) and note what the technician sees: the day's booking list, the work order details, the customer asset history, the guided inspection, photo capture, parts used, customer signature, and offline capability when there is no signal.
19. Record in your worksheet the three field service metrics this process improves: first-time fix rate, on-time arrival and travel time.

## Test it

Your work order carries an incident type, three service tasks, at least one product and one service, and a published inspection with all five questions answered. You can list the six work order statuses in order and show your work order at 'Closed - Posted'.

---

**Printable instructions:** [`lab-09-instructions.pdf`](lab-09-instructions.pdf)

Part of [Microsoft Dynamics 365 Fundamentals (CRM) (MB-910)](https://www.tertiarycourses.com.sg/wsq-microsoft-dynamics-365-fundamentals-crm-mb-910.html) · WSQ Course Code TGS-2023040481 · Tertiary Infotech Academy Pte Ltd (UEN 201200696W)
