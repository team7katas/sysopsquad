## Title: 
ADR-9: Extract notification service

## Status: 
Proposed

## Context: 
Provide customer and expert notification capability to all domain areas.

## Decision: 
The service does not belong to any specific domain and is used by all domain services.

If notifications arrive a bit late to the destination due to maintenance or failure, this is not critical to the business operations, thus it does not require any specific considerations towards availability and performance.

## Consequences: 

Alternative would be having a separate notification service for each domain, but this will require to duplicate implementation in several places what will negatively impact on maintainability.
