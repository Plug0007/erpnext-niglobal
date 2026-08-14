# Overseas Manpower ERPNext — Uniform Mermaid Blueprint

> **Format used for every module:** Definition → Simple Business Flow → Vertical Mermaid.
>
> The diagrams are intentionally simple and vertical. Decision points use explicit **Yes / No** branches wherever the process has a real condition.

---

# 1. Organization

## Definition

The **Organization** module defines the company's internal structure, including company, branches, departments, designations, and employment types.

## Simple Business Flow

```text
Company
 ↓
Branches
 ↓
Departments
 ↓
Designations
 ↓
Employment Types
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% ORGANIZATION
    %% Company structure and HR foundation.
    %% =========================================================

    A["Organization"]
    A --> B["Company"]
    B --> C["Branches"]
    C --> C1["Mumbai Head Office"]
    C --> C2["Saudi Operations"]
    C --> C3["UAE Office"]

    B --> D["Departments"]
    D --> D1["Management"]
    D --> D2["HR"]
    D --> D3["Recruitment"]
    D --> D4["Operations"]
    D --> D5["Finance"]
    D --> D6["Documentation"]

    B --> E["Designations"]
    E --> E1["HR Manager"]
    E --> E2["Recruiter"]
    E --> E3["Operations Manager"]
    E --> E4["Document Controller"]

    B --> F["Employment Types"]
    F --> F1["Full Time"]
    F --> F2["Contract"]
    F --> F3["Temporary"]
    F --> F4["Overseas Contract"]
```

---

# 2. Users & Roles

## Definition

The **Users & Roles** module controls who can access the ERP, which business area they can access, and what actions they can perform.

## Simple Business Flow

```text
User
 ↓
Role
 ↓
Module Access
 ↓
Permissions
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% USERS & ROLES
    %% User access and responsibility.
    %% =========================================================

    A["User Access"]
    A --> B["Business Role"]

    B --> B1["Recruitment"]
    B --> B2["HR"]
    B --> B3["Documentation"]
    B --> B4["Operations"]
    B --> B5["Finance"]
    B --> B6["Management"]

    B1 --> C1["JDR / Candidates / Interviews"]
    B2 --> C2["Employees / Contracts / HRMS"]
    B3 --> C3["Passport / Iqama / Visa"]
    B4 --> C4["Deployment / Sites / Timesheets"]
    B5 --> C5["Billing / Costs / Margin"]
    B6 --> C6["Dashboard / Reports"]

    C1 --> D["Permissions"]
    C2 --> D
    C3 --> D
    C4 --> D
    C5 --> D
    C6 --> D

    D --> D1["View"]
    D --> D2["Create"]
    D --> D3["Edit"]
    D --> D4["Submit"]
    D --> D5["Approve"]
    D --> D6["Report"]
```

---

# 3. Clients & Vendors

## Definition

The **Clients & Vendors** module manages the external organizations involved in the overseas manpower business.

## Simple Business Flow

```text
External Party
 ↓
Client / Vendor
 ↓
Master Details
 ↓
Contract / Cost
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% CLIENTS & VENDORS
    %% External business parties.
    %% =========================================================

    A["External Party"]
    A --> B{"Party Type"}

    B -->|Client| C["Client Master"]
    B -->|Vendor| D["Vendor Master"]

    C --> C1["Contact"]
    C --> C2["Address"]
    C --> C3["Country"]
    C --> C4["Client Type"]
    C --> C5["Client Contract"]

    D --> D1["Contact"]
    D --> D2["Address"]
    D --> D3["Country"]
    D --> D4["Vendor Type"]
    D --> D5["Vendor Cost"]
```

---

# 4. Client Contract

## Definition

The **Client Contract** records the commercial agreement between the manpower company and an overseas client.

## Simple Business Flow

```text
Client
 ↓
Contract
 ↓
Manpower Terms
 ↓
Commercial Terms
 ↓
JDR
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% CLIENT CONTRACT
    %% Commercial agreement with overseas client.
    %% =========================================================

    A["Client"]
    A --> B["Client Contract"]

    B --> C["Contract Details"]
    C --> C1["Contract Number"]
    C --> C2["Start Date"]
    C --> C3["End Date"]
    C --> C4["Country"]
    C --> C5["Location"]

    B --> D["Manpower Terms"]
    D --> D1["Position"]
    D --> D2["Required Quantity"]
    D --> D3["Working Hours"]
    D --> D4["Contract Duration"]

    B --> E["Commercial Terms"]
    E --> E1["Billing Rate"]
    E --> E2["Currency"]
    E --> E3["Payment Terms"]

    B --> F["JDR"]
```

