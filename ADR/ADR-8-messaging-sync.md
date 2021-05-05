## Title: 
ADR-8: Use message-based synchronization of customer data and ticket assignments.

## Status: 
Proposed

## Context: 
Keep customer-facing data and expert ticket assignments in sync between domain parts.

## Decision: 
Since we use separate database for customer and expert data ([ADR-6](ADR-6-separate-customer-db.md) and [ADR-7](ADR-7-separate-experts-db.md)) we need to keep this data in sync with administration database.

Insofar as we decided to use event-drive approach ([ADR-2](ADR-2-event-driven-broker.md)) we can leverage the messaging system to sync customer billing information changes and ticket assignment changes. This will allow communication to be more uniform across the system and will provide maximum decoupling between domain parts.

## Consequences: 

Eventual consistency is fine here because administration data does not need actual state of the ticket assignment and customer billing info immediately when upon modification.

Alternative would using table-level synchronization, but this will increase coupling of database schema and will require some sort of trigger-based notification what will significantly complicate implementation.
