# Vulnerability Triage Playbook (Lab)

## Purpose
Turn raw Nessus output into prioritized, trackable work items that map back to application security maturity.

## Steps

1. **Curate Nessus findings**
   - Review Nessus Scan 1 results for the Azure static site.
   - Select findings worth tracking (High/Medium and relevant Info).
   - Record each in `data/nessus_findings.xlsx` with Severity, OWASP_Area, Business_Impact, and Status.

2. **Create Azure DevOps work items**
   - For each curated finding, create an Issue in Azure DevOps:
     - Title: short, action-oriented summary.
     - Description: key details from Nessus, impact, and recommended fix.
     - Severity/Priority: based on Nessus severity and business context.
   - Note `Finding_ID` in the description to link back to the Excel row.

3. **Use the board to drive work**
   - **To Do**: new / untriaged findings.
   - **Doing**: items being analysed or fixed.
   - **Done**: verified as resolved or accepted risk.
   - Move cards across the board as remediation progresses.

4. **Verify and close**
   - After changing configuration (e.g., TLS settings), re-scan or verify manually.
   - If the finding no longer appears, leave the card in **Done** and document how it was validated.
