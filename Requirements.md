## Functional Requirements

* **UC-1**: **User maintenance**:
    - administrator maintains internal user accounts;
    - administrator maintains expert skillset, location, and availability;

* **UC-2**: **Customer registration**:
    - customers register their profile, credit card and support plan;

* **UC-3**: **Ticket workflow**:
    - customers submit tickets via web or by phone call (admins assist);
    - experts use mobile app to read ticket and change ticket status;
    - experts can search knowledge base via mobile app;

* **UC-4**: Survey submission:
    - users fill out and submit satisfaction surveys;

* **UC-5**: **Knowledge base maintenance**:
    - experts update knowledge base;

* **UC-6**: **Reporting**:
    - managers track ticket operations;
    - managers generate reports: financial, expert performance, ticketing;

* **UC-7**: **Billing**:
    - customers are billed automatically (monthly);
    - customers can view their billing history and statements;
    - administrator manages billing processing for customers;

* **UC-8**: **Notification**:
    - customers receive SMS or email about expert assignment;
    - customers receive email with a link to survey web form;
    - experts receive SMS about ticket assignment;

## Architectural Characteristics

* **QA-1**: **scalability** (UC-3)
    - country scale geography (USA?);
    - number of customers - millions;
    - number of tickets per customer <= 100 (let's assume something crazy);

* **QA-2**: **availability** (UC-2, UC-3, UC-4)
    - customer-facing services and KB must be highly available because outages will make a negative impact on business;
    - 99.9% seems reasonable here;

* **QA-3**: **performance** (UC-2, UC-3, UC-6)
    - response time < 2s for page load;
    - knowledge search time several seconds;
    - reports generation should not take an excessive amount of time;

* **QA-4**: **robustness** (UC-3)
    - lost tickets or wrong experts may lead to the business closure;

* **QA-5**: **security** (UC-2, UC-7)
    - customer personal information and credit cards should be stored in secure and comply to PCI requirements;

* **QA-6**: **deployability** (all use cases)
    - deployments should be safe and avoid regression in unrelated components;

## Constraints
* **CON-1**: Integration? Cloud/on-prem?

## Assumptions
* ASM-1: Mobile app can be changed

## Questions:
* What is "help desk"?
* What is the bottleneck in the monolithic app - code? database?
