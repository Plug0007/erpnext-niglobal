

# 1. Organization

## Definition

The **Organization** module defines the company's internal structure. It establishes the Company, Branches, Departments, Designations, and Employment Types that other ERP records depend on.

## Business purpose

Use this module to answer:

- Which legal/company entity owns the operation?
- Which branches exist?
- Which departments exist?
- Which designations are used?
- What types of employment does the company support?

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% ORGANIZATION
    %% Foundation of the company's internal structure.
    %% =========================================================

    A[Organization] --> B[Company]

    %% A company can have multiple operating branches.
    B --> C[Branches]

    %% Departments define functional business areas.
    B --> D[Departments]

    %% Designations define job positions within the organization.
    B --> E[Designations]

    %% Employment types define how employees are engaged.
    B --> F[Employment Types]

    %% Example branches
    C --> C1[Mumbai Head Office]
    C --> C2[Saudi Operations]
    C --> C3[UAE Office]

    %% Example departments
    D --> D1[Management]
    D --> D2[HR]
    D --> D3[Recruitment]
    D --> D4[Operations]
    D --> D5[Finance]
    D --> D6[Documentation]

    %% Example designations
    E --> E1[HR Manager]
    E --> E2[Recruiter]
    E --> E3[Operations Manager]
    E --> E4[Document Controller]
    E --> E5[Finance Manager]

    %% Example employment types
    F --> F1[Full Time]
    F --> F2[Contract]
    F --> F3[Temporary]
    F --> F4[Overseas Contract]
```

---

# 2. Users & Roles

## Definition

The **Users & Roles** module controls who can access ERPNext and what each user is allowed to view, create, edit, submit, approve, cancel, or report on.

## Business purpose

Permissions should follow actual responsibilities instead of giving everyone Administrator/System Manager access.

## Mermaid
```
flowchart TB
    %% =========================================================
    %% USERS & ROLES
    %% Role-centric access architecture
    %% =========================================================

    A["USER ACCESS"] --> B["BUSINESS ROLES"]

    %% ---------------------------------------------------------
    %% RECRUITMENT
    %% ---------------------------------------------------------
    B --> R["RECRUITMENT"]

    R --> R1["JDR"]
    R --> R2["Candidates"]
    R --> R3["Interviews"]
    R --> R4["Job Offers"]

    R1 --> R5["Create / Edit / Submit"]
    R2 --> R6["Create / Edit"]
    R3 --> R7["Manage"]
    R4 --> R8["Create / Submit"]

    %% ---------------------------------------------------------
    %% HR
    %% ---------------------------------------------------------
    B --> H["HR"]

    H --> H1["Employees"]
    H --> H2["Contracts"]
    H --> H3["Attendance"]
    H --> H4["Leave"]

    H1 --> H5["Create / Edit"]
    H2 --> H6["Manage"]
    H3 --> H7["Manage"]
    H4 --> H8["Manage"]

    %% ---------------------------------------------------------
    %% DOCUMENTATION
    %% ---------------------------------------------------------
    B --> D["DOCUMENTATION"]

    D --> D1["Passport"]
    D --> D2["Iqama"]
    D --> D3["Visa"]
    D --> D4["Medical"]
    D --> D5["Insurance"]

    D1 --> D6["Upload / Verify"]
    D2 --> D7["Process / Renew"]
    D3 --> D8["Process / Track"]
    D4 --> D9["Verify"]
    D5 --> D10["Track"]

    %% ---------------------------------------------------------
    %% OPERATIONS
    %% ---------------------------------------------------------
    B --> O["OPERATIONS"]

    O --> O1["Deployment"]
    O --> O2["Client Sites"]
    O --> O3["Travel"]
    O --> O4["Timesheets"]

    O1 --> O5["Create / Update"]
    O2 --> O6["Manage"]
    O3 --> O7["Track"]
    O4 --> O8["Manage"]

    %% ---------------------------------------------------------
    %% FINANCE
    %% ---------------------------------------------------------
    B --> F["FINANCE"]

    F --> F1["Client Billing"]
    F --> F2["Employee Cost"]
    F --> F3["Vendor Cost"]
    F --> F4["Margin"]

    F1 --> F5["Create / Approve"]
    F2 --> F6["Manage"]
    F3 --> F7["Manage"]
    F4 --> F8["View / Report"]

    %% ---------------------------------------------------------
    %% MANAGEMENT
    %% ---------------------------------------------------------
    B --> M["MANAGEMENT"]

    M --> M1["Dashboard"]
    M --> M2["Reports"]
    M --> M3["Approvals"]

    M1 --> M4["View"]
    M2 --> M5["View / Export"]
    M3 --> M6["Approve"]
    ```
---

# 3. Clients & Vendors

## Definition

The **Clients & Vendors** module manages external organizations connected to the manpower business.

- **Client:** Overseas organization requesting manpower.
- **Vendor:** External organization providing recruitment, medical, travel, documentation, insurance, or other services.

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% CLIENTS AND VENDORS
    %% External business parties.
    %% =========================================================

    A[Clients & Vendors]

    %% Client side
    A --> B[Clients]
    B --> B1[Customer Master]

    B1 --> B2[Client Contact]
    B1 --> B3[Client Address]
    B1 --> B4[Client Type]
    B1 --> B5[Country]

    %% Vendor side
    A --> C[Vendors]
    C --> C1[Supplier Master]

    C1 --> C2[Vendor Contact]
    C1 --> C3[Vendor Address]
    C1 --> C4[Vendor Type]
    C1 --> C5[Country]

    %% Contracts are created from these parties.
    B1 --> D[Client Contract]
    C1 --> E[Vendor Contract]
```

