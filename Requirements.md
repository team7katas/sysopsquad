## Business Case

Penultimate Electronics is a large electronics giant that has numerous retail stores throughout the country. When customers buy computers, TV's, stereos, and other electronic equipment, they can choose to purchase a support plan. Customer-facing technology experts (the "Sysops Squad") will then come to the customers residence (or work office) to fix problems with the electronic device.

The current trouble ticket system is a large monolithic application that was developed many years ago. Customers are complaining that consultants are never showing up due to lost tickets, and often times the wrong consultant shows up to fix something they know nothing about. Customers and call-center staff have been complaining that the system is not always available for web-based or call-based problem ticket entry. Change is difficult and risky in this large monolith - whenever a change is made, it takes too long and something else usually breaks. Due to reliability issues, the monolithic system frequently "freezes up" or crashes - they think it's mostly due a spike in usage and the number of customers using the system. If something isn't done soon, Penultimate Electronics will be forced to abandon this very lucrative business line and fire all of the experts.

## Stakeholders
The following stakeholders and their key concerns have been identified:

- **SH-1**: **Administrator**
    - usability, performance, availability, robustness

- **SH-2**: **Customer**  
    - usability, performance, availability, robustness

- **SH-3**: **Sysops Expert**
    - availability, performance, mobility

- **SH-4**: **Manager**
    - reportability, performance

- **SH-5**: **Project Team**
    - extensibility, maintainability, deployability

- **SH-6**: **Sponsor**
    - cost, timeline

- **SH-7**: **IT Support**
    - security, monitorability

## Functional Requirements

- **UC-1**: **User maintenance**:
    1. Maintain internal users of the syste (SH-1)
    2. Maintain expert skillset, location, and availability (SH-1)

- **UC-2**: **Customer support**:
    1. Customer registration (SH-2)
    2. Customer profile maintenance (SH-2)
    3. Support contracts management (SH-2)

- **UC-3**: **Ticket processing**:
    1. Ticket submission (SH-2)
    2. Searching for the right expert (SH-2, SH-3)
    3. Read and update ticket via mobile and web (SH-3)
    4. Survey submission (SH-2)

- **UC-4**: **Knowledge base access**:
    1. Knowledge base search via mobile (SH-3)
    2. Knowledge base update via web (SH-3)

- **UC-5**: **Reporting**:
    1. Tracking of ticket operations (SH-4)
    2. Reporting - financial, expert performance, ticketing (SH-4)

- **UC-6**: **Billing**:
    1. Automatic customer billing (monthly) (SH-2)
    2. View billing history and statements (SH-2)
    3. Billing information maintenance (SH-2)
    4. Billing processing management (SH-2)

- **UC-7**: **Notification**:
    1. Expert assignment notification via SMS or email (SH-2)
    2. Survey notification via email (SH-2)
    3. Ticket assignment notification via mobile (SH-3)

TBD: Integration with Help Desk?

## Architectural Characteristics
- **QA-1**: **scalability** (UC-2, UC-3, UC-4)
    - country scale geography (USA?);
    - number of customers = millions;
    - number of tickets per customer <= 100 (let's assume something crazy);

- **QA-2**: **availability** (UC-2, UC-3.1, UC-3.3, UC-3.4, UC-4.1)
    - customer-facing services and KB must be highly available, because outages will make negative impact on business;
    - 99.9% seems reasonable;

- **QA-3**: **elasticity** (UC-2)
    - the system should remain effective and robust in periods of sales when customers buy a lot things and register for support;

- **QA-4**: **performance** (UC-2, UC-3.1, UC-3.3, UC-3.4, UC-4.1, UC-5)
    - response time < 2s for page load;
    - reports generation should not take an excessive amount of time;

- **QA-5**: **robustness** (UC-3.2)
    - lost tickets or wrong experts may lead to the business closure;

- **QA-6**: **security** (UC-2, UC-6)
    - customer personal information and credit cards should be stored in secure and comply to PCI requirements;

- **QA-7**: **deployability** (All use cases)
    - deployments should be safe and avoid regression in unrelated components;

## Constraints
- **CON-1**: Integration? Cloud/on-prem?

## Assumptions
- **ASM-1**: An expert updates KB via web site