---

# 5. JDR — Job Demand Request

## Definition

The **JDR** is the main manpower-demand record. It captures what the overseas client needs and starts the recruitment process.

## Simple Business Flow

```text
Client Contract
 ↓
JDR
 ↓
Manpower Requirement
 ↓
Approval
 ↓
Recruitment
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% JDR
    %% Client manpower demand.
    %% =========================================================

    A["Client Contract"]
    A --> B["JDR"]

    B --> C["JDR Information"]
    C --> C1["JDR Number"]
    C --> C2["Client"]
    C --> C3["Country"]
    C --> C4["Location"]
    C --> C5["Required By"]
    C --> C6["Priority"]

    B --> D["Manpower Requirements"]
    D --> D1["Position"]
    D --> D2["Required Quantity"]
    D --> D3["Experience"]
    D --> D4["Qualification"]
    D --> D5["Salary"]
    D --> D6["Benefits"]

    B --> E{"JDR Approved?"}
    E -->|No| F["Draft / Correction"]
    F --> B
    E -->|Yes| G["Recruitment"]
```

---

# 6. Overseas Recruitment

## Definition

The **Overseas Recruitment** module manages the process of selecting candidates for overseas client requirements, from sourcing and screening to client approval, documentation, medical/visa processing, and deployment readiness.

## Simple Business Flow

```text
Approved JDR
 ↓
Candidate Sourcing
 ↓
Screening
 ↓
Document Verification
 ↓
Interview / Trade Test
 ↓
Client Selection
 ↓
Offer & Contract
 ↓
Medical & Compliance
 ↓
Visa Processing
 ↓
Deployment Ready
 ↓
Employee
 ↓
Deployment
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% OVERSEAS RECRUITMENT
    %% Candidate lifecycle for overseas manpower.
    %% =========================================================

    A["Approved JDR"]
    A --> B["Candidate Sourcing"]
    B --> C["Screening"]

    C --> D{"Eligible?"}
    D -->|No| X["Rejected / Hold"]
    D -->|Yes| E["Document Verification"]

    E --> F{"Documents Valid?"}
    F -->|No| G["Document Correction"]
    G --> E
    F -->|Yes| H["Interview / Trade Test"]

    H --> I{"Passed?"}
    I -->|No| X
    I -->|Yes| J["Client Selection"]

    J --> K{"Selected by Client?"}
    K -->|No| X
    K -->|Yes| L["Offer & Contract"]

    L --> M{"Offer Accepted?"}
    M -->|No| X
    M -->|Yes| N["Medical & Compliance"]

    N --> O{"Cleared?"}
    O -->|No| P["Hold / Action Required"]
    O -->|Yes| Q["Visa Processing"]

    Q --> R{"Visa Approved?"}
    R -->|No| S["Visa Hold"]
    R -->|Yes| T["Deployment Ready"]

    T --> U["Employee Master"]
    U --> V["Deployment"]
```

---

# 7. Employee Master

## Definition

The **Employee Master** is the central HR record created after a candidate successfully completes recruitment.

## Simple Business Flow

```text
Selected Candidate
 ↓
Employee Master
 ↓
Personal Information
 ↓
Employment Information
 ↓
Overseas Information
 ↓
Documents / Contract / Deployment
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% EMPLOYEE MASTER
    %% Central employee HR record.
    %% =========================================================

    A["Selected Candidate"]
    A --> B["Employee Master"]

    B --> C["Personal Information"]
    C --> C1["Name"]
    C --> C2["Date of Birth"]
    C --> C3["Nationality"]
    C --> C4["Contact"]
    C --> C5["Address"]

    B --> D["Employment Information"]
    D --> D1["Employee ID"]
    D --> D2["Department"]
    D --> D3["Designation"]
    D --> D4["Joining Date"]
    D --> D5["Employment Type"]

    B --> E["Overseas Information"]
    E --> E1["Country"]
    E --> E2["Client"]
    E --> E3["Deployment Status"]
    E --> E4["Current Location"]

    B --> F["Employee Documents"]
    B --> G["Employee Contract"]
    B --> H["Deployment"]
```

