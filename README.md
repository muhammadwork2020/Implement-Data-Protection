# AZ-Lab: Implement Data Protection

This lab demonstrates how to implement backup and disaster recovery for Azure virtual machines using Recovery Services vaults, backup policies, and Azure Site Recovery. It includes infrastructure deployment, backup configuration, monitoring, and replication across regions.

## 🧭 Lab Overview

- **Lab Duration:** ~50 minutes  
- **Azure Services Used:**  
  - Recovery Services Vault  
  - Azure Backup  
  - Azure Site Recovery  
  - Storage Accounts  
- **Regions Used:** East US (primary), West US (secondary)  
- **VM Name:** `az104-10-vm0`  
- **Resource Groups:**  
  - `az104-rg-region1` (East US)  
  - `az104-rg-region2` (West US)

---

## 🧱 Tasks Breakdown

### Task 1: Provision Infrastructure via Template
Deploy a virtual machine and virtual network using a custom ARM template.

- **Template:** `az104-10-vms-edge-template.json`  
- **Parameters:** `az104-10-vms-edge-parameters.json`  
- **Resource Group:** `az104-rg-region1`  
- **Region:** East US

### Task 2: Create Recovery Services Vault
Create a vault to store VM backup data.

- **Vault Name:** `az104-rsv-region1`  
- **Region:** East US  
- **Soft Delete:** Enabled (14-day retention)  
- **Replication Type:** Geo-redundant

### Task 3: Configure VM-Level Backup
Enable backup for `az104-10-vm0` using a custom policy.

- **Policy Name:** `az104-backup`  
- **Frequency:** Daily at 12:00 AM  
- **Retention:** 2 days (instant recovery snapshot)

### Task 4: Monitor Azure Backup
Deploy a storage account and configure diagnostic settings.

- **Storage Account:** Globally unique name in East US  
- **Logs Enabled:**  
  - Azure Backup Reporting  
  - Backup Job & Alert Data  
  - Site Recovery Jobs & Events  
- **Destination:** Archive to storage account

### Task 5: Enable VM Replication
Configure disaster recovery by replicating VM to West US.

- **Vault Name:** `az104-rsv-region2`  
- **Region:** West US  
- **Automation Account:** Created during setup  
- **Replication Status:** Healthy → Protected

---


