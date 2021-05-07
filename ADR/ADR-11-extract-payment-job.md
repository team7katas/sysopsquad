## Title: 
ADR-10: Extract payment processing into a separate component (Payment Job)

## Status: 
Proposed

## Context: 
Perform payment in the given time interval (monthly).

## Decision: 
Payment is a scheduled behavior. If implement this in an always-running service we will need to deal with time intervals calculation. And this code is needed just once per month.
By extracting it into a separate job we can leverage 3rd-party schedulers and offload this behavior from the operational stuff. Also, if any errors in payment processing, the job can easily be rerun when necessary.

## Consequences: 
The job will need access to the billing information.
