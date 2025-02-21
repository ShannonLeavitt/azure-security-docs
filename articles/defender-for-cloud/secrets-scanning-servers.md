---
title: Protecting VM secrets with Microsoft Defender for Cloud
description: Learn how to protect VM secrets with Defender for Server's agentless secrets scanning in Microsoft Defender for Cloud.
ms.topic: overview
ms.date: 02/19/2025
---


# Machine secrets scanning

Microsoft Defender for Cloud provides [secrets scanning](secrets-scanning.md) in a number of scenarios, including scanning for machine secrets.

Machine secrets scanning is provided as one of Defender for Cloud's [agentless scanning features](concept-agentless-data-collection.md) that improve machine security posture. Agentless scanning doesn't need any installed agents or network connectivity, and doesn't effect machine performance.

- Agentless machine secrets scanning for helps you to quickly detect, prioritize, and remediate exposed plaintext secrets in your environment.
- If secrets are detected, findings help security teams to prioritize actions, and remediate to minimize the risk of lateral movement.
- Scanning machines for [supported secrets](secrets-scanning.md#secrets-support) is available when Defender for Servers Plan 2, or the Defender Cloud Security Posture Management (CSPM) plan is enabled.
- Machine secrets scanning can scan Azure VMs, and AWS/GCP instances connected to Defender for Cloud.

## Reducing security risk

Secrets scanning helps reduce risk by:

- Eliminating secrets that aren’t needed.
- Applying the principle of least privilege.
- Strengthening secrets security by using secrets management systems such as Azure Key Vault.
- Using short-lived secrets such as substituting Azure Storage connection strings with SAS tokens that possess shorter validity periods.

## How machine secrets scanning works

Secrets scanning for VMs is agentless and uses cloud APIs. Here's how it works:

1. Secrets scanning captures disk snapshots and analyses them, with no impact on VM performance.
2. After the Microsoft secrets scanning engine collects secrets metadata from disk, it sends them to Defender for Cloud.
3. The secrets scanning engine verifies whether SSH private keys can be used to move laterally in your network.
    - SSH keys that aren’t successfully verified are categorized as unverified on the Defender for Cloud **Recommendations** page.
    - Directories recognized as containing test-related content are excluded from scanning.

## Machine secrets recommendations

The following machine secrets security recommendations are available:

- Azure resources: Machines should have secrets findings resolved
- AWS resources: EC2 instances should have secrets findings resolved
- GCP resources: VM instances should have secrets findings resolved

## Machine secrets attack paths

The table summarizes supported attack paths.

**VM** | **Attack paths**
--- | ---
Azure | Exposed Vulnerable VM has an insecure SSH private key that is used to authenticate to a VM.<br/>Exposed Vulnerable VM has insecure secrets that are used to authenticate to a storage account.<br/>Vulnerable VM has insecure secrets that are used to authenticate to a storage account.<br/>Exposed Vulnerable VM has insecure secrets that are used to authenticate to an SQL server.
AWS | Exposed Vulnerable EC2 instance has an insecure SSH private key that is used to authenticate to an EC2 instance.<br/>Exposed Vulnerable EC2 instance has an insecure secret that is used to authenticate to a storage account.<br/>Exposed Vulnerable EC2 instance has insecure secrets that are used to authenticate to an AWS RDS server.<br/>Vulnerable EC2 instance has insecure secrets that are used to authenticate to an AWS RDS server.
GCP | Exposed Vulnerable GCP VM instance has an insecure SSH private key that is used to authenticate to a GCP VM instance.

## Predefined cloud security explorer queries

Defender for Cloud provides these predefined queries for investigating secrets security issues:

- VM with plaintext secret that can authenticate to another VM - Returns all Azure VMs, AWS EC2 instances, or GCP VM instances with plaintext secret that can access other VMs or EC2s.
- VM with plaintext secret that can authenticate to a storage account - Returns all Azure VMs, AWS EC2 instances, or GCP VM instances with plaintext secret that can access storage accounts
- VM with plaintext secret that can authenticate to an SQL database - Returns all Azure VMs, AWS EC2 instances, or GCP VM instances with plaintext secret that can access SQL databases.

## Investigating and remediating machine secrets

You can investigate machine secrets findings in Defender for Cloud using a number of method. Not all methods are available for all secrets. [Review supported methods](secrets-scanning.md#secrets-support) for different types of secrets.

## Related content

[Investigate and remediate machine secrets](remediate-server-secrets.md).