---

# 4. Client Contract

## Definition

A **Client Contract** represents the commercial agreement between the manpower company and an overseas client.

It defines the terms under which manpower requirements, deployments, billing, and profitability are managed.

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% CLIENT CONTRACT
    %% Commercial relationship with the client.
    %% =========================================================

    A[Client] --> B[Client Contract]

    %% Contract identity and validity.
    B --> C[Contract Details]
    C --> C1[Contract Number]
    C --> C2[Start Date]
    C --> C3[End Date]
    C --> C4[Country]
    C --> C5[Location]

    %% Manpower requirements allowed by the contract.
    B --> D[Manpower Terms]
    D --> D1[Position]
    D --> D2[Required Quantity]
    D --> D3[Working Hours]
    D --> D4[Contract Duration]

    %% Commercial terms used for billing.
    B --> E[Commercial Terms]
    E --> E1[Billing Rate]
    E --> E2[Currency]
    E --> E3[Payment Terms]

    %% Client demand is created against the contract.
    B --> F[JDR]
```

---

# 5. JDR — Job Demand Request

## Definition

The **JDR** is the central manpower-demand document.

It represents a client's request for workers and starts the recruitment process.

One JDR can contain multiple positions.

Example:

- 50 Electricians
- 20 Welders
- 10 Plumbers

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% JDR - JOB DEMAND REQUEST
    %% Central recruitment-demand object.
    %% =========================================================

    A[Client Contract] --> B[JDR]

    %% Basic JDR information.
    B --> C[JDR Information]
    C --> C1[JDR Number]
    C --> C2[Client]
    C --> C3[Country]
    C --> C4[Location]
    C --> C5[Required By]
    C --> C6[Priority]

    %% A JDR can contain many manpower positions.
    B --> D[Manpower Requirements]
    D --> D1[Position]
    D --> D2[Required Quantity]
    D --> D3[Experience]
    D --> D4[Qualification]
    D --> D5[Salary]
    D --> D6[Benefits]

    %% JDR lifecycle.
    B --> S[Status]

    S --> S1[Draft]
    S --> S2[Submitted]
    S --> S3[Approved]
    S --> S4[Recruitment]
    S --> S5[Selection]
    S --> S6[Documentation]
    S --> S7[Ready for Deployment]
    S --> S8[Closed]

    %% Recruitment is initiated from the JDR.
    B --> E[Recruitment]
```

---

# 6. Recruitment

## Definition

