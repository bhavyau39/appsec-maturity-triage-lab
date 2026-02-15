# Architecture Overview

## Goal

Simulate how an enterprise security team would manage application security for an Azure-hosted web application:
- Assess **maturity** of key application security practices.
- Collect **vulnerability data** from Nessus.
- Triage and track remediation using **Azure DevOps Boards**.
- Visualize maturity and vulnerability data in **Power BI**.

## High-Level Components

- **Azure Storage Static Website**  
  Hosts a simple sample web application (HTML page) used as the target.

- **Nessus Essentials**  
  Runs external scans against the Azure endpoint and surfaces vulnerabilities.

- **Curated Findings Dataset (Excel)**  
  Manual curation of key Nessus findings into a structured table with added context:
  - OWASP area
  - Business impact
  - Status

- **Application Security Maturity Model (Excel)**  
  Simple maturity scores (1–5) across key OWASP ASVS-inspired areas.

- **Azure DevOps Boards**  
  Each curated finding becomes a Bug work item. A Kanban board tracks status:
  - New → Triaged → In Progress → Resolved.

- **Power BI Dashboard**  
  Combines the findings dataset and maturity model to show:
  - Vulnerabilities by severity and area.
  - Current vs target maturity scores per area.

## Logical Diagram

```text
                           +---------------------------+
                           |   Nessus Essentials       |
                           |  - Scan Azure web app     |
                           |  - Surface vulnerabilities|
                           +-------------+-------------+
                                         |
                         Curated findings (Excel) + context
                                         |
                                         v
+-------------------+           +---------------------------+
| Azure Static Site |           |  Findings Dataset (Excel) |
|  (Storage Account)|<--------->+  Maturity Model (Excel)   |
+---------+---------+           +-------------+-------------+
          ^                                   |
          |                                   |
          |           +-----------------------+--------------------+
          |           |                                            |
          v           v                                            v
   Public HTTPS   Power BI Desktop                          Azure DevOps Boards
   Endpoint       - Severity & area charts                  - One bug per finding
                  - Maturity charts                         - Triage workflow
