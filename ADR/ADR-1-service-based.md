## Title: 
ADR-1: Use Service-based architectural style as the basic style

## Status: 
Proposed

## Context: 
Choose overall architectural approach

## Decision: 
We discovered three main domain areas here:
 - customer-facing services, such as ticket submission and profile management;
 - expert services, such as knowledge base and ticket search;
 - administration services, such as reporting and billing management.

By using Service-based approach we can enable separate architectural characteristics for these domains. For example, customer-facing services have higher availability, scalability and performance requirements. Expert services also require high availability because if an expert will not be able to access the knowledge base, he might not be able to fix the problem. Scalability is not that critical here because number of experts obviously is not growing as the number of customers. And administration services may only require security where billing operations occur.

Thus, the Service-based approach provides good fault-tolerance, scalability, and agility possibilities here and with no cost overhead as in Microservices.

## Consequences: 
This may require splitting the database.