The **Recruitment** module converts an approved JDR into job openings, candidates, screening, interviews, selection, offers, and eventually employees.

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% RECRUITMENT
    %% Candidate lifecycle from JDR to Employee.
    %% =========================================================

    A[JDR] --> B[Job Opening]
    B --> C[Candidates]

    %% Candidate evaluation.
    C --> D[Screening]
    D --> E[Interview]
    E --> F[Selection]

    %% Selection decision.
    F --> G{Selected?}

    G -->|No| H[Rejected / Hold]
    G -->|Yes| I[Job Offer]

    %% Offer decision.
    I --> J{Offer Accepted?}

    J -->|No| K[Offer Rejected]
    J -->|Yes| L[Employee Creation]

    %% Candidate data.
    C --> C1[Candidate Profile]
    C --> C2[Experience]
    C --> C3[Qualification]
    C --> C4[Skills]
    C --> C5[Passport Details]

    %% Successful candidate becomes an employee.
    L --> M[Employee Master]
```

---

# 7. Employee Master

## Definition

The **Employee Master** is the central HR record for a worker after recruitment/selection.

It should hold core employee information while linking specialized records such as Passport, Iqama, Visa, Contract, and Deployment.

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% EMPLOYEE MASTER
    %% Central employee record.
    %% =========================================================

    A[Selected Candidate] --> B[Employee Master]

    %% Personal information.
    B --> C[Personal Information]
    C --> C1[Name]
    C --> C2[Date of Birth]
    C --> C3[Nationality]
    C --> C4[Contact]
    C --> C5[Address]

    %% Internal employment information.
    B --> D[Employment Information]
    D --> D1[Employee ID]
    D --> D2[Department]
    D --> D3[Designation]
    D --> D4[Joining Date]
    D --> D5[Employment Type]

    %% Overseas assignment information.
    B --> E[Overseas Information]
    E --> E1[Country]
    E --> E2[Client]
    E --> E3[Deployment Status]
    E --> E4[Current Location]

    %% Related employee records.
    B --> F[Documents]
    F --> F1[Passport]
    F --> F2[Iqama]
    F --> F3[Visa]
    F --> F4[Medical]
    F --> F5[Insurance]

    B --> G[Contracts]
    B --> H[Deployment]
```

---

# 8. Employee Documents

## Definition

The **Employee Documents** layer manages identity, immigration, medical, insurance, qualification, and employment documents.

Each document can have an issue date, expiry date, attachment, and verification status.

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% EMPLOYEE DOCUMENTS
    %% Common document management layer.
    %% =========================================================

    A[Employee] --> B[Employee Documents]

    B --> C[Passport]
    B --> D[Iqama]
    B --> E[Visa]
    B --> F[Medical]
    B --> G[Insurance]
    B --> H[Certificate]
    B --> I[Employment Contract]

    %% Common document metadata.
    C --> C1[Document Number]
    C --> C2[Issue Date]
    C --> C3[Expiry Date]
    C --> C4[Attachment]
    C --> C5[Verification Status]

    %% Specialized Iqama data.
    D --> D1[Iqama Number]
    D --> D2[Issue Date]
    D --> D3[Expiry Date]
    D --> D4[Profession]
    D --> D5[Sponsor]
    D --> D6[Attachment]

    %% Specialized Visa data.
    E --> E1[Visa Number]
    E --> E2[Visa Type]
    E --> E3[Issue Date]
    E --> E4[Expiry Date]
    E --> E5[Attachment]
```

---

# 9. Passport

## Definition

The **Passport** module tracks passport identity information, validity, scanned documents, and renewal requirements.

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% PASSPORT
    %% Employee passport lifecycle.
    %% =========================================================

    A[Employee] --> B[Passport]

    %% Passport identity data.
    B --> C[Passport Details]
    C --> C1[Passport Number]
    C --> C2[Nationality]
    C --> C3[Issue Date]
    C --> C4[Expiry Date]
    C --> C5[Place of Issue]

    %% Stored passport files.
    B --> D[Passport Document]
    D --> D1[Passport Scan]
    D --> D2[Photo]
    D --> D3[Supporting Documents]

    %% Expiry monitoring.
    B --> E[Expiry Monitoring]
    E --> E1[90 Days]
    E --> E2[60 Days]
    E --> E3[30 Days]
    E --> E4[7 Days]
    E --> E5[Expired]

    %% Expired passport triggers renewal.
    E5 --> F[Renewal Process]
    F --> B
```

