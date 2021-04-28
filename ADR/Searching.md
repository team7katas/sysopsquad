## Title: 
Expert assignment should be done by a separate component

## Status: 
Proposed

## Context: 
- Wrong experts are assigned
- often times the wrong consultant shows up to fix something they know nothing about

## Decision: 
 - A separate component that has access to expert profile to select the correct expert. 
 - it also needs access to monitor the problem ticket queue (see ADR#2) to pick one ticket and select the best expert based on location, problem and his experience (rating perhaps?) 
 - As a separate component, testing of this functionality is easier. More emphasis is on testing as there are problems in assigning the expert correctly (match is incorrect). 
 

## Consequences: 
- Needs access to the expert profile information (could be a separate DB if micro service is chosen).
 
