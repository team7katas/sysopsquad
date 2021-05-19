## Title: 
ADR-12: Offload operational concerns into API Gateways.

## Status: 
Proposed

## Context: 
At this point, we extracted 8 services. Now the question - how do we handle authentication and authorization? How do we ensure that front-ends access only services that they are permitted to? What about logging? Should we implement these things inside each service thus take a burden of code duplication? Or we can offload domain services from this operational stuff?

## Decision: 
API Gateways can come at hand here. It seems a good idea to have separate API Gateways for each domain quanta for the same reason we explain in [ADR-1](ADR/ADR-1-service-based.md) - they may require different architectural characteristics.

So what gateways do we need here? The first candidate is the billing silo, since this is the highest security risk and may to be isolated from the rest of the system as much as possible. The least thing we want that either admin staff or customer users gain access to somebody credit card data.  
Admin API operates with admin permissions so any intrusion here will make a high impact on the whole business.  
Customer API and Sysops API need different levels of availability and scalability here so this is another Gateway. And Mobile application may need more efficient data responses than web applications.

An important thing to notice that API Gateways should contain no domain logic. Remember, we are not building an ESB here. API Gateways should care exceptionally about security checks and operational concerns here.

## Consequences: 
Again, this adds complexity, because the number of services increases. We should pay careful attention while developing API Gateways to avoid performance bottlenecks and a single point of failure, so they need to be properly load-balanced.
API Gateways also require additional development cost and future maintenance.