---

# 10. Iqama

## Definition

The **Iqama** module manages an employee's Saudi residence/work-permit record, related documents, verification, expiry monitoring, and renewal lifecycle.

> **Important:** The actual legal document checklist should be configurable according to the company's current Saudi process and the employee's case. Do not hard-code a universal legal checklist.

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% IQAMA
    %% Saudi employee residence/work-permit lifecycle.
    %% =========================================================

    A[Employee] --> B[Iqama Record]

    %% Core Iqama information.
    B --> C[Iqama Details]
    C --> C1[Iqama Number]
    C --> C2[Iqama Type]
    C --> C3[Profession]
    C --> C4[Sponsor]
    C --> C5[Issue Date]
    C --> C6[Expiry Date]
    C --> C7[Place of Issue]

    %% Supporting document checklist.
    B --> D[Required Documents]
    D --> D1[Passport]
    D --> D2[Visa]
    D --> D3[Medical]
    D --> D4[Insurance]
    D --> D5[Employment Contract]
    D --> D6[Photograph]
    D --> D7[Other Documents]

    %% Every required document must pass verification.
    D1 --> E[Verification]
    D2 --> E
    D3 --> E
    D4 --> E
    D5 --> E

    E --> E1[Uploaded]
    E --> E2[Under Review]
    E --> E3[Verified]
    E --> E4[Rejected]

    %% Iqama operational status.
    B --> S{Iqama Status}
    S --> S1[Active]
    S --> S2[Expiring Soon]
    S --> S3[Expired]
    S --> S4[Renewal in Progress]
    S --> S5[Renewed]

    %% Expiry monitoring thresholds.
    B --> G[Expiry Monitoring]
    G --> G1[90 Days]
    G --> G2[60 Days]
    G --> G3[30 Days]
    G --> G4[7 Days]
    G --> G5[Expired]

    %% Expiry triggers renewal.
    G5 --> F[Renewal]

    %% Renewal lifecycle.
    F --> F1[Start Renewal]
    F1 --> F2[Collect Documents]
    F2 --> F3[Verify Documents]
    F3 --> F4[Submit]
    F4 --> F5[Processing]
    F5 --> F6[Approved]
    F6 --> F7[New Iqama]

    %% New record/version becomes active.
    F7 --> B
```

---

# 11. Visa

## Definition

The **Visa** module tracks visa details, supporting documents, processing stages, approval/rejection, and expiry.

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% VISA
    %% Immigration/visa processing lifecycle.
    %% =========================================================

    A[Employee] --> B[Visa]

    %% Visa identity and validity.
    B --> C[Visa Details]
    C --> C1[Visa Number]
    C --> C2[Visa Type]
    C --> C3[Country]
    C --> C4[Issue Date]
    C --> C5[Expiry Date]

    %% Supporting files.
    B --> D[Documents]
    D --> D1[Passport]
    D --> D2[Employment Contract]
    D --> D3[Medical]
    D --> D4[Other Supporting Documents]

    %% Processing workflow.
    B --> E[Processing]
    E --> E1[Application]
    E --> E2[Submitted]
    E --> E3[Processing]
    E --> E4[Approved]
    E --> E5[Rejected]

    %% Expiry action.
    B --> F[Expiry]
    F --> F1[Expiry Alert]
    F1 --> F2[Renewal / Action]
```

---

# 12. Employee Contract

## Definition

The **Employee Contract** represents the employment agreement between the company and the employee.

It is different from the Client Contract.

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% EMPLOYEE CONTRACT
    %% Employment relationship with the worker.
    %% =========================================================

    A[Employee] --> B[Employee Contract]

    %% Employment terms.
    B --> C[Employment Terms]
    C --> C1[Contract Number]
    C --> C2[Start Date]
    C --> C3[End Date]
    C --> C4[Employment Type]
    C --> C5[Working Hours]

    %% Compensation.
    B --> D[Compensation]
    D --> D1[Basic Salary]
    D --> D2[Allowances]
    D --> D3[Benefits]
    D --> D4[Currency]

    %% Overseas assignment.
    B --> E[Assignment]
    E --> E1[Client]
    E --> E2[Country]
    E --> E3[Position]
    E --> E4[Project / Site]

    %% Contract lifecycle.
    B --> F[Expiry Monitoring]
    F --> G[Renewal]
