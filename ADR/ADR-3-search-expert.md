## Title: 
Ticket Processor: a separate component for expert assignment

## Status: 
Proposed

## Context: 
- Wrong experts are assigned.
- Often times the wrong consultant shows up to fix something they know nothing about.

## Decision: 
 - A separate component that has access to expert profile to select the correct expert. 
 - The component has different availability and scalability requirements from the rest of the system. If ticket processing will be unavailable for a short period of time or will not find experts immediately, nothing critical will happen to the operations.
 - This component might be a subject to frequent changes due to the assignment rules and optimization.
 - It also needs access to monitor the problem ticket queue (see ADR#4) to pick one ticket and select the best expert based on location, problem and his experience (rating perhaps?).
 - As a separate component, testing of this functionality is easier. More emphasis is on testing as there are problems in assigning the expert correctly (match is incorrect). 
 

## Consequences: 
- Needs access to the expert profile information (could be a separate DB if micro service is chosen).
 
