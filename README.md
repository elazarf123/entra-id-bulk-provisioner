# ☁️ Microsoft Entra ID: Bulk User Provisioning Automation

## 📌 Project Overview
This project is an enterprise-grade IT automation script built with Python and the Microsoft Graph API. It is designed to programmatically handle bulk employee onboarding by automating the creation of user identities in Microsoft Entra ID (formerly Azure AD). 

By replacing manual data entry with an automated pipeline, this tool significantly reduces administrative overhead, minimizes human error, and ensures strict adherence to security and compliance protocols from day one.

## 🚀 Business Value & Impact
* **Operational Efficiency:** Automates the ingestion of structured HR data (CSV) to instantly provision multiple user accounts.
* **Automated Licensing:** Programmatically assigns specific Microsoft 365 licenses (e.g., E3/E5) to new users upon creation, ensuring immediate access to necessary productivity tools.
* **Security & Zero-Trust:** Leverages Python's cryptographically secure `secrets` module to generate robust, randomized temporary passwords. It automatically flags accounts to force a password reset upon the user's initial login, adhering to Zero-Trust identity principles.
* **Resilient Architecture:** Built with robust error handling (`try/except`) to ensure that a failure in one row (e.g., a duplicate email address) does not halt the entire batch execution.

## 🛠️ Technology Stack
* **Language:** Python 3.10+
* **Authentication:** App-Only (Client Credentials flow) via `azure-identity`
* **API:** Microsoft Graph API (`msgraph-sdk`)
* **Core Modules:** `csv`, `asyncio`, `secrets`, `uuid`, `os`

## ⚙️ Prerequisites & Setup
To run this script in a live Microsoft 365 environment, you must configure an App Registration in the Microsoft Entra admin center with the following:
1. **API Permissions:** `User.ReadWrite.All` (Application permission with Admin Consent granted).
2. **Environment Variables:** You must securely export the following credentials to your local environment (never hardcode them into the script):
   * `TENANT_ID`
   * `CLIENT_ID`
   * `CLIENT_SECRET`

## 💻 Usage Instructions
1. Clone the repository to your local machine.
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
