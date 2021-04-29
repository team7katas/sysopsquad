## Functional Requirements

* **UC-1**: **User maintenance**:
    - administrator maintains internal user accounts;
    - administrator maintains expert skillset, location, and availability;

* **UC-2**: **Customer registration**:
    - customers register their profile, credit card and support plan;

* **UC-3**: **Ticket workflow**:
    - customers submit tickets via web or by phone call;
    - experts use mobile app to read ticket and change ticket status;
    - experts can search knowledge base via mobile app;
    - users fill out and submit satisfaction surveys;

* **UC-4**: **Knowledge base updating**:
    - experts update knowledge base via web;

* **UC-5**: **Reporting**:
    - managers tracking ticket operations;
    - managers generate reports: financial, expert performance, ticketing;

* **UC-6**: **Billing**:
    - customers are billed automatically monthly;
    - customers can view billing history and statements;
    - administrator manages billing processing for customers;

* **UC-7**: **Notification**:
    - customers receive SMS or email about expert assignment;
    - customers receive email with a link on survey web form;
    - experts receive SMS about ticket assignment;

TBD: Integration with Help Desk?

## Architectural Characteristics

* **QA-1**: **scalability** (UC-2, UC-3)
    - country scale geography (USA?);
    - number of customers - millions;
    - number of tickets per customer <= 100 (let's assume something crazy);

* **QA-2**: **availability** (UC-2, UC-3, UC-7)
    - customer-facing services and KB must be highly available because outages will make a negative impact on business;
    - 99.9% seems reasonable here;

* **QA-3**: **elasticity** (UC-2)
    - the system should remain effective and robust in periods of sales when customers buy a lot of things and register for support;

* **QA-4**: **performance** (UC-2, UC-3, UC-5)
    - response time < 2s for page load;
    - reports generation should not take an excessive amount of time;

* **QA-5**: **robustness** (UC-3)
    - lost tickets or wrong experts may lead to the business closure;

* **QA-6**: **security** (UC-2, UC-6)
    - customer personal information and credit cards should be stored in secure and comply to PCI requirements;

* **QA-7**: **deployability** (all use cases)
    - deployments should be safe and avoid regression in unrelated components;

## Constraints
* **CON-1**: Integration? Cloud/on-prem?

## Assumptions
* **ASM-1**: An expert updates KB via web site, not mobile app.