---

# 8. Employee Documents

## Definition

The **Employee Documents** module stores and verifies documents required for employee identity, overseas employment, immigration, medical, insurance, and compliance.

## Simple Business Flow

```text
Employee
 ↓
Documents
 ↓
Upload
 ↓
Verify
 ↓
Valid / Rejected
 ↓
Expiry Monitoring
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% EMPLOYEE DOCUMENTS
    %% Document collection and verification.
    %% =========================================================

    A["Employee"]
    A --> B["Employee Documents"]

    B --> C["Passport"]
    B --> D["Iqama"]
    B --> E["Visa"]
    B --> F["Medical"]
    B --> G["Insurance"]
    B --> H["Certificates"]
    B --> I["Employment Contract"]

    C --> J{"Documents Verified?"}
    D --> J
    E --> J
    F --> J
    G --> J

    J -->|No| K["Correction / Re-upload"]
    K --> B

    J -->|Yes| L["Verified Documents"]
    L --> M["Expiry Monitoring"]
```

---

# 9. Passport

## Definition

The **Passport** module tracks passport identity information, validity, scanned documents, and renewal status.

## Simple Business Flow

```text
Employee
 ↓
Passport
 ↓
Passport Details
 ↓
Expiry Monitoring
 ↓
Renewal if Required
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% PASSPORT
    %% Passport validity and renewal.
    %% =========================================================

    A["Employee"]
    A --> B["Passport"]

    B --> C["Passport Details"]
    C --> C1["Passport Number"]
    C --> C2["Nationality"]
    C --> C3["Issue Date"]
    C --> C4["Expiry Date"]
    C --> C5["Place of Issue"]

    B --> D["Passport Scan"]
    B --> E["Expiry Monitoring"]

    E --> F{"Expired / Expiring?"}
    F -->|No| G["Valid"]
    F -->|Yes| H["Renewal Process"]

    H --> I["New Passport"]
    I --> B
```

---

# 10. Iqama

## Definition

The **Iqama** module manages the employee's Saudi residence/work-permit record, supporting documents, verification, expiry, and renewal.

## Simple Business Flow

```text
Employee
 ↓
Iqama Record
 ↓
Documents
 ↓
Verification
 ↓
Active
 ↓
Expiry Alert
 ↓
Renewal
 ↓
New Iqama
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% IQAMA
    %% Saudi residence/work-permit lifecycle.
    %% =========================================================

    A["Employee"]
    A --> B["Iqama Record"]

    B --> C["Iqama Details"]
    C --> C1["Iqama Number"]
    C --> C2["Iqama Type"]
    C --> C3["Profession"]
    C --> C4["Sponsor"]
    C --> C5["Issue Date"]
    C --> C6["Expiry Date"]

    B --> D["Required Documents"]
    D --> D1["Passport"]
    D --> D2["Visa"]
    D --> D3["Medical"]
    D --> D4["Insurance"]
    D --> D5["Employment Contract"]

    D --> E{"Documents Verified?"}
    E -->|No| F["Correction / Re-upload"]
    F --> D
    E -->|Yes| G["Iqama Active"]

    G --> H["Expiry Monitoring"]
    H --> I{"Expiring?"}

    I -->|No| J["Continue Active"]
    I -->|Yes| K["Renewal Process"]

    K --> L["Collect Documents"]
    L --> M["Submit Renewal"]
    M --> N{"Approved?"}

    N -->|No| O["Follow Up / Correction"]
    O --> M
    N -->|Yes| P["New Iqama"]

    P --> B
```

---

# 11. Visa

## Definition

The **Visa** module manages overseas visa information, supporting documents, processing, approval, rejection, and expiry.

## Simple Business Flow

```text
Employee
 ↓
Visa Application
 ↓
Documents
 ↓
Processing
 ↓
Approval
 ↓
Visa Active
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% VISA
    %% Visa application and processing.
    %% =========================================================

    A["Employee"]
    A --> B["Visa Application"]

    B --> C["Visa Details"]
    C --> C1["Visa Number"]
    C --> C2["Visa Type"]
    C --> C3["Country"]
    C --> C4["Issue Date"]
    C --> C5["Expiry Date"]

    B --> D["Supporting Documents"]
    D --> D1["Passport"]
    D --> D2["Employment Contract"]
    D --> D3["Medical"]

    B --> E["Visa Processing"]
    E --> F{"Visa Approved?"}

    F -->|No| G["Rejected / Correction"]
    G --> E

    F -->|Yes| H["Visa Active"]
    H --> I["Expiry Monitoring"]
```

