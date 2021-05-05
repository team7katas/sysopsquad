## Title: 
ADR-6: Use separate expert database

## Status: 
Proposed

## Context: 
Improve performance and availability of expert services.

## Decision: 
The motivation here is basically the same as for customers, see [ADR-6](ADR-6-separate-customer-db.md).

Maintenance of the administration data (reporting, billing, users etc) may affect effectiveness of the expert work. Experts need to access assigned tickets and knowledge base quickly and any time of the working day.

## Consequences: 

We need to keep in sync ticket assignments.
