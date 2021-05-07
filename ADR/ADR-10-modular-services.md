## Title: 
ADR-10: Use sub-domain partitioning for service design

## Status: 
Proposed

## Context: 
The company has concerns regarding the system modularity because each change requires a lot of unrelated stuff to be changed too.

## Decision: 
By designing service as a modular monolith around sub-domain rather than technical layers we can improve modularity and minimize unnecessary changes

## Consequences: 

This may require corresponding database partitioning.
