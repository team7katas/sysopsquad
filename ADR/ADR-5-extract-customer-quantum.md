## ADR-5: Extract customer architectural quantum

## Status
Proposed

## Context
Improve responsiveness and availability of the customer-facing services.

As the business grows, the number of customers using the system grows as well, so we need to preserve performance characteristics while scaling up.

## Decision
The challenging thing here is that customers interact quite closely with the other parts of the system, specifically:

* **UC-2 support contracts**: customers need to choose from available support contracts while composing their support plans;
* **UC-2 billing info**: the system has to move credit card data into a secure place;
* **UC-3 ticket submission**: customers submit their tickets for processing by another part of system;
* **UC-4 survey submission**: customers will need to submit feedback surveys that are needed for analytics;
* **UC-7 receive invoices**: when get billed customers should receive invoices.

New support contracts, or support contract changes, are not the kind of an event that needs a reaction, thus we can leave it for a table-based replication. This can be a built-in database feature, or, in case we want to avoid this database level coupling, it can be an ETL job that runs periodically and synchronizes support contract information between quanta.

Since we don't store sensitive credit card information within the customer quantum (see [ADR-4](ADR/ADR-4-extract-billing-quanta.md)), we need move this information securely to the billing quantum. Doing this synchronously (via a REST API or a RPC call) will nullify our efforts on scalability and availability for the customer quantum, so we will leverage asynchronous messaging here.

The same for the ticket submission - we don't want to make our customer to wait for the ticket to be taken into processing, so this is simple fire and forget message.

Survey submission, on the other side, is not a kind of an event that needs an immediate reaction so table-based replication might work here. However, since feedback surveys are needed only for analytics, we don't need those surveys to be stored within the customer quantum so we can push them to the corresponding quantum asynchronously as well.

When the Payment job generates an invoice, it does not have to wait for the invoice to be sent to the customer. Or, if the Notification system is down (for maintenance, for example), we don't want any invoices to be missed; customers should eventually get their invoices. For this reason, we will use an persistent message queue for sending invoices between billing and customer quanta.

All together:

![Customer Quantum](../images/adr-5.jpg)

## Consequences
