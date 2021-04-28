## Title: 
Handling the problem tickets separately, Isolating from the rest of the system.

## Status: 
Proposed

## Context: 
- System hangs when there is load and there is spike in usage
- not always available for call based or web based 
- system does not respond when entering problem tickets



Decision: 
 - Create a micro service for entering the tickets into the system
 - As this is the part that call center and users face when registering complaints, taking this part away would isolate it from the rest of the system.
 - Because of micro service the load due to entering tickets can be handled as this part is scale-able. 
 
 

## Consequences: 
- database is split (bounded context) 
