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