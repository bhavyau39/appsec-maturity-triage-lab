## 2026-02-14 – Nessus Scan 1 and curated findings

- Ran a Basic Network Scan in Nessus Essentials against the Azure static website host `appseclabstorage01.z13.web.core.windows.net` (port 443).
- Scan surfaced 4 findings: 1 High (SWEET32 / medium-strength ciphers), 2 Medium (TLS 1.0 and TLS 1.1 enabled), 1 Info (HTTP methods allowed).
- Since Nessus Essentials cannot export CSV, manually curated these findings into `data/nessus_findings.xlsx` with:
  - Severity, host, port, OWASP area, and a one-line business impact.
- This dataset is used later for Azure DevOps work items and Power BI dashboards.


## 2026-02-14 – Application security maturity model

- Created `data/AppSec_Maturity_Model.xlsx` with a simple 1–5 scoring model inspired by OWASP ASVS.
- Defined maturity for:
  - Cryptography / TLS
  - Secure Configuration
  - Logging & Monitoring
  - Authentication & Session Management
  - Input Validation & Output Encoding
  - Deployment & Change Management
- Scored current vs target levels and documented evidence, gaps, and next steps for each area.
- Used Nessus findings (SWEET32 and deprecated TLS versions) as evidence for weaker Cryptography/TLS and Secure Configuration maturity.

## 2026-02-15 – Azure DevOps board for vulnerability triage

- Created Azure DevOps project `appsec-maturity-lab`.
- Used the default **To Do / Doing / Done** board to track Nessus findings for the Azure static site.
- Created one work item per curated finding from `data/nessus_findings.xlsx`:
  - Disable 3DES / medium-strength TLS ciphers (SWEET32) – High
  - Disable deprecated TLS 1.0 on static site endpoint – Medium
  - Disable deprecated TLS 1.1 on static site endpoint – Medium
  - Review HTTP methods allowed on root path – Informational
- Mapped them on the board as:
  - **To Do**: TLS 1.1 deprecation work
  - **Doing**: SWEET32 and TLS 1.0 remediation
  - **Done**: HTTP methods informational review
- Screenshot: `docs/screenshots/DEVOPS-01_BoardOverview.png`

