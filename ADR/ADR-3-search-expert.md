## Title: 
ADR-3: Extract ticket assignment into a separate batch processing job.

## Status: 
Proposed

## Context: 
The ticket assignment part seems to be a problematic one. Often times the wrong expert shows up to fix something they know nothing about. Sometimes, tickets never get assigned to an expert and lost forever. We need to come up with a robust solution to this problem.

## Decision: 

Since ticket assignment is a subject to frequent changes, it seems a good idea to make it a separate component thus improve modularity. 

One option is to make it a standalone service that reacts to ticket events and processes each new ticket separately. But this will imply significant limitations on the processing capabilities. What about ticket priorities? Tickets with a higher priority may need to be assigned first postponing lower priority tickets. This can barely be achieved when processing one ticket at a time.

A better solution to this is making it a batch processing job that runs periodically (hourly for example, or even once a day). Whenever a customer submits a ticket, they don't expect that an expert be waiting behind the door in a next minute. Even urgent situations can way hours, less urgent days. Robustness is over performance here.

Making it a batch job will also make the component much simpler to test and develop ridding of the servicing burden, like maintaining an API.

The job will simply start on schedule (as a cron job for example), scan for ticket statuses and create ticket assignments. It will not accept any incoming requests or events, so it's only responsibility is assigning experts to tickets.

It will also improve robustness, because no problem to re-run the job in case of a problem.

## Consequences: 
There is a risk that the job will not start due to a configuration issue or a bug, thus it will require additional monitoring.