```

---

# 13. Deployment

## Definition

The **Deployment** module records where, when, and under which client/project an employee is deployed.

It connects the JDR, employee, client, project/site, travel, and joining process.

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% DEPLOYMENT
    %% Employee assignment and overseas movement lifecycle.
    %% =========================================================

    A[JDR] --> B[Deployment]
    C[Employee] --> B
    D[Client] --> B
    E[Client Site] --> B

    %% Deployment master information.
    B --> F[Deployment Details]
    F --> F1[Employee]
    F --> F2[Client]
    F --> F3[JDR]
    F --> F4[Position]
    F --> F5[Project / Site]
    F --> F6[Country]
    F --> F7[Deployment Date]

    %% Operational deployment workflow.
    B --> G[Deployment Process]
    G --> G1[Selected]
    G --> G2[Documentation]
    G --> G3[Visa Processing]
    G --> G4[Visa Approved]
    G --> G5[Travel Pending]
    G --> G6[Travel Booked]
    G --> G7[Departed]
    G --> G8[Arrived]
    G --> G9[Client Joined]
    G --> G10[Deployed]

    %% Deployed employees enter operational management.
    G10 --> H[Operations]
```

---

# 14. Timesheet / Operations

## Definition

The **Operations** layer manages the employee after deployment, including attendance, leave, timesheets, working hours, activities, billing rates, and cost rates.

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% OPERATIONS
    %% Post-deployment workforce activity.
    %% =========================================================

    A[Deployed Employee] --> B[Client / Project]
    B --> C[Timesheet]

    %% Timesheet data.
    C --> D[Date]
    C --> E[Working Hours]
    C --> F[Activity]
    C --> G[Billing Rate]
    C --> H[Cost Rate]
    C --> I[Billing Amount]
    C --> J[Cost Amount]

    %% Other HR operational records.
    A --> K[Attendance]
    A --> L[Leave]

    %% Operational data feeds timesheet/costing.
    K --> M[Working Data]
    L --> M
    M --> C
```

---

# 15. Employee Cost

## Definition

The **Employee Cost** module calculates the actual cost of an employee to the company, including salary and deployment-related expenses.

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% EMPLOYEE COST
    %% Direct and allocated employee/deployment costs.
    %% =========================================================

    A[Employee] --> B[Employee Cost]

    %% Cost components.
    B --> C[Salary]
    B --> D[Accommodation]
    B --> E[Transport]
    B --> F[Insurance]
    B --> G[Visa]
    B --> H[Medical]
    B --> I[Travel]
    B --> J[Other Costs]

    %% Aggregate all employee-related costs.
    C --> K[Total Employee Cost]
    D --> K
    E --> K
    F --> K
    G --> K
    H --> K
    I --> K
    J --> K

    %% Allocate cost to business context.
    K --> L[Client / JDR / Deployment]
```

---

# 16. Vendor Cost

## Definition

The **Vendor Cost** module tracks money spent on external suppliers and links each cost to the relevant JDR, employee, or deployment.

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% VENDOR COST
    %% External supplier/recruitment costs.
    %% =========================================================

    A[Vendor] --> B[Vendor Cost]

    %% Cost categories.
    B --> C[Recruitment]
    B --> D[Visa]
    B --> E[Medical]
    B --> F[Travel]
    B --> G[Documentation]
    B --> H[Commission]
    B --> I[Other]

    %% Traceability.
    B --> J[JDR]
    B --> K[Employee]
    B --> L[Deployment]

    %% Aggregate vendor costs.
    C --> M[Total Vendor Cost]
    D --> M
    E --> M
    F --> M
    G --> M
    H --> M
    I --> M
```

---

# 17. Client Billing

## Definition

The **Client Billing** module converts contractual rates, employee deployments, timesheets, and other billable items into invoices and recognized revenue.

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% CLIENT BILLING
    %% Revenue generation.
    %% =========================================================

    A[Client Contract] --> B[Billing Terms]
    C[Deployment] --> B
    D[Timesheet] --> B

    %% Billing record.
    B --> E[Client Billing]

    %% Billable components.
    E --> F[Employee Billing]
    E --> G[Timesheet Billing]
    E --> H[Fixed Charges]
    E --> I[Other Charges]

    %% Standard accounting invoice.
    F --> J[Invoice]
    G --> J
    H --> J
    I --> J

    J --> K[Revenue]
```

