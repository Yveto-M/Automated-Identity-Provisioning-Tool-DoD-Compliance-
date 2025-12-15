# Automated Identity Provisioning Tool (DoD Compliance)

## 📌 Project Overview
**Role:** Identity Management Specialist (DoD Work Role 661)
**Scenario:**
To support the "Thunderdome" Zero Trust initiative, the organization required the rapid onboarding of defense contractors. Manual creation of accounts was rejected due to the risk of human error and strict auditing requirements for clearance levels.

**The Solution:**
I engineered a PowerShell automation tool to ingest HR data and provision Active Directory identities in bulk. The tool enforces strict naming conventions and attribute mapping required for federal compliance audits.

## 📸 Proof of Compliance (Validation)
*Below: Verification of the "Contractor" OU in Active Directory. Note the correct naming convention (`ctr.firstname.lastname`) and the audit-ready Description fields (`Clearance Level` + `Role`).*

![Active Directory Validation]<img width="696" height="360" alt="proof-of-onboard" src="https://github.com/user-attachments/assets/69b1ddda-896f-40c3-8b18-af99daadf675" />


## ⚙️ Technical Features
* **Input Validation:** Ingests CSV data to minimize manual entry errors.
* **Compliance Tagging:** Automatically prefixes contractor usernames with `ctr.` to distinguish non-employee accounts (NIST 800-53 IA-2).
* **Attribute Mapping:** Dynamically concatenates `Clearance Level` and `Job Title` into the AD `Description` field for easy auditing by Security Officers.
* **Error Handling:** Implements `Try/Catch` blocks to log failures without stopping the entire batch process.
* **Security:** Uses `SecureString` conversion to handle default credentials safely during transit.

## 🚀 Execution Output
*Below: The script running in the Nylabs Federal environment, successfully parsing the CSV and provisioning users with zero errors.*

![PowerShell Execution]<img width="963" height="662" alt="powershell script" src="https://github.com/user-attachments/assets/4c53712f-e4c1-41a4-93f5-e05fb97ee107" />


## 🛠️ Technology Stack
* **Language:** PowerShell 
* **Target System:** Windows Server 2022 (Active Directory Domain Services)
* **Standards:** NIST 800-53 (Identification & Authentication), RBAC

## 📸 Usage
```powershell
# 1. Inspect the CSV for accuracy
Import-Csv "C:\Scripts\contractors.csv"

# 2. Execute the provisioning script
.\New-FederalHires.ps1
