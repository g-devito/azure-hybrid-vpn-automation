# 🌐 Hybrid Cloud VPN: Site-to-Site Automation (Azure & On-Prem)

![Azure](https://img.shields.io/badge/azure-%230072C6.svg?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Terraform](https://img.shields.io/badge/terraform-%235835CC.svg?style=for-the-badge&logo=terraform&logoColor=white)
![Ansible](https://img.shields.io/badge/ansible-%231A1918.svg?style=for-the-badge&logo=ansible&logoColor=white)
![Linux](https://img.shields.io/badge/linux-%23FCC624.svg?style=for-the-badge&logo=linux&logoColor=black)

This project implements a complete hybrid infrastructure, connecting an **On-Premises** environment (simulated via Vagrant/KVM on Fedora) to an **Azure VNet** through a **Site-to-Site IPsec VPN tunnel**.

The entire deployment is automated via a single master orchestrator script, combining **Infrastructure as Code (IaC)**, **Configuration Management**, and **Enterprise Networking** principles.

## 🏗️ Project Architecture
![Architecture Diagram](./architecture.png)

### Key Components:
- **On-Prem (Site A):** AlmaLinux 9 VM provisioned with Vagrant (Libvirt provider). Acts as the local VPN Gateway using StrongSwan.
- **Azure (Site B):** A full hub-spoke ready network including Virtual Network Gateway, VNet, and an isolated workload VM with no public IP.
- **Networking:** Static routing configured to enable seamless traffic flow between the local LAN (`192.168.x.x`) and the Azure VNet (`10.0.x.x`).

## 🛠️ Technology Stack
- **Vagrant (Libvirt/KVM):** Local virtualization on Fedora Linux.
- **Terraform:** Infrastructure provisioning on Microsoft Azure.
- **Ansible:** Automated configuration of the IPsec gateway (StrongSwan) and OS-level kernel hardening.
- **StrongSwan:** Open-source IPsec IKEv2 implementation.
- **Bash:** Workflow orchestration and automation.

## 🚀 Getting Started
1. **Prerequisites:** Ensure `az login` is configured and the `vagrant-libvirt` plugin is installed.
2. **Execution:**
   ```bash
   chmod +x deploy_all.sh
   ./deploy_all.sh