---

# 12. Employee Contract

## Definition

The **Employee Contract** represents the employment agreement between the company and the employee, including terms, compensation, assignment, and validity.

## Simple Business Flow

```text
Employee
 ↓
Employment Contract
 ↓
Terms & Compensation
 ↓
Assignment
 ↓
Active Contract
 ↓
Expiry / Renewal
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% EMPLOYEE CONTRACT
    %% Employment agreement.
    %% =========================================================

    A["Employee"]
    A --> B["Employee Contract"]

    B --> C["Employment Terms"]
    C --> C1["Contract Number"]
    C --> C2["Start Date"]
    C --> C3["End Date"]
    C --> C4["Employment Type"]
    C --> C5["Working Hours"]

    B --> D["Compensation"]
    D --> D1["Basic Salary"]
    D --> D2["Allowances"]
    D --> D3["Benefits"]
    D --> D4["Currency"]

    B --> E["Assignment"]
    E --> E1["Client"]
    E --> E2["Country"]
    E --> E3["Position"]
    E --> E4["Project / Site"]

    B --> F{"Contract Valid?"}
    F -->|Yes| G["Active Contract"]
    F -->|No| H["Renewal / New Contract"]
    H --> B
```

---

# 13. Deployment

## Definition

The **Deployment** module manages the movement and assignment of an employee to an overseas client, project, or site.

## Simple Business Flow

```text
Employee
 ↓
Deployment Record
 ↓
Documentation
 ↓
Visa
 ↓
Travel
 ↓
Arrival
 ↓
Client Joining
 ↓
Deployed
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% DEPLOYMENT
    %% Overseas employee deployment.
    %% =========================================================

    A["Employee"]
    A --> B["Deployment"]

    B --> C["Deployment Details"]
    C --> C1["Client"]
    C --> C2["JDR"]
    C --> C3["Position"]
    C --> C4["Country"]
    C --> C5["Project / Site"]
    C --> C6["Deployment Date"]

    B --> D["Documentation"]
    D --> E{"Ready for Travel?"}

    E -->|No| F["Pending Documents"]
    F --> D

    E -->|Yes| G["Travel Planning"]
    G --> H["Travel Booked"]
    H --> I["Departed"]
    I --> J["Arrived"]

    J --> K{"Joined Client?"}
    K -->|No| L["Joining Pending"]
    L --> J

    K -->|Yes| M["Deployed"]
```

---

# 14. Timesheet / Operations

## Definition

The **Timesheet / Operations** module manages the employee's work activity after deployment, including attendance, leave, hours, and billable work.

## Simple Business Flow

```text
Deployed Employee
 ↓
Client / Project
 ↓
Attendance / Leave
 ↓
Timesheet
 ↓
Working Hours
 ↓
Billing / Cost
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% TIMESHEET / OPERATIONS
    %% Post-deployment operations.
    %% =========================================================

    A["Deployed Employee"]
    A --> B["Client / Project"]

    B --> C["Attendance"]
    B --> D["Leave"]
    B --> E["Timesheet"]

    E --> F["Date"]
    E --> G["Working Hours"]
    E --> H["Activity"]
    E --> I["Billing Rate"]
    E --> J["Cost Rate"]

    E --> K{"Timesheet Approved?"}
    K -->|No| L["Correction"]
    L --> E
    K -->|Yes| M["Approved Timesheet"]

    M --> N["Client Billing"]
    M --> O["Employee Cost"]
```

---

# 15. Employee Cost

## Definition

The **Employee Cost** module calculates the total cost associated with employing and deploying a worker.

## Simple Business Flow

```text
Employee
 ↓
Salary + Benefits + Deployment Costs
 ↓
Total Employee Cost
 ↓
Client / JDR / Deployment
 ↓
Margin
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% EMPLOYEE COST
    %% Employee and deployment-related cost.
    %% =========================================================

    A["Employee"]
    A --> B["Employee Cost"]

    B --> C["Salary"]
    B --> D["Accommodation"]
    B --> E["Transport"]
    B --> F["Insurance"]
    B --> G["Visa"]
    B --> H["Medical"]
    B --> I["Travel"]
    B --> J["Other Costs"]

    C --> K["Total Employee Cost"]
    D --> K
    E --> K
    F --> K
    G --> K
    H --> K
    I --> K
    J --> K

    K --> L["Client / JDR / Deployment"]
```

