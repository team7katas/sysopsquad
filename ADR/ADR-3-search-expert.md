## Title: 
ADR-3: Separate service for ticket processing.

## Status: 
Proposed

## Context: 
- Wrong experts are assigned.
- Often times the wrong consultant shows up to fix something they know nothing about.

## Decision: 
 - Since this is area which is often reported to have problems, we want to isolate it from the rest of the system to reduce coupling and simplify testability and deloyability of this part.
 - Customer don't normally expect that their tickets are taken into processing right away, so robustness is over performance here. Hence we can keep a single instance of the service to ensure consistency.
 - This component might be a subject to frequent changes due to the assignment rules and optimization.

## Consequences: 
Needs access to the expert profile information (could be a separate DB if micro service is chosen).

