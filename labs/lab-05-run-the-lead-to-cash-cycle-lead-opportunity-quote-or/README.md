# Lab 5 — Run the Lead-to-Cash Cycle: Lead, Opportunity, Quote, Order

> **Topic 05:** Explore Dynamics 365 Sales  ·  **Estimated time:** 60 minutes

**Objective:** Explore Dynamics 365 Sales: lead qualification, opportunity management, quotes, orders and invoices, and business process flows.

## Scenario

Suzanne Burke of Contoso - Washington has enquired about new espresso equipment. You take that enquiry through the entire sales lifecycle: capture the lead, work the Lead to Opportunity business process flow, qualify it into an opportunity, add products from the catalog, generate a quote, activate and win it, convert to an order and raise the invoice. This is the LO1/LO3 backbone of the course.

## What you'll produce

A qualified lead, an opportunity with product line items and estimated revenue, an activated and won quote, a sales order and an invoice — with the business process flow advanced to Close.

**Tools:** Dynamics 365 Sales Hub, Dataverse, business process flows, product catalog, quotes, orders, invoices

## Workflow

1. Create the lead and complete the Qualify stage
2. Log activities and qualify into an opportunity
3. Add catalog products and estimated revenue
4. Create, activate and win the quote
5. Convert to an order and generate the invoice

## Mock data

| File | Rows | Columns |
|---|---|---|
| [`data/leads.csv`](data/leads.csv) | 4 | Topic, First Name, Last Name, Job Title, Business Phone, Email, Company Name, City, Est. Budget (SGD), Purchase Timeframe |
| [`data/products.csv`](data/products.csv) | 5 | Product ID, Name, Unit Group, Default Unit, List Price (SGD), Description |

## Step-by-step

1. Open the Dynamics 365 Sales Hub. Under Sales in the left navigation select Leads, then choose the My Open Leads view and select New on the command bar.
2. Create the lead from row 1 of data/leads.csv: Topic 'Looking for New Equipment - <your initials>', First Name 'Suzanne', Last Name 'Burke', Job Title 'CFO', Business Phone '888 555-8715', Email 'suzanne@contososample.com', Company Name 'Contoso - Washington'. Select Save and leave the record open.
3. Note the Lead to Opportunity Sales Process business process flow across the top of the form. Select the Qualify stage to open its flyout and complete it: Purchase Timeframe 'This Quarter', Estimated Budget '25000', Purchase Process 'Individual', Identify Decision Maker 'Completed'.
4. Scroll to the Timeline in the middle of the form. Select the + icon and choose Phone Call. Set the Subject to 'Initial phone call - <your initials>' and leave the other fields as they are. Select Save and Close.
5. On the Timeline, hover over the phone call activity and select the check-mark icon to close it, then select Close on the dialog. The activity now shows as Closed — a completed qualification touch.
6. On the command bar select Qualify. Dynamics 365 creates the related Account, Contact and Opportunity records and advances the business process flow to the Develop stage. If prompted about creating records, accept the defaults.
7. You are now on the new Opportunity. Confirm the Contact is Suzanne Burke and the Account is Contoso - Washington. Set the Est. Close Date to the end of next month and the Purchase Timeframe to This Quarter. Save.
8. Add products. On the opportunity, open the Product Line Items sub-grid (Products tab) and select + New Opportunity Product. Choose Existing Product, pick a product from the catalog, set Quantity to 2, and Save and Close. Add a second line item the same way.
9. If your environment has no product catalog entries, create them first: Settings > Advanced Settings > Product Catalog > Products, and add the two items from data/products.csv with the Default Price List. Publish each product before it can be added to an opportunity.
10. Note that the opportunity's Est. Revenue is now calculated from the line items (System Calculated). Switch it to User Provided and enter 25000 if you want to override it — record which method your organisation would use and why.
11. Complete the Develop stage of the business process flow: set Identify Stakeholders and Identify Competitors to Completed. Open the Related tab and add one Stakeholder (Suzanne Burke, role Decision Maker) and one Competitor.
12. Advance to the Propose stage. On the command bar select Create Quote (or, from the Quotes sub-grid, + New Quote). The quote inherits the account, contact, price list and product line items from the opportunity.
13. On the quote, set the Name to 'Espresso equipment quote - <your initials>', confirm the line items carried across, and check the totals: Detail Amount, Discount, Pre-Freight Amount, Freight Amount and Total Amount. Save.
14. Select Activate Quote on the command bar. The quote becomes read-only — this is the version you would send to the customer. Note that you must Revise the quote to change it, which creates a new revision.
15. Select Create Order (or Close Quote as Won). On the Create Order dialog, tick Close Opportunity and set the status. This converts the quote into a Sales Order and marks the opportunity Won.
16. On the new Order, confirm the line items and Total Amount carried across. Set the Requested Delivery Date to two weeks from today. Save. Note the Order is the customer's commitment to buy.
17. Select Create Invoice on the order command bar. On the Invoice, confirm the line items and total. Note the Due Date field. Save.
18. Mark the invoice as paid: on the command bar select Invoice Paid, and choose Complete (paid in full) rather than Partial. Record the difference between the two options in your worksheet.
19. Return to the Opportunity and confirm the business process flow has reached Close and the opportunity status is Won with the actual revenue recorded. Take a screenshot of the full record chain as evidence.

## Test it

You can trace one unbroken chain: Lead (Qualified) -> Opportunity (Won) -> Quote (Won) -> Order -> Invoice (Paid), with the same two product line items and totals carried through, and the Lead to Opportunity business process flow advanced to the Close stage.

---

**Printable instructions:** [`lab-05-instructions.pdf`](lab-05-instructions.pdf)

Part of [Microsoft Dynamics 365 Fundamentals (CRM) (MB-910)](https://www.tertiarycourses.com.sg/wsq-microsoft-dynamics-365-fundamentals-crm-mb-910.html) · WSQ Course Code TGS-2023040481 · Tertiary Infotech Academy Pte Ltd (UEN 201200696W)