---

# 16. Vendor Cost

## Definition

The **Vendor Cost** module tracks costs paid to external vendors such as recruitment agencies, medical providers, travel providers, and documentation service providers.

## Simple Business Flow

```text
Vendor
 ↓
Vendor Cost
 ↓
Cost Category
 ↓
JDR / Employee / Deployment
 ↓
Total Vendor Cost
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% VENDOR COST
    %% External supplier costs.
    %% =========================================================

    A["Vendor"]
    A --> B["Vendor Cost"]

    B --> C["Recruitment"]
    B --> D["Visa"]
    B --> E["Medical"]
    B --> F["Travel"]
    B --> G["Documentation"]
    B --> H["Commission"]
    B --> I["Other"]

    B --> J["JDR"]
    B --> K["Employee"]
    B --> L["Deployment"]

    C --> M["Total Vendor Cost"]
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

The **Client Billing** module converts client contract rates, deployments, timesheets, and other billable items into invoices and revenue.

## Simple Business Flow

```text
Client Contract
 ↓
Deployment / Timesheet
 ↓
Billing
 ↓
Invoice
 ↓
Revenue
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% CLIENT BILLING
    %% Revenue generation.
    %% =========================================================

    A["Client Contract"]
    A --> B["Billing Terms"]

    C["Deployment"] --> B
    D["Timesheet"] --> B

    B --> E["Client Billing"]

    E --> F["Employee Billing"]
    E --> G["Timesheet Billing"]
    E --> H["Fixed Charges"]
    E --> I["Other Charges"]

    F --> J["Invoice"]
    G --> J
    H --> J
    I --> J

    J --> K{"Invoice Approved?"}
    K -->|No| L["Correction"]
    L --> E
    K -->|Yes| M["Revenue"]
```

---

# 18. Margin Reporting

## Definition

The **Margin Reporting** module compares client revenue against employee, vendor, and other operational costs to determine profitability.

## Simple Business Flow

```text
Revenue
 ↓
Total Revenue
 ↓
Minus Total Cost
 ↓
Gross Profit
 ↓
Margin %
 ↓
Client / JDR / Project / Country
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% MARGIN REPORTING
    %% Profitability calculation.
    %% =========================================================

    A["Client Revenue"] --> B["Total Revenue"]

    C["Employee Cost"] --> D["Total Cost"]
    E["Vendor Cost"] --> D
    F["Other Operational Cost"] --> D

    B --> G["Gross Profit"]
    D --> G

    G --> H["Margin %"]

    H --> I["Client Margin"]
    H --> J["JDR Margin"]
    H --> K["Employee Margin"]
    H --> L["Project Margin"]
    H --> M["Country Margin"]

    M --> N["Management Dashboard"]
```

---

# 19. Expiry Management

## Definition

The **Expiry Management** module monitors employee documents and contracts and generates alerts before they expire.

## Simple Business Flow

```text
Employee Documents
 ↓
Expiry Engine
 ↓
Days Remaining
 ↓
Alert
 ↓
Renewal / Action
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% EXPIRY MANAGEMENT
    %% Centralized document expiry monitoring.
    %% =========================================================

    A["Employee Documents"]

    A --> A1["Passport"]
    A --> A2["Iqama"]
    A --> A3["Visa"]
    A --> A4["Medical"]
    A --> A5["Insurance"]
    A --> A6["Employee Contract"]

    A1 --> B["Expiry Engine"]
    A2 --> B
    A3 --> B
    A4 --> B
    A5 --> B
    A6 --> B

    B --> C{"Days Remaining"}

    C -->|More than 90| D["Valid"]
    C -->|61 - 90| E["Monitor"]
    C -->|31 - 60| F["Warning"]
    C -->|8 - 30| G["Urgent"]
    C -->|1 - 7| H["Critical"]
    C -->|Expired| I["Expired"]

    E --> J["HR Alert"]
    F --> J
    G --> J
    H --> K["Management Alert"]
    I --> K

    J --> L["Renewal / Action"]
    K --> L
