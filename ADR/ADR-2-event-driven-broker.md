## Title: 
ADR-2: Use message queues with guaranteed delivery for ticket workflow

## Status: 
Proposed

## Context: 
As mentioned in [ADR-1](ADR-1-service-based.md), customer-facing services will require special considerations on availability and scalability with respect to the rest of the system. Similar requirements toward the expert-facing software, they need their sub-system to be highly available and provide a good response time than the rest of the system.
This makes an implication for decoupling these areas from one another.

## Decision: 
Using an asynchronous message queues between customer and Sysops services enables the following:
 - enables fire and forget ticket submission for the customer, so that customer does not have to wait for any ticket processing; hence we get very low response time;
 - same for Sysops Experts, they don't have to wait until the system finishes with ticket processing or report generation; while working on the field they just need to search for a ticket or a kb article;
 - enables independent scalability and availability of the corresponding quantums;

If look at the ticket workflow between domains, it looks naturally pretty much as messaging rather than query-response behavior as illustrated in this BPMN diagram (circles are messages):

![Ticket workflow](../images/bpmn-ticket-workflow.jpg "Ticket workflow")

Note that we should guarantee message delivery to the exact destination so this end-to-end queue-based messaging, not a topic-based publisher-subscriber communication.

## Consequences: 
Let's consider the trade-offs:
 - added complexity;
 - message queues can introduce a single point of failure so has to be load-balanced;
 - ticket workflow becomes more difficult for testing and debugging.

Since aforementioned qualities are critical to the business we accept these trade-offs.
