# Lab 8 — Omnichannel, Supervisor Insights and Service Analytics

> **Topic 08:** Customer Service Capabilities and Related Apps  ·  **Estimated time:** 45 minutes

**Objective:** Describe Customer Service capabilities and related apps: Omnichannel for Customer Service, supervisor experiences, sentiment analysis, Customer Voice and service reporting.

## Scenario

Contoso's support team is moving from email-only to multi-channel support. You explore the Omnichannel agent workspace and its session model, review the supervisor's near-real-time dashboards and sentiment KPIs, read the historical analytics reports, and connect a Customer Voice post-resolution survey — then draw the performance insight LO4 asks for.

## What you'll produce

An Omnichannel agent workspace walkthrough, a supervisor insights review with recorded KPIs, a completed analytics report comparison, and a service performance insight statement.

**Tools:** Omnichannel for Customer Service, Customer Service workspace, Omnichannel Insights, Customer Voice, Power BI

## Workflow

1. Open the Customer Service workspace and review sessions
2. Explore the Omnichannel channels and productivity tools
3. Review supervisor dashboards and sentiment KPIs
4. Read the historical analytics reports
5. Connect Customer Voice and state the insight

## Mock data

| File | Rows | Columns |
|---|---|---|
| [`data/service-analytics.csv`](data/service-analytics.csv) | 7 | Management question, Which report answers it, Key metric, Action if it worsens |

## Step-by-step

1. Open the Customer Service workspace app (or Omnichannel for Customer Service if it is provisioned). Note the session-based layout: a session panel down the left, tabs across the top of each session, and the productivity pane on the right.
2. Open one of the cases you created in Lab 7 from the workspace. Note that it opens as a session with its own tabs, and that you can open a second case as a second session without losing the first — this is how an agent handles concurrent conversations.
3. Review the productivity pane on the right. Identify the Knowledge search pane, the Smart assist / Copilot suggestions area, and the Agent scripts pane. Record what each one gives the agent.
4. Explore the channels. Open the Customer Service admin center > Channels. List the channel types available: Chat (live chat for websites), SMS, Voice, Microsoft Teams, and social channels (Facebook, WhatsApp, LINE, WeChat), plus entity/record channels for email and cases.
5. Open a chat workstream (Channels > Chat, or Work streams). Review its configuration: the routing rules, the capacity profile, the work distribution mode (push or pick), and the attached bot if one is configured. Record how a conversation reaches an agent.
6. Review bot escalation. In the workstream, note where a Copilot Studio bot is attached and what happens on escalation — the human agent receives the full conversation transcript and customer context, so the customer does not repeat themselves.
7. Switch to the supervisor view. Open Omnichannel Insights (or the Customer Service historical analytics area). Open the real-time / ongoing conversations dashboard and note what a supervisor can see: ongoing conversations, waiting conversations, agent status and queue load.
8. Note the supervisor actions available on an ongoing conversation: monitor, assign, transfer and force-close. Record which action you would use when a conversation is going badly.
9. Open the Sentiment Analysis dashboard. Record the four sentiment KPIs: Average Sentiment Pulse, % Positive Sentiment, % Neutral Sentiment and % Negative Sentiment, plus Conversations with sentiment prediction. Note where the sentiment score comes from (real-time analysis of the customer's messages).
10. Explore the personalisation options on the dashboards: Manage report filters (adjust the time period, queue, channel or agent) and Manage report bookmarks (save a filtered state you return to). Apply a filter and save a bookmark.
11. Read the Customer Service historical analytics reports. Open each of the three and record one metric from each: Summary (case volume, resolution rate), Agent (cases handled, average handle time), and Case Topics (AI-clustered case themes).
12. Read the Omnichannel historical analytics reports. Open each of the five and record one metric from each: Conversation, Queue, Agent, Bot and Conversation Topics. Note what the Bot report tells you about deflection.
13. Complete the analytics comparison table in data/service-analytics.csv, filling in which report answers which management question.
14. Connect the feedback loop. In Customer Voice, open the project you created in Lab 4 (or create a short post-resolution survey with one CSAT rating question and one free-text question). Note the four distribution options and that survey responses are stored in Dataverse.
15. Record where the survey result surfaces: on the case or customer record, on the Customer Service dashboards, and as a trigger for a follow-up journey when a low score arrives.
16. Write your service performance insight in data/service-insight.md: state the three KPIs you would put on the team's dashboard, what each one tells you about performance, and one concrete action you would take if each moved in the wrong direction.

## Test it

You can describe the session model and name the three productivity-pane tools, list at least five Omnichannel channel types, state the four sentiment KPIs with a value or definition, name the three Customer Service and five Omnichannel historical reports, and produce a written insight statement naming three KPIs with an action for each.

---

**Printable instructions:** [`lab-08-instructions.pdf`](lab-08-instructions.pdf)

Part of [Microsoft Dynamics 365 Fundamentals (CRM) (MB-910)](https://www.tertiarycourses.com.sg/wsq-microsoft-dynamics-365-fundamentals-crm-mb-910.html) · WSQ Course Code TGS-2023040481 · Tertiary Infotech Academy Pte Ltd (UEN 201200696W)
