## Title: 
ADR-8: Use table-based synchronization of customer billing info

## Status: 
Proposed

## Context: 
Since we use a separate database for customer data ([ADR-6](ADR-6-separate-customer-db.md) we need to keep this data in sync with administration database where the billing stuff is running.

## Decision: 
Changing of the customer billing information is not an event that needs immediate reaction. This data will be used monthly by the payment service when it is time, so it is fine if this data will be silently replicated to the billing store.

## Consequences: 

Depending on the database vendor this can be implemented in a variety of ways. Some databases support table-based replication. In other cases it can be an ETL job that runs periodically.