```

---

# 20. Management Dashboard

## Definition

The **Management Dashboard** provides management with a consolidated view of recruitment, employees, deployment, document expiry, revenue, costs, and margins.

## Simple Business Flow

```text
ERP Data
 ↓
KPIs
 ↓
Dashboard
 ↓
Management Decisions
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% MANAGEMENT DASHBOARD
    %% Executive reporting.
    %% =========================================================

    A["ERP Data"]
    A --> B["Management Dashboard"]

    B --> C["Recruitment"]
    C --> C1["Open JDRs"]
    C --> C2["Candidates"]
    C --> C3["Selected"]
    C --> C4["Pending"]

    B --> D["Employees"]
    D --> D1["Total"]
    D --> D2["Deployed"]
    D --> D3["Available"]
    D --> D4["Processing"]

    B --> E["Deployment"]
    E --> E1["Visa Processing"]
    E --> E2["Travel Pending"]
    E --> E3["Ready"]
    E --> E4["Deployed"]

    B --> F["Document Alerts"]
    F --> F1["Passport"]
    F --> F2["Iqama"]
    F --> F3["Visa"]
    F --> F4["Contract"]

    B --> G["Commercial"]
    G --> G1["Revenue"]
    G --> G2["Employee Cost"]
    G --> G3["Vendor Cost"]
    G --> G4["Gross Profit"]
    G --> G5["Margin %"]
```

---

# 21. Complete System Architecture

## Definition

The **Complete System Architecture** shows how the major modules connect from the initial client requirement through recruitment, HR, documentation, deployment, operations, costing, billing, alerts, and management reporting.

## Simple Business Flow

```text
Organization
 ↓
Client
 ↓
Contract
 ↓
JDR
 ↓
Recruitment
 ↓
Employee
 ↓
Documents
 ↓
Deployment
 ↓
Operations
 ↓
Cost / Billing
 ↓
Margin
 ↓
Dashboard
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% COMPLETE OVERSEAS MANPOWER ERP
    %% =========================================================

    A["Organization"]
    A --> B["Users & Roles"]
    B --> C["Clients & Vendors"]
    C --> D["Client Contract"]
    D --> E["JDR"]

    E --> F["Overseas Recruitment"]
    F --> G["Employee Master"]

    G --> H["Employee Documents"]
    H --> H1["Passport"]
    H --> H2["Iqama"]
    H --> H3["Visa"]
    H --> H4["Medical"]
    H --> H5["Insurance"]

    G --> I["Employee Contract"]
    G --> J["Deployment"]

    J --> K["Client / Project / Site"]
    K --> L["Timesheet / Operations"]

    G --> M["Employee Cost"]
    C --> N["Vendor Cost"]

    L --> O["Client Billing"]
    J --> O
    I --> O

    M --> P["Margin"]
    N --> P
    O --> P

    H --> Q["Expiry Management"]
    I --> Q

    P --> R["Management Dashboard"]
    Q --> R
    F --> R
    J --> R
```

---

# 22. Recommended Implementation Order

## Definition

The **Implementation Order** shows which modules should be built first based on their data dependencies.

## Simple Business Flow

```text
Foundation
 ↓
Masters
 ↓
Recruitment
 ↓
Employee
 ↓
Documents
 ↓
Deployment
 ↓
Operations
 ↓
Commercial
 ↓
Alerts
 ↓
Dashboard
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% IMPLEMENTATION ORDER
    %% Build from foundation to reporting.
    %% =========================================================

    A["1. Organization"]
    A --> B["2. Users & Roles"]
    B --> C["3. Clients & Vendors"]
    C --> D["4. Client Contract"]
    D --> E["5. JDR"]
    E --> F["6. Overseas Recruitment"]
    F --> G["7. Employee Master"]
    G --> H["8. Employee Documents"]
    H --> I["9. Passport / Iqama / Visa"]
    I --> J["10. Employee Contract"]
    J --> K["11. Deployment"]
    K --> L["12. Timesheet / Operations"]
    L --> M["13. Employee / Vendor Cost"]
    M --> N["14. Client Billing / Margin"]
    N --> O["15. Expiry Management"]
    O --> P["16. Management Dashboard"]
```

---

# 23. Core Business Flow

## Definition

The **Core Business Flow** represents the company's main business journey from receiving an overseas manpower requirement to generating revenue and monitoring employee documents.

## Simple Business Flow

```text
Client
 ↓
Contract
 ↓
