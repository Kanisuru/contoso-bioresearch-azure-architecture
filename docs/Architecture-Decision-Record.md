Title: Contoso BioResearch - Enterprise Secure Hybrid Application Architecture
Status: Final
Context: Contoso requires a hybrid-identity, multi-tier research portal that is secure by default, highly available, recoverable within aggressive RTO/RPO targets, fully governed, and cost-efficient.

2.1 Identity - Hybrid Identity
Choice: Microsoft Entra ID + Entra Connect (Password Hash Sync) + Conditional Access + Privileged Identity Management + B2B for partners.
Why:
- Existing on-premises Active Directory must remain the source of truth for employees.
- Password Hash Sync is the simplified, most resilent hybrid model (Well-Achitected: Reliability & Operational Excellence).
- Conditional Access + PIM enforce least privilege and just-in time admin access (Security pillar).
- B2B guest accounts allow external research partners without creating new credentials.
