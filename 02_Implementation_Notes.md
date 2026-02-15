## 2026-02-14 – Nessus Scan 1 and curated findings

- Ran a Basic Network Scan in Nessus Essentials against the Azure static website host `appseclabstorage01.z13.web.core.windows.net` (port 443).
- Scan surfaced 4 findings: 1 High (SWEET32 / medium-strength ciphers), 2 Medium (TLS 1.0 and TLS 1.1 enabled), 1 Info (HTTP methods allowed).
- Since Nessus Essentials cannot export CSV, manually curated these findings into `data/nessus_findings.xlsx` with:
  - Severity, host, port, OWASP area, and a one-line business impact.
- This dataset is used later for Azure DevOps work items and Power BI dashboards.
