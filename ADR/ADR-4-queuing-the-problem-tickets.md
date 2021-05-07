## Title: 
ADR-4: Queue the problem tickets.

## Status: 
Proposed

## Context: 
- Problem tickets are often lost
- Experts do not show up for the problem already entered into the system (see ADR #3)

## Decision: 
 - Place a queue between the problem ticket service and the rest of the system. this queue will move problem tickets into the system.
 - A part in the existing app will read queue, pick a problem ticket and assign an expert to it. 
 - other problem tickets are not lost as they are present in the queue waiting to be processed. The cause of usage spike is thus removed from the system and only the result of the usage spike i.e. problem tickets, are available for the system to process thus system is never over burdened
  
## Consequences: 
- A piece of code is required in current monolith that will pick one ticket at a time.
- rest of the system will not need many changes, we are only working on the points that cause spike in the system when a large number of tickets are entered into the system 