---

# 18. Margin Reporting

## Definition

The **Margin Reporting** layer determines profitability by comparing client revenue with employee, vendor, and operational costs.

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% MARGIN REPORTING
    %% Profitability analysis.
    %% =========================================================

    A[Client Revenue] --> E[Total Revenue]

    B[Employee Cost] --> F[Total Cost]
    C[Vendor Cost] --> F
    D[Other Operational Cost] --> F

    %% Profit calculation.
    E --> G[Gross Profit]
    F --> G

    %% Percentage margin.
    G --> H[Margin %]

    %% Drill-down reporting dimensions.
    H --> I[Client Margin]
    H --> J[JDR Margin]
    H --> K[Employee Margin]
    H --> L[Project Margin]
    H --> M[Country Margin]

    %% Management consumes the reports.
    I --> N[Management Dashboard]
    J --> N
    K --> N
    L --> N
    M --> N
```

---

# 19. Expiry Management

## Definition

The **Expiry Management** engine monitors dates for passports, Iqamas, visas, medical documents, insurance, contracts, and certifications.

It generates warnings and starts renewal/action processes.

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% EXPIRY MANAGEMENT
    %% Centralized expiry and alert engine.
    %% =========================================================

    A[Employee Documents] --> B[Expiry Engine]

    %% Documents monitored by the engine.
    A1[Passport] --> A
    A2[Iqama] --> A
    A3[Visa] --> A
    A4[Medical] --> A
    A5[Insurance] --> A
    A6[Contract] --> A
    A7[Certification] --> A

    %% Determine the remaining validity.
    B --> C{Days Remaining}

    C -->|> 90 Days| D[Valid]
    C -->|61 - 90| E[Monitor]
    C -->|31 - 60| F[Warning]
    C -->|8 - 30| G[Urgent]
    C -->|1 - 7| H[Critical]
    C -->|< 0| I[Expired]

    %% Notifications.
    F --> J[HR Alert]
    G --> J
    H --> K[Management Alert]
    I --> K

    %% Renewal/action workflow.
    J --> L[Renewal Process]
    K --> L
```

---

# 20. Management Dashboard

## Definition

The **Management Dashboard** is the final reporting layer. It gives management a consolidated view of manpower, recruitment, deployment, document expiry, revenue, cost, and profitability.

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% MANAGEMENT DASHBOARD
    %% Executive reporting layer.
    %% =========================================================

    A[Management Dashboard]

    %% Organization KPIs.
    A --> B[Organization]
    B --> B1[Branches]
    B --> B2[Departments]
    B --> B3[Users]

    %% Recruitment KPIs.
    A --> C[Recruitment]
    C --> C1[Open JDRs]
    C --> C2[Candidates]
    C --> C3[Selected]
    C --> C4[Pending Recruitment]

    %% Employee KPIs.
    A --> D[Employees]
    D --> D1[Total Employees]
    D --> D2[Deployed]
    D --> D3[Available]
    D --> D4[Under Processing]

    %% Deployment KPIs.
    A --> E[Deployment]
    E --> E1[Visa Processing]
    E --> E2[Travel Pending]
    E --> E3[Ready]
    E --> E4[Deployed]

    %% Document expiry KPIs.
    A --> F[Documents]
    F --> F1[Passport Expiry]
    F --> F2[Iqama Expiry]
    F --> F3[Visa Expiry]
    F --> F4[Contract Expiry]

    %% Commercial KPIs.
    A --> G[Commercial]
    G --> G1[Revenue]
    G --> G2[Employee Cost]
    G --> G3[Vendor Cost]
    G --> G4[Gross Profit]
    G --> G5[Margin %]