JDR
 ↓
Recruitment
 ↓
Employee
 ↓
Documentation
 ↓
Deployment
 ↓
Timesheet
 ↓
Billing
 ↓
Margin
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% CORE BUSINESS FLOW
    %% Main overseas manpower business process.
    %% =========================================================

    A["Client"]
    A --> B["Client Contract"]
    B --> C["JDR"]
    C --> D["Overseas Recruitment"]
    D --> E["Candidate"]

    E --> F{"Selected?"}
    F -->|No| G["Rejected / Hold"]
    F -->|Yes| H["Employee"]

    H --> I["Documentation"]
    I --> J{"Ready for Deployment?"}

    J -->|No| K["Pending Requirements"]
    K --> I

    J -->|Yes| L["Deployment"]
    L --> M["Client / Site"]
    M --> N["Timesheet"]

    N --> O["Client Billing"]
    H --> P["Employee Cost"]
    M --> Q["Vendor Cost"]

    O --> R["Revenue"]
    P --> S["Total Cost"]
    Q --> S

    R --> T["Profit / Margin"]
```

---

# 24. Key Data Relationships

## Definition

The **Key Data Relationships** show how the main records are connected. These links are important for traceability and reporting.

## Simple Business Flow

```text
Client
 ↓
Contract
 ↓
JDR
 ↓
Candidate
 ↓
Employee
 ↓
Documents / Contract
 ↓
Deployment
 ↓
Operations
 ↓
Cost / Billing
 ↓
Margin
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% KEY DATA RELATIONSHIPS
    %% Main records and their relationships.
    %% =========================================================

    A["Client"]
    A --> B["Client Contract"]
    B --> C["JDR"]
    C --> D["Candidate"]
    D --> E["Employee"]

    E --> F["Passport"]
    E --> G["Iqama"]
    E --> H["Visa"]
    E --> I["Medical"]
    E --> J["Insurance"]
    E --> K["Employee Contract"]

    C --> L["Deployment"]
    E --> L
    A --> L

    L --> M["Client Project / Site"]
    M --> N["Timesheet"]

    E --> O["Employee Cost"]
    A --> P["Vendor"]
    P --> Q["Vendor Cost"]

    N --> R["Client Billing"]
    L --> R

    O --> S["Total Cost"]
    Q --> S

    R --> T["Revenue"]
    S --> U["Margin"]
    T --> U

    F --> V["Expiry Management"]
    G --> V
    H --> V
    I --> V
    J --> V
    K --> V

    U --> W["Management Dashboard"]
    V --> W
```

---

# 25. Final Dependency Chain

## Definition

The **Final Dependency Chain** is the shortest representation of the complete ERP dependency structure.

## Simple Business Flow

```text
Organization
 ↓
Users
 ↓
Client
 ↓
Contract
 ↓
JDR
 ↓
Candidate
 ↓
Employee
 ↓
Documents
 ↓
Deployment
 ↓
Operations
 ↓
Cost
 ↓
Billing
 ↓
Margin
 ↓
Alerts
 ↓
Dashboard
```

## Mermaid

```mermaid
flowchart TD
    %% =========================================================
    %% FINAL DEPENDENCY CHAIN
    %% High-level system dependency.
    %% =========================================================

    A["Organization"]
    A --> B["Users"]
    B --> C["Client"]
    C --> D["Client Contract"]
    D --> E["JDR"]
    E --> F["Candidate"]
    F --> G["Employee"]
    G --> H["Documents"]
    H --> I["Iqama / Visa / Passport"]
    I --> J["Employee Contract"]
    J --> K["Deployment"]
    K --> L["Timesheet / Operations"]
    L --> M["Cost"]
    M --> N["Billing"]
    N --> O["Margin"]
    O --> P["Expiry Alerts"]
    P --> Q["Management Dashboard"]
```

---

# Design Principle

Every module follows the same documentation pattern:

```text
Definition
     ↓
Simple Business Flow
     ↓
Vertical Mermaid
     ↓
Decision / Yes-No Branches where required
```

The main system principle is:

```text
Client
 ↓
Contract
 ↓
JDR
 ↓
Overseas Recruitment
 ↓
Employee
 ↓
Documents
 ↓
Deployment
 ↓
Operations
 ↓
Cost + Billing
 ↓
Margin
 ↓
Expiry Alerts
 ↓
Management Dashboard
```
