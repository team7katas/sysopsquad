## Title: 
ADR-7: Analytics/reporting database

## Status: 
Proposed

## Context: 
Improve performance and availability of operational services.

## Decision: 
The motivation here is basically the same as for customers, see [ADR-6](ADR-6-separate-customer-db.md).

Report generation is usually a heavy process and affect the operational system significantly, so it is reasonable to store reporting related data in a separate database.

Also, maintenance work of the administration database (reporting, billing, etc) may affect effectiveness of the expert work. Experts need to access assigned tickets and knowledge base quickly and any time of the working day.

Note that billing information is not required during operation so we can keep it on the analytics database and offload the operational database.

## Consequences: 

We need to keep in sync reporting data.