```

---

# 21. Complete System Architecture

## Definition

This is the **master architecture**. It shows how the entire system is connected from organization setup to recruitment, employee management, immigration documents, deployment, operations, costing, billing, expiry alerts, and management reporting.

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% COMPLETE OVERSEAS MANPOWER ERP ARCHITECTURE
    %% =========================================================

    %% ---------------- FOUNDATION ----------------
    A[ORGANIZATION] --> B[USERS & ROLES]
    B --> C[CLIENTS & VENDORS]

    %% ---------------- COMMERCIAL FOUNDATION ----------------
    C --> D[CLIENT CONTRACT]

    %% ---------------- RECRUITMENT ----------------
    D --> E[JDR]
    E --> F[JOB OPENING]
    F --> G[CANDIDATE]
    G --> H[SCREENING]
    H --> I[INTERVIEW]
    I --> J[SELECTION]
    J --> K[JOB OFFER]

    %% ---------------- EMPLOYEE ----------------
    K --> L[EMPLOYEE MASTER]

    %% ---------------- DOCUMENTS ----------------
    L --> M[EMPLOYEE DOCUMENTS]
    M --> M1[PASSPORT]
    M --> M2[IQAMA]
    M --> M3[VISA]
    M --> M4[MEDICAL]
    M --> M5[INSURANCE]

    %% ---------------- EMPLOYMENT ----------------
    L --> N[EMPLOYEE CONTRACT]

    %% ---------------- DEPLOYMENT ----------------
    L --> O[DEPLOYMENT]
    E --> O
    C --> O

    O --> P[CLIENT / PROJECT / SITE]

    %% ---------------- OPERATIONS ----------------
    P --> Q[ATTENDANCE]
    P --> R[TIMESHEET]

    %% ---------------- COSTING ----------------
    L --> S[EMPLOYEE COST]
    C --> T[VENDOR COST]

    %% ---------------- BILLING ----------------
    R --> U[CLIENT BILLING]
    N --> U
    O --> U

    %% ---------------- PROFITABILITY ----------------
    S --> V[MARGIN]
    T --> V
    U --> V

    %% ---------------- EXPIRY ----------------
    M1 --> W[EXPIRY ENGINE]
    M2 --> W
    M3 --> W
    M4 --> W
    M5 --> W
    N --> W

    W --> X[RENEWAL / ALERTS]

    %% ---------------- MANAGEMENT ----------------
    V --> Y[MANAGEMENT DASHBOARD]
    W --> Y
    E --> Y
    G --> Y
    O --> Y
```

---

# 22. Recommended Implementation Order

## Definition

This diagram shows the order in which the ERP should be implemented. The sequence follows data dependencies.

For example, Iqama depends on Employee, Employee depends on Recruitment, and Recruitment depends on JDR.

## Mermaid

```mermaid
flowchart LR
    %% =========================================================
    %% IMPLEMENTATION ORDER
    %% Build according to data dependencies.
    %% =========================================================

    A[1. Organization] --> B[2. Users & Roles]
    B --> C[3. Clients & Vendors]
    C --> D[4. Client Contracts]
    D --> E[5. JDR]
    E --> F[6. Recruitment]
    F --> G[7. Employee Master]
    G --> H[8. Employee Documents]
    H --> I[9. Passport / Iqama / Visa]
    I --> J[10. Employee Contract]
    J --> K[11. Deployment]
    K --> L[12. Timesheets / Operations]
    L --> M[13. Costs]
    M --> N[14. Billing / Margin]
    N --> O[15. Expiry Alerts]
    O --> P[16. Dashboards]
```

---

# 23. Core Business Flow

## Definition

This is the shortest representation of the company's actual business process.

```mermaid
flowchart TD
    %% =========================================================
    %% CORE BUSINESS FLOW
    %% One client requirement through to profitability.
    %% =========================================================

    A[CLIENT] --> B[CLIENT CONTRACT]
    B --> C[JDR]
    C --> D[RECRUITMENT]
    D --> E[CANDIDATE]
    E --> F[SELECTION]
    F --> G[EMPLOYEE]
    G --> H[DOCUMENTATION]
    H --> I[IQAMA / VISA / PASSPORT]
    I --> J[DEPLOYMENT]
    J --> K[CLIENT / SITE]
    K --> L[TIMESHEET]
    L --> M[BILLING]
    G --> N[EMPLOYEE COST]
    K --> O[VENDOR COST]
    M --> P[REVENUE]
    N --> Q[TOTAL COST]
    O --> Q
    P --> R[PROFIT / MARGIN]
    I --> S[EXPIRY MONITORING]
    S --> T[RENEWAL / ALERT]
```

