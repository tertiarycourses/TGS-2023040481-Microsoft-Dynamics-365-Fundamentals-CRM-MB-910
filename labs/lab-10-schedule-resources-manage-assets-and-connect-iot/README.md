# Lab 10 — Schedule Resources, Manage Assets and Connect IoT

> **Topic 10:** Field Service Scheduling Capabilities and Related Apps  ·  **Estimated time:** 55 minutes

**Objective:** Describe Field Service scheduling capabilities and related apps: resource and scheduling processes, the schedule board and schedule assistant, asset management and Connected Field Service.

## Scenario

The work order from Lab 9 must now be scheduled, and the customer's equipment tracked over its life. You book the work with the schedule assistant, work the schedule board as a dispatcher (rebook, substitute, move), build the customer asset hierarchy with its service history, and register an IoT device so an alert can raise a work order automatically. This completes LO3, LO4 and LO5.

## What you'll produce

A booked work order on the schedule board, a rebooked and substituted booking, a customer asset hierarchy with service history, and an IoT device registered against an asset with an alert that creates a work order.

**Tools:** Dynamics 365 Field Service, schedule board, schedule assistant, Resource Scheduling Optimization, customer assets, Connected Field Service, Azure IoT

## Workflow

1. Book the work order with the schedule assistant
2. Work the schedule board as a dispatcher
3. Rebook, substitute and move bookings
4. Build the customer asset hierarchy and history
5. Register the IoT device and raise an alert

## Mock data

| File | Rows | Columns |
|---|---|---|
| [`data/customer-assets.csv`](data/customer-assets.csv) | 5 | Asset Name, Account, Product, Serial Number, Parent Asset, Install Date |
| [`data/iot-components.csv`](data/iot-components.csv) | 7 | Component, What it is, Example in this lab |

## Step-by-step

1. Open the Dynamics 365 Field Service application and open the work order you created in Lab 9 (use the work order number you wrote down). Confirm its System Status is 'Open - Unscheduled'.
2. On the command bar select Book. This opens the Schedule Assistant. Note what it is doing: filtering bookable resources by the required characteristics (skills), the service territory, availability in the promised window, and proximity to the service address.
3. Review the ranked results. Each candidate shows the available time slot, the travel time and distance, and how well they match the requirement. Record why the top candidate ranked first.
4. Select a resource from the results. In the Create Resource Booking pane set the Start Time to the top of the next hour and the End Time to 2.5 hours later. Select Book & Exit.
5. Return to the work order and confirm the System Status has changed automatically to 'Open - Scheduled' and a Bookable Resource Booking now exists on the Bookings tab. Save and Close.
6. Open the Schedule Board from the left navigation. Orient yourself: the resource rows down the left, the time axis across the top, the bookings in the grid, the map on the right showing resource and job locations, and the requirements panel at the bottom.
7. In the requirements panel at the bottom, select the Unscheduled Work Orders tab. This is the dispatcher's queue of work that still needs a resource.
8. Take a second work order from data/work-orders.csv (create it if needed) and schedule it a different way: right-click it in the requirements panel and select Find Availability to open the schedule assistant, choose a resource, set the times and select Book & Exit.
9. Now schedule a third one manually: drag an unscheduled work order from the requirements panel directly onto a resource's row on the board at the time you want. Note that manual scheduling bypasses the assistant's constraint checking — record when that is acceptable and when it is risky.
10. Practise the three dispatcher moves. First, Move: drag an existing booking to a different time slot or a different day on the board, and confirm the booking's start time updated.
11. Second, Substitute Resource: right-click a booking, select Substitute Resource, then Find Substitution. Choose another qualified resource from the results. Confirm the booking transferred and the original resource's row is now free.
12. Third, Rebook: right-click a booking and select Reschedule (or Rebook), then pick a new slot from the schedule assistant. Record which of the three moves you would use for (a) a technician calling in sick, (b) a customer asking for a later time, (c) an emergency job that must displace a routine one.
13. Review automated scheduling. Open Resource Scheduling Optimization (if provisioned) or its documentation, and record what it adds: it runs on a schedule, optimises many bookings at once against objectives such as minimising travel and maximising working hours, and can re-optimise the day automatically.
14. Build the asset record. Select Customer Assets from the left navigation, then New. Create the parent asset from row 1 of data/customer-assets.csv: Name 'Espresso Machine E900 - Marina Bay', Account 'Marina Bay Roasters', Product 'Contoso Espresso Machine E900', Serial Number 'E900-SG-0417'. Save.
15. Create a child asset: New, Name 'Boiler assembly - E900-SG-0417', Account the same, and set the Parent Asset to the machine you just created. Save. Repeat for a second child, 'Grinder module - E900-SG-0417'. You now have an asset hierarchy — the sub-components of the machine.
16. Link the service history: open the parent asset and check the Work Orders sub-grid — the work order from Lab 9 should be associated (set the work order's Customer Asset field if it is not). Confirm you can now see every job ever done on this specific machine.
17. Record the four asset management capabilities in your worksheet: see all assets for a customer, identify where an asset is located, open work orders against an asset, and track the asset's full service history and hierarchy.
18. Set up Connected Field Service. Review the seven components in data/iot-components.csv: Customer Asset, Device Category, IoT Device, IoT Alert, IoT Device Command, Command Definition and Property Definition. Record what each one does.
19. Register a device: select IoT Devices > New. Name it 'E900-SG-0417 telemetry', set the Device ID, and set the Customer Asset to your parent asset. Save. In a production deployment this device is registered in Azure IoT Hub and its telemetry flows to Dynamics 365.
20. Simulate an alert: select IoT Alerts > New. Set the Alert Type to 'Anomaly', the Description to 'Boiler pressure exceeded 1.4 bar for 10 minutes', and the IoT Device to the device you registered. Save.
21. From the IoT Alert, select Create Work Order (or the equivalent command). Confirm a new work order is created and linked back to the alert and the asset. This is the closed loop: device -> telemetry -> alert -> work order -> technician — service dispatched before the customer noticed a problem.
22. Write your recommendation in data/field-service-recommendation.md: state which scheduling method (manual, assistant, optimisation) you would recommend for a 12-technician Singapore operation, and whether Connected Field Service is worth the investment, with three supporting reasons drawn from what you observed.

## Test it

Your Lab 9 work order is 'Open - Scheduled' with a booking visible on the schedule board; you have performed a move, a substitution and a rebook; your customer asset has two child assets and a linked work order history; and your IoT alert has generated a work order linked back to the asset.

---

**Printable instructions:** [`lab-10-instructions.pdf`](lab-10-instructions.pdf)

Part of [Microsoft Dynamics 365 Fundamentals (CRM) (MB-910)](https://www.tertiarycourses.com.sg/wsq-microsoft-dynamics-365-fundamentals-crm-mb-910.html) · WSQ Course Code TGS-2023040481 · Tertiary Infotech Academy Pte Ltd (UEN 201200696W)
