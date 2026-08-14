# 🆔 Entra ID Bulk User Provisioning & Identity Automation

[![Python 3.11](https://img.shields.io/badge/python-3.11-blue.svg)](https://www.python.org/downloads/)
[![Microsoft Graph API](https://img.shields.io/badge/Microsoft%20Graph-SDK%20v1.0-0078D4.svg)](https://learn.microsoft.com/graph/)
[![Entra ID](https://img.shields.io/badge/Identity-Microsoft%20Entra%20ID-blue.svg)](https://entra.microsoft.com/)
[![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub%20Actions-2088FF.svg)](https://github.com/features/actions)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Enterprise identity lifecycle management automation for **Microsoft Entra ID (Azure AD)** using **Python**, the **Microsoft Graph API**, and **GitHub Actions**.

Automates bulk user onboarding, licensing, departmental group assignment, and attribute validation while enforcing **Least Privilege** and **Zero Trust** identity standards.

---

## 📐 Architecture & Identity Workflow

```mermaid
graph TD
    HR[HR Roster / CSV / JSON Feed] -->|Validated Ingestion| SchemaCheck[Schema & UPN Validator]
    SchemaCheck -->|OAuth 2.0 Client Creds| MSGraph[Microsoft Graph API Endpoint]
    
    subgraph Provisioning Pipeline
        MSGraph --> Create[Create Entra ID User Object]
        Create --> GroupAssign[Assign Dynamic / Security Groups]
        GroupAssign --> License[Assign Microsoft 365 License SKU]
        License --> MFAFlag[Enforce Registration Campaign / MFA]
    end

    subgraph Audit & Governance
        Create --> AuditLog[Structured Audit Log / JSON]
        AuditLog --> SIEM[SIEM / Azure Monitor Ingestion]
    end