---

# 24. Key Data Relationships

## Definition

These are the relationships that should exist between the main ERP records. They prevent the system from becoming a collection of disconnected forms.

```mermaid
flowchart TD
    %% =========================================================
    %% KEY DATA RELATIONSHIPS
    %% =========================================================

    CLIENT[Client] --> CONTRACT[Client Contract]
    CONTRACT --> JDR[JDR]

    JDR --> CANDIDATE[Candidate]
    CANDIDATE --> EMPLOYEE[Employee]

    EMPLOYEE --> PASSPORT[Passport]
    EMPLOYEE --> IQAMA[Iqama]
    EMPLOYEE --> VISA[Visa]
    EMPLOYEE --> MEDICAL[Medical]
    EMPLOYEE --> INSURANCE[Insurance]
    EMPLOYEE --> EMP_CONTRACT[Employee Contract]

    JDR --> DEPLOYMENT[Deployment]
    EMPLOYEE --> DEPLOYMENT
    CLIENT --> DEPLOYMENT

    DEPLOYMENT --> SITE[Client Project / Site]

    SITE --> TIMESHEET[Timesheet]
    EMPLOYEE --> EMP_COST[Employee Cost]

    VENDOR[Vendor] --> VENDOR_COST[Vendor Cost]
    VENDOR_COST --> JDR
    VENDOR_COST --> EMPLOYEE
    VENDOR_COST --> DEPLOYMENT

    CLIENT --> BILLING[Client Billing]
    DEPLOYMENT --> BILLING
    TIMESHEET --> BILLING

    BILLING --> REVENUE[Revenue]
    EMP_COST --> COST[Total Cost]
    VENDOR_COST --> COST

    REVENUE --> MARGIN[Margin]
    COST --> MARGIN

    PASSPORT --> EXPIRY[Expiry Engine]
    IQAMA --> EXPIRY
    VISA --> EXPIRY
    MEDICAL --> EXPIRY
    INSURANCE --> EXPIRY
    EMP_CONTRACT --> EXPIRY

    EXPIRY --> ALERTS[Alerts / Renewal]
```

---

# 25. Design Rules

The following rules should be followed during implementation:

1. **Use standard ERPNext/Frappe HR DocTypes where they already solve the problem.**
2. **Create custom DocTypes only for business objects that ERPNext does not model correctly.**
3. **JDR should be a major custom DocType.**
4. **Deployment should be a major custom DocType.**
5. **Iqama needs a specialized workflow because it has documents, verification, expiry, and renewal.**
6. **Do not duplicate Customer, Supplier, Employee, Timesheet, Invoice, or accounting data unnecessarily.**
7. **Use Link fields to connect records instead of manually typing names.**
8. **Use child tables for repeating structures such as multiple positions in a JDR.**
9. **Use Workflow for approval/status transitions rather than relying only on editable status fields.**
10. **Keep historical records for documents such as Passport and Iqama instead of overwriting old records.**
11. **Make expiry thresholds configurable.**
12. **Build dashboards only after the underlying data is reliable.**
13. **Test every phase before moving to the next dependency.**

---

# 26. Final Dependency Chain

```mermaid
flowchart LR
    %% =========================================================
    %% FINAL DEPENDENCY CHAIN
    %% =========================================================

    A[Organization]
    --> B[Users]
    --> C[Client]
    --> D[Client Contract]
    --> E[JDR]
    --> F[Candidate]
    --> G[Employee]
    --> H[Documents]
    --> I[Iqama / Visa / Passport]
    --> J[Employee Contract]
    --> K[Deployment]
    --> L[Timesheet]
    --> M[Cost]
    --> N[Billing]
    --> O[Margin]
    --> P[Expiry Alerts]
    --> Q[Management Dashboard]
```

> **Core principle:** `Client → Contract → JDR → Candidate → Employee → Documents → Deployment → Operations → Cost → Billing → Margin → Alerts → Dashboard`.
