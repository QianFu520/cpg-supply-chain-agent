# Decision Log

This document records important product and architecture decisions, including their reasoning and tradeoffs.

## DEC-001: Use a Fixed 14-Day Planning Window

**Status:** Accepted

### Decision

The MVP will identify stockout exceptions using a fixed 14-day planning window.

A stockout exception occurs when forecast demand over the next 14 days exceeds current inventory plus confirmed inbound inventory expected during the same period.

### Reason

A fixed window makes exception detection consistent, testable, and easier to evaluate during the MVP. Fourteen days provides enough time to consider inventory transfers or shipment expediting while keeping the initial scope manageable.

### Tradeoff

Real companies may use different planning windows based on product category, supplier lead time, or business priorities. Configurable planning windows can be added in a later version.

## DEC-002: Use Synthetic CPG Supply-Chain Data

**Status:** Accepted

### Decision

The project will use synthetic operational data representing products, distribution centers, inventory, demand forecasts, inbound shipments, suppliers, and transfer options.

### Reason

Proprietary CPG supply-chain data and enterprise-system access are not available. Synthetic data allows the project to create controlled, realistic scenarios with known causes and correct resolution options.

It also allows the creation of ground-truth cases for testing stockout detection and evaluating agent recommendations.

### Tradeoff

Synthetic data cannot reproduce every complexity, inconsistency, or distribution found in a real enterprise environment. The data-generation assumptions and project limitations will therefore be documented clearly.
