## Title: 
Handling the problem tickets separately, isolating from the rest of the system.

## Status: 
Proposed

## Context: 
- System hangs when there is load and there is spike in usage
- not always available for call based or web based 
- system does not respond when entering problem tickets

## Decision: 
 - Create a service for entering the tickets into the system that only captures the problem tickets and returns confirmation to the client/call center after registering the problem ticket into the system.
 - In case of spike in usage, more instances can be created. 
 - Since this is area which is often reported to have problems, we want to isolate it from the rest of the system to reduce the load on the rest of the system and also focus on making it more resilient.
 - it can be tested independently thus ensuring the reliability of the system.

## Consequences: 
- database is split (bounded context) 
