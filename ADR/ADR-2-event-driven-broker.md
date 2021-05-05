## Title: 
ADR-2: Use broker-based event-driven approach with guaranteed delivery for communicating between domains

## Status: 
Proposed

## Context: 
Provide robust communication between domains.

## Decision: 

The ticket workflow between domains here looks naturally pretty much as messaging, as illustrated in this BPMN diagram (circles are messages):

![Ticket workflow](../images/bpmn-ticket-workflow.jpg "Ticket workflow")


## Consequences: 
So even-driven approach must be a good fit. Let's consider the trade-offs and benefits:

 - eventual consistency in ticket state is fine between our domains (see ADR-1), because billing and reporting don't need actual ticket status right now; experts many not available right now so it's ok if the ticket remains in the queue some time;
 - process flow is relatively simple and sequential here with no parallel processing;
 - more difficult to test and debug; we can take if we have these:

 Benefits:
 - better scalability - what we need;
 - better agility and change management - what we need;
 - better adaptability and extensibility - we still need that;
 - better responsiveness and performance - we need this obe to.
