#  Enterprise Hybrid Infrastructure Project

[![Azure](https://img.shields.io/badge/Azure-0078D4?style=for-the-badge&logo=microsoft-azure&logoColor=white)](https://azure.microsoft.com)
[![Windows Server](https://img.shields.io/badge/Windows_Server_2025-0078D6?style=for-the-badge&logo=windows&logoColor=white)](https://www.microsoft.com/windows-server)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

> A production-ready hybrid cloud infrastructure demonstrating enterprise-level integration between Windows Server 2025 and Azure services, featuring identity management, file synchronization, and comprehensive security monitoring.

##  Table of Contents

- [Overview](#overview)
- [Architecture](#architecture)
- [Key Features](#key-features)
- [Technologies Used](#technologies-used)
- [Project Components](#project-components)
- [Implementation Timeline](#implementation-timeline)
- [Getting Started](#getting-started)
- [Documentation](#documentation)
- [Demo](#demo)
- [Cost Analysis](#cost-analysis)
- [Skills Demonstrated](#skills-demonstrated)
- [Lessons Learned](#lessons-learned)
- [Future Enhancements](#future-enhancements)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

##  Overview

This project showcases a comprehensive hybrid cloud infrastructure that bridges on-premises Windows Server 2025 with Microsoft Azure cloud services. It demonstrates enterprise-grade implementations of identity management, storage solutions, and security operations - skills directly applicable to real-world IT environments.

**Business Value:**
- Seamless identity synchronization between on-premises and cloud
- Cost-effective storage with intelligent cloud tiering
- Advanced threat detection and automated incident response
- Disaster recovery capabilities with minimal RTO/RPO
- Scalable infrastructure ready for production deployment

##  Architecture

![Architecture Diagram](./diagrams/architecture-overview.png)

### High-Level Design
```
┌─────────────────────────────────────────────────────────────────────┐
│                     ON-PREMISES ENVIRONMENT                          │
│  (Windows Server 2025 - Simulated in Azure VM)                      │
│                                                                      │
│  ┌──────────────────────┐        ┌──────────────────────┐         │
│  │  Domain Controller   │        │   File Server        │         │
│  │  - Active Directory  │◄──────►│  - Shared Folders    │         │
│  │  - DNS Server        │        │  - NTFS Permissions  │         │
│  │  - Azure AD Connect  │        │  - File Sync Agent   │         │
│  └──────────┬───────────┘        └──────────┬───────────┘         │
│             │                                 │                      │
└─────────────┼─────────────────────────────────┼──────────────────────┘
              │ Sync                           │ Sync
              ▼                                 ▼
┌─────────────────────────────────────────────────────────────────────┐
│                        AZURE CLOUD                                   │
│                                                                      │
│  ┌──────────────────────┐        ┌──────────────────────┐         │
│  │    Azure AD          │        │   Azure Files        │         │
│  │  - Synced Users      │        │  - Cloud Storage     │         │
│  │  - Conditional Access│        │  - Tiered Files      │         │
│  │  - MFA               │        │  - Backup & DR       │         │
│  └──────────┬───────────┘        └──────────────────────┘         │
│             │                                                        │
│             ▼                                                        │
│  ┌──────────────────────────────────────────────────────┐         │
│  │           SECURITY & MONITORING                       │         │
│  │  ┌────────────┐  ┌──────────────┐  ┌──────────┐    │         │
│  │  │Log Analytics│  │Microsoft     │  │ Sentinel │    │         │
│  │  │ Workspace  │◄─┤Defender for  │◄─┤   SIEM   │    │         │
│  │  └────────────┘  │  Cloud       │  └──────────┘    │         │
│  │                  └──────────────┘                    │         │
│  └──────────────────────────────────────────────────────┘         │
└─────────────────────────────────────────────────────────────────────┘
```

##  Key Features

###  Hybrid Identity Management
- **Azure AD Connect** synchronizing on-premises Active Directory with Azure AD
- **Multi-Factor Authentication (MFA)** for enhanced security
- **Conditional Access Policies** enforcing location and device compliance
- **Self-Service Password Reset (SSPR)** with password writeback
- **Hybrid Azure AD Join** for seamless device management

###  Intelligent File Services
- **Azure File Sync** providing bidirectional file synchronization
- **Cloud Tiering** automatically moving cold data to Azure (60% storage savings)
- **Disaster Recovery** with sub-5-minute RTO using direct Azure Files access
- **Automated Backup** with point-in-time recovery
- **Multi-site sync** capability for distributed organizations

###  Security Operations Center (SOC)
- **Azure Sentinel** SIEM with threat intelligence
- **Microsoft Defender for Cloud** providing vulnerability assessment
- **Automated Threat Detection** with 15+ analytics rules
- **Playbook-based Response** automatically disabling compromised accounts
- **UEBA (User and Entity Behavior Analytics)** for anomaly detection
- **Custom KQL Queries** for threat hunting

###  Monitoring & Compliance
- **Real-time Dashboards** showing security posture
- **Custom Workbooks** visualizing identity and file access patterns
- **Automated Alerts** for security events and performance issues
- **Audit Logging** for compliance requirements
- **Just-In-Time VM Access** reducing attack surface

##  Technologies Used

**On-Premises (Simulated in Azure)**
- Windows Server 2025 Datacenter
- Active Directory Domain Services (AD DS)
- File and Storage Services
- Azure AD Connect
- Azure File Sync Agent
- Azure Monitor Agent

**Microsoft Azure**
- Azure Active Directory (Entra ID)
- Azure Files & Storage Sync Service
- Log Analytics Workspace
- Azure Monitor
- Microsoft Defender for Cloud
- Azure Sentinel
- Azure Logic Apps (Playbooks)
- Azure Backup & Recovery Services Vault

**Languages & Tools**
- PowerShell (automation scripts)
- Kusto Query Language (KQL) for log analytics
- Azure Resource Manager (ARM) / Bicep templates
- Git / GitHub for version control

##  Project Components

### 1. Identity Management
- [x] Active Directory forest with 15+ test users
- [x] Organizational Units (OUs) structure
- [x] Azure AD Connect with delta sync
- [x] 5 Conditional Access policies
- [x] MFA enabled for privileged accounts
- [x] SSPR with password writeback

### 2. Storage & File Services
- [x] Windows File Server with departmental shares
- [x] Azure File Sync with 4 sync groups
- [x] Cloud tiering (20% free space policy)
- [x] Automated daily backups
- [x] Disaster recovery testing

### 3. Security Monitoring
- [x] Log Analytics collecting 10+ data sources
- [x] 15+ Sentinel analytics rules
- [x] 3 custom threat hunting queries
- [x] 5+ automated response playbooks
- [x] Security workbooks and dashboards

##  Implementation Timeline

| Week | Phase | Key Deliverables |
|------|-------|------------------|
| 1 | Foundation Setup | Windows Server deployed, AD configured |
| 2 | Hybrid Identity | Azure AD Connect, MFA, Conditional Access |
| 3 | File Services | File Sync configured, cloud tiering enabled |
| 4 | Security Monitoring | Log Analytics, Defender, alerts configured |
| 5 | Advanced Security | Sentinel deployed, playbooks created |
| 6 | Testing & Documentation | All tests passed, docs complete, demo ready |

**Total Time Investment:** ~60-80 hours over 6 weeks

##  Getting Started

### Prerequisites
```
 Azure subscription (free trial works)
 Basic understanding of Active Directory
 Familiarity with Windows Server administration
 PowerShell knowledge (basic level)
```

### Quick Start

1. **Clone this repository**
```bash
   git clone https://github.com/yourusername/hybrid-infrastructure.git
   cd hybrid-infrastructure
```

2. **Review the implementation guide**
```bash
   # Read the full guide
   cat IMPLEMENTATION.md
```

3. **Deploy the infrastructure**
   - Follow the week-by-week guide in [IMPLEMENTATION.md](./IMPLEMENTATION.md)
   - Use the provided PowerShell scripts in `/scripts`
   - Deploy Azure resources using templates in `/templates`

4. **Configure and test**
   - Execute test scenarios from [TESTING.md](./TESTING.md)
   - Verify all components are functioning
   - Review security configurations

### Deployment Scripts
```powershell
# Example: Create AD users from CSV
.\scripts\Create-ADUsers.ps1 -CSVPath .\data\users.csv

# Example: Configure file shares
.\scripts\Configure-FileShares.ps1 -ShareConfig .\config\shares.json

# Example: Deploy Azure infrastructure
az deployment group create --resource-group RG-HybridLab \
  --template-file .\templates\main.bicep
```

##  Documentation

| Document | Description |
|----------|-------------|
| [IMPLEMENTATION.md](./IMPLEMENTATION.md) | Complete step-by-step implementation guide |
| [TESTING.md](./TESTING.md) | Test scenarios and validation procedures |
| [SECURITY.md](./SECURITY.md) | Security controls and incident response |
| [COST-ANALYSIS.md](./COST-ANALYSIS.md) | Detailed cost breakdown and optimization |
| [TROUBLESHOOTING.md](./TROUBLESHOOTING.md) | Common issues and solutions |

##  Demo

**Live Demo Video:** [Watch on YouTube](#)

**Demo Highlights:**
-  User synchronization from on-premises to Azure AD
-  Multi-factor authentication in action
-  File sync between on-premises and Azure Files
-  Cloud tiering automatically freeing up local storage
-  Security incident detection and automated response
-  Sentinel workbooks visualizing security posture

##  Cost Analysis

### Development Environment (Optimized)
| Resource | Monthly Cost |
|----------|--------------|
| VMs (with auto-shutdown) | $23 |
| Azure Storage (200GB) | $10 |
| Log Analytics + Sentinel | $15 |
| Backup Storage | $5 |
| **Total** | **~$53/month** |

### Production Environment (Estimated)
| Resource | Monthly Cost |
|----------|--------------|
| Highly Available VMs (4x) | $760 |
| Azure Storage (5TB) | $100 |
| Sentinel + Defender | $360 |
| ExpressRoute (optional) | $1,200 |
| **Total** | **$1,220-$2,420/month** |

**Cost Optimization Tips:**
- Use B-series VMs for dev/test workloads
- Enable auto-shutdown schedules (save 60-70%)
- Leverage free tiers (Log Analytics: 5GB/month free)
- Implement cloud tiering (saved 60% storage in testing)
- Use Azure Hybrid Benefit for licensing

Full analysis: [COST-ANALYSIS.md](./COST-ANALYSIS.md)

##  Skills Demonstrated

**This project showcases:**

| Skill Category | Technologies |
|----------------|--------------|
| **Identity & Access** | Azure AD, AD Connect, MFA, Conditional Access, RBAC |
| **Storage** | File Server, Azure Files, File Sync, Cloud Tiering, Backup |
| **Security** | Sentinel, Defender, SIEM, SOAR, Threat Hunting, KQL |
| **Networking** | VNets, NSGs, Site-to-Site VPN (planned), DNS |
| **Monitoring** | Log Analytics, Azure Monitor, Workbooks, Alerts |
| **Automation** | PowerShell, Logic Apps, Playbooks, IaC |
| **Compliance** | Audit logging, RBAC, Policy enforcement |

**Certifications Applied:**
-  Microsoft AZ-800 (Windows Server Hybrid Administrator)
-  CompTIA A+ (Hardware/OS fundamentals)
-  CompTIA Network+ (Networking concepts)
-  CompTIA Security+ (Security principles)
-  Microsoft AZ-900 (Azure Fundamentals)
-  Microsoft SC-900 (Security, Compliance, Identity)
-  LPI Linux Essentials (Linux administration)

##  Lessons Learned

### Technical Insights
1. **Azure AD Connect Sync**: Default 30-minute sync can be forced for testing with `Start-ADSyncSyncCycle -PolicyType Delta`
2. **Cloud Tiering**: Requires careful planning - too aggressive tiering can impact user experience
3. **Sentinel Cost Management**: Data ingestion is primary cost driver - implement log filtering early
4. **Conditional Access**: Report-only mode is essential for testing policies before enforcement

### Best Practices
-  Always document as you build, not after
-  Test backup restoration, not just backup creation
-  Implement monitoring from day one
-  Use Infrastructure as Code for reproducibility
-  Plan for disaster scenarios, not just happy paths

### Challenges Overcome
| Challenge | Solution |
|-----------|----------|
| Sync conflicts in Azure File Sync | Implemented file locking for critical documents |
| High Sentinel ingestion costs | Created data filtering rules and sampling |
| Complex Conditional Access testing | Built matrix of test scenarios and used report-only mode |
| Password writeback latency | Documented expected timing (2-5 minutes) for users |

Full retrospective: [LESSONS-LEARNED.md](./LESSONS-LEARNED.md)

##  Future Enhancements

**Planned improvements:**

### Phase 2 (Short-term)
- [ ] Implement high availability with second DC and file server
- [ ] Add Site-to-Site VPN for true hybrid connectivity
- [ ] Deploy Azure Arc for unified management
- [ ] Implement DFS Replication across sites
- [ ] Add Azure Policy for governance

### Phase 3 (Long-term)
- [ ] Integrate Microsoft Defender for Endpoint
- [ ] Implement AD FS for federated authentication
- [ ] Add Azure NetApp Files for high-performance storage
- [ ] Create Infrastructure as Code (Bicep/Terraform) for full deployment
- [ ] Implement advanced SOAR capabilities with custom connectors

**Want to contribute?** See [CONTRIBUTING.md](./CONTRIBUTING.md)

##  Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/yourusername/hybrid-infrastructure/issues).

**Ways to contribute:**
-  Report bugs or issues
-  Suggest new features or improvements
-  Improve documentation
-  Submit pull requests

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

##  Contact

**Your Name** - [LinkedIn](https://linkedin.com/in/yourprofile) - [Email](mailto:your.email@example.com)

**Project Link:** [https://github.com/yourusername/hybrid-infrastructure](https://github.com/yourusername/hybrid-infrastructure)

**Demo Video:** [YouTube Link](#)

---

##  Acknowledgments

- Microsoft Learn documentation and labs
- Azure community and forums
- CompTIA and Microsoft certification programs
- Open-source contributors and tools used

---

<p align="center">
  <strong> If you found this project helpful, please give it a star! </strong><br>
  <em>Built with dedication. Deployed with confidence. Ready for production.</em>
</p>

---

<p align="center">
  <sub>© 2025 Your Name. Built as part of continuous learning in cloud infrastructure and security.</sub>
</p>
