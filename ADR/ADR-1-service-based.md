## Title: 
ADR-1: Use Service-based architectural style as the basic style

## Status: 
Proposed

## Context: 
Choose overall architectural approach

## Decision: 
We discovered three main domain areas here:
 - customer-facing services, such as ticket submission and profile management;
 - operational services, such as knowledge base and ticket workflow;
 - administration services, such as reporting and billing management.

By using Service-based approach we can enable separate architectural characteristics for these domains. For example, customer-facing services have higher requirements of availability, scalability and performance than the rest of the system. Operational services also require high availability because if an expert will not be able to access the knowledge base, he might not be able to fix the problem. Scalability is not that critical here because the number of experts is not growing as the number of customers. And administration services may only require security where billing operations occur.

Thus, the Service-based approach provides good fault-tolerance, scalability, and agility possibilities here and with no cost overhead as in Microservices.

## Consequences: 
This may require splitting the database.
