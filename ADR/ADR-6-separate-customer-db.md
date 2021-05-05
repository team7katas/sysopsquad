## Title: 
ADR-6: Use separate customer database

## Status: 
Proposed

## Context: 
Improve performance, availability and scalability of customer-facing services.

## Decision: 
By storing customer data separately from the operational data we ensure that maintenance of the operational database will not affect the customer-facing service. Additional, decoupling customer data from the rest of the system improves extensibility. Also customers don't need to access all the information stored in the operational database so we can filter out unnecessary data.

## Consequences: 

We need to keep in sync customer billing information (address, credit cards etc) between customer database and the rest of the system.
