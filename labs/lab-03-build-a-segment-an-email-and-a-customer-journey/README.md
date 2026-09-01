# Lab 3 — Build a Segment, an Email and a Customer Journey

> **Topic 03:** Dynamics 365 Customer Insights – Journeys  ·  **Estimated time:** 60 minutes

**Objective:** Describe Dynamics 365 Customer Insights – Journeys: segments, email marketing, customer journeys, lead generation, forms and events.

## Scenario

Contoso Coffee Singapore is launching a cold-brew range to its Singapore hospitality contacts. You build the targeting segment, design a marketing email with dynamic personalisation, wire both into a customer journey with a trigger and a conditional branch, then create the marketing form and event that capture the resulting leads. This is the full marketing framework the course's LO2 requires.

## What you'll produce

A live segment of Singapore hospitality contacts, a published marketing email, a running customer journey with a branch, a marketing form on a landing page, and an event with a registration record.

**Tools:** Dynamics 365 Customer Insights – Journeys, Dataverse, email designer, segment builder, event management

## Workflow

1. Create the audience segment and check its membership
2. Design and personalise the marketing email
3. Build the journey with a trigger and a branch
4. Publish the journey and verify it goes live
5. Create the marketing form and the event registration

## Mock data

| File | Rows | Columns |
|---|---|---|
| [`data/marketing-contacts.csv`](data/marketing-contacts.csv) | 12 | First Name, Last Name, Email, Company Name, City, Industry, Consent |

## Step-by-step

1. Open the Dynamics 365 Customer Insights – Journeys app. Use the area switcher at the bottom of the left navigation to confirm you are in the Real-time journeys area (not Outbound marketing).
2. Import the marketing contacts first. In the Sales Hub or Customer Service Hub, select Contacts, then Import from Excel on the command bar, and upload data/marketing-contacts.csv. Map the columns to First Name, Last Name, Email, Company Name, City and Industry, and complete the import.
3. Back in Customer Insights – Journeys, under Audience select Segments, then New segment > Build your own.
4. Name the segment 'SG hospitality contacts - <your initials>'. Set the target audience to Contact. Add the condition: Contact.City equals Singapore. Select Add attribute again and add AND Contact.Industry contains Hospitality.
5. Try the Copilot query assist if it is enabled: select the copilot icon and type 'contacts in Singapore who work in hospitality'. Compare the generated definition with the one you built by hand.
6. Select Save, then Go live (or Publish). Wait for the segment status to change to Live, then open the Members tab and confirm the expected contacts appear. Record the member count in your worksheet.
7. Under Channels select Emails, then + New. Choose a simple layout (or Start from blank).
8. Set the email Name to 'Cold brew launch - <your initials>'. Set the Subject line to 'Introducing our new cold brew range'. In the designer, drag a Text element onto the canvas and write a short opening paragraph.
9. Add personalisation: place your cursor in the greeting line, select the Personalization button, choose Contact > First Name, and insert it. Set a fallback value of 'there' so the email still reads correctly if the field is blank.
10. Drag a Button element onto the canvas. Set its text to 'Reserve a tasting' and set the link to your event or landing page URL (you will create the form in a later step — a placeholder URL is fine now).
11. Complete the required compliance elements: confirm the email includes a physical postal address and an unsubscribe/preference-centre link. Real-time marketing blocks publishing without them.
12. Select Check content (or Preview) to validate the email, fix any errors reported, then select Ready to send / Publish. Confirm the status shows Ready to send.
13. Under Engagement select Journeys, then + New journey. Choose Segment-based (start when a contact joins a segment), and select your 'SG hospitality contacts' segment as the audience. Name the journey 'Cold brew launch journey - <your initials>'.
14. On the journey canvas, the audience tile is already placed. Select the + below it and add your 'Cold brew launch' email as the first message tile.
15. Select + again and add a Wait tile. Set it to wait 2 days (or 5 minutes if you want to observe the journey run during the class).
16. Select + and add an If/then branch. Set the condition to 'Email was opened' on your cold-brew email. This creates a Yes path and a No path.
17. On the Yes path add an Action tile > Create a lead (or Sales activity), so an engaged contact becomes a lead for the sales team. On the No path add a second Message tile with a follow-up reminder email (you may reuse the same email for the lab).
18. Select Publish (Go live) on the command bar. Confirm the journey status changes to Live and note the audience count it reports.
19. Create the lead-capture form. Under Channels select Forms, then + New form. Choose the Landing page form type. Drag in the First Name, Last Name and Email fields, plus a Submit button. Name it 'Cold brew tasting signup - <your initials>' and select Save, then Publish. Copy the hosted form URL.
20. Create the event. Switch the area to Events (or open the Events app area). Select Events > + New. Set Name 'Cold brew tasting - <your initials>', a Start and End date next month, Venue 'Marina Bay Roasters', and set the Event registration to allow anonymous registration. Save.
21. On the event record, open the Agenda tab and add one Session: Name 'Cold brew method masterclass', with a start time inside the event window and a speaker of your choice. Save.
22. Publish the event (set the status to Live) and confirm the event website URL is generated. Record the segment member count, journey status and event URL in your worksheet.

## Test it

Your segment is Live with a non-zero member count; your email passes the content check and is Ready to send; your journey is Live and shows the audience -> email -> wait -> branch structure on the canvas; your form is published with a URL; and your event is Live with one session.

---

**Printable instructions:** [`lab-03-instructions.pdf`](lab-03-instructions.pdf)

Part of [Microsoft Dynamics 365 Fundamentals (CRM) (MB-910)](https://www.tertiarycourses.com.sg/wsq-microsoft-dynamics-365-fundamentals-crm-mb-910.html) · WSQ Course Code TGS-2023040481 · Tertiary Infotech Academy Pte Ltd (UEN 201200696W)
