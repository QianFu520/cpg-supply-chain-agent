# Problem Definition

## Project

CPG Supply Chain Exception Resolution Platform

## Problem Statement

A supply-chain planner selects a stockout exception. The AI agent investigates the cause using inventory, demand-forecast, supplier, and transfer data; checks company policies; and produces a structured resolution recommendation for human approval.

## Primary User

A supply-chain planner responsible for investigating and resolving potential stockouts.

## Stockout Exception Definition

A stockout exception is generated when projected demand is expected to exceed available and incoming inventory within a defined planning period, creating a risk that the product will become unavailable at a distribution center.

For the MVP, the planning period is fixed at 14 days.

A stockout exception occurs when:

**Forecast demand over the next 14 days > Current inventory + Confirmed inbound inventory over the next 14 days**

## Data Source

The project will use synthetic CPG supply-chain data because proprietary company data is not available.

The synthetic data will represent realistic products, distribution centers, inventory levels, demand forecasts, inbound shipments, suppliers, and transfer options. It will include intentionally created scenarios such as demand spikes, shipment delays, inventory shortages, and excess inventory at nearby distribution centers.

The data, assumptions, and limitations will be clearly documented. The project will not claim that the data came from a real company.

## Exception Generation

The application will calculate stockout exceptions from the synthetic operational data rather than using a pre-existing exception dataset.

For each product and distribution center, the system will compare:

**Forecast demand over the next 14 days > Current inventory + Confirmed inbound inventory over the next 14 days**

If forecast demand exceeds available and incoming inventory, the system will create a stockout exception.

The exception will include the product, location, projected shortfall, expected stockout date, severity, and estimated business impact.
## Investigation Input

The investigation begins when a supply-chain planner selects a stockout exception and requests an AI-assisted investigation.

The application sends the selected exception ID to the agent. The agent uses this ID to retrieve the relevant operational data through approved tools.



## MVP Scope

The first version will handle stockout exceptions within a fixed 14-day planning window.

A stockout exception occurs when forecast demand over the next 14 days exceeds the sum of current inventory and confirmed inbound inventory during that period.

The MVP will allow a supply-chain planner to select an exception, initiate an AI-assisted investigation, review a structured resolution recommendation, and approve or reject the recommendation.

## Resolution Options

For the MVP, the agent can produce one of three final recommendation types:

1. Transfer inventory from another distribution center.
2. Expedite an existing inbound shipment from the supplier.
3. Escalate the exception for manual review when neither option is feasible or the available evidence is insufficient.

The agent will investigate the cause of the stockout, evaluate the feasibility, cost, risk, and policy compliance of the available options, and recommend the best-supported resolution.

The agent will not execute operational actions. Every recommendation must be reviewed and approved or rejected by an authorized human user.

## Agent Investigation Responsibilities

For each selected stockout exception, the agent will:

1. Retrieve the exception details.
2. Determine the likely cause using demand, inventory, and inbound-shipment data.
3. Evaluate whether inventory can be transferred from another distribution center.
4. Evaluate whether the existing inbound shipment can be expedited.
5. Check the applicable company policies.
6. Escalate the exception when data is missing, conflicting, or insufficient.

The agent must gather and evaluate sufficient evidence before producing a resolution recommendation.

## Structured Recommendation Output

After completing the investigation, the agent must return a structured recommendation containing:

1. Exception ID
2. Identified root cause
3. Recommended action: `transfer`, `expedite`, or `manual_review`
4. Action details, such as quantity, source location, or shipment
5. Supporting operational evidence
6. Relevant policy evidence
7. Expected business impact
8. Risks and assumptions
9. Reason for escalation, if applicable

The output must follow a validated schema so the application can reliably display, store, and evaluate the recommendation.

After receiving a valid recommendation, the application will create an approval record with an initial status of `pending`. The agent cannot approve its own recommendation or execute an operational action.

## Human Approval Workflow

Every agent recommendation requires review by an authorized supply-chain planner.

The application will:

1. Display the recommendation and its supporting evidence.
2. Allow the planner to approve or reject the recommendation.
3. Allow the planner to add a decision comment.
4. Store the decision, planner identity, timestamp, and recommendation version.
5. Prevent the agent from changing or bypassing the approval decision.

The approval status can transition from:

- `pending` to `approved`
- `pending` to `rejected`

For the MVP, the workflow ends after the decision is recorded. The application will not execute an actual inventory transfer or supplier action because it does not connect to a real enterprise resource planning system.

## MVP Limitations

The MVP has the following boundaries:

- Uses synthetic CPG data and fictional company policies.
- Handles only stockout exceptions.
- Uses a fixed 14-day planning window.
- Supports only `transfer`, `expedite`, and `manual_review` recommendations.
- Uses one supply-chain agent rather than a multi-agent system.
- Does not connect to a real ERP, supplier, or warehouse system.
- Does not execute approved operational actions.
- Does not initially support real-time data ingestion.

These limitations control the project’s business scope while allowing the implementation to demonstrate production-grade data, software, cloud, and AI-agent engineering.
