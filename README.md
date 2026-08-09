# Enterprise Secure Hybrid Application Architecture  
**Contoso BioResearch Ltd. – Project**

## Overview
This repository contains the complete architecture, decision rationale, infrastructure-as-code outline, and cost estimate for a secure, hybrid-identity, multi-tier web application platform on Microsoft Azure.

The design delivers:
- Hybrid identity with Microsoft Entra ID
- Secure multi-tier web application
- Highly available relational database
- Private networking (hub-spoke + Private Link)
- Full backup + disaster recovery
- End-to-end monitoring & governance
- Cost-optimized configuration

All decisions map explicitly to the Azure Well-Architected Framework pillars and the Cloud Adoption Framework.

## Repository Structure
- `/docs/Architecture-Decision-Record.md` – Full decision document with WAF pillar references
- `/docs/Architecture-Diagram.md` – Text + Mermaid diagram (exportable to draw.io / Visio)
- `/infra/main.bicep` – High-level Bicep outline
- `/infra/modules/` – Placeholder module structure
- `/cost/Cost-Estimate.md` – Pricing Calculator assumptions and monthly estimate
- `README.md` – This file

## How to Use
1. Review the Architecture Decision Record first.
2. Open the Mermaid diagram in any Mermaid live editor or import into draw.io.
3. Deploy the Bicep outline into a test subscription after filling in parameters.
4. Recalculate costs in the Azure Pricing Calculator using the exact SKUs listed.

## Author
KANISURU DANIEL  
Date: August 2026
