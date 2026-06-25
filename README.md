# Enterprise Active Directory & Core Network Infrastructure Sandbox

## Project Overview
This project involves the design, deployment, and validation of a fully isolated, enterprise-grade Active Directory (AD DS) environment built completely from scratch using Oracle VirtualBox. The core objective was to simulate a real-world corporate infrastructure, establishing centralized identity management, dynamic network address provisioning, internal DNS resolution, and formal workstation domain integration. 

By building this architecture, I established a secure sandbox environment mirroring enterprise operational standards, providing a baseline foundation for practicing systems administration, automated provisioning, and security monitoring.

## Architectural Design & Specifications
The lab environment is entirely segmented from the physical host network using an isolated virtual network topology, ensuring zero external interference and an authentic enterprise boundary.

* **Hypervisor:** Oracle VirtualBox
* **Network Domain:** `mydomain.local` (Internal Active Directory Forest Root)
* **Network Segment:** Isolated Virtual "Internal Network"
* **IP Provisioning Mode:** Centralized DHCP Dynamic Allocation

### Infrastructure Inventory
1.  **Domain Controller (Server):** Windows Server (Evaluation Edition)
    * **Roles:** Active Directory Domain Services (AD DS), DNS Server, DHCP Server
    * **Network Adapter:** Internal Network Interface
2.  **Enterprise Workstation (Client):** Windows 11 Pro
    * **Role:** Authenticated Domain Member Workstation
    * **Network Adapter:** Internal Network Interface (DHCP-dependent)

---

## Deployment Lifecycle & Phases

### Phase 1: Virtual Network Architecture & Base Builds
* Provisioned base storage blocks and compute resources for both target virtual environments.
* Severed external internet bindings by switching network interfaces to VirtualBox's strict **Internal Network** mode to enforce absolute containment.
* Assigned static network parameters to the primary server interface to ensure infrastructure role stability.

### Phase 2: Active Directory & DNS Core Provisioning
* Deployed and promoted the core **Active Directory Domain Services (AD DS)** role.
* Initialized a new forest root designated as `mydomain.local`.
* Configured integrated DNS zones to manage all local hostname-to-IP path routing across the internal network zone.

### Phase 3: DHCP Server Scope Engineering
* Installed and authorized the enterprise DHCP Server role.
* Engineered a dedicated IPv4 allocation scope pool to dynamically lease network parameters (IP addresses, Subnet masks, Default gateways, and primary DNS pointers) to incoming client workstations.

### Phase 4: Workstation Edition Upgrade & Domain Integration
* Booted the Windows 11 client environment, which automatically broadcasted and grabbed its network parameters from the newly authorized DHCP pool.
* Executed an OS upgrade to unlock corporate domain-joining capabilities.
* Initiated a formal security handshake to bind the Windows 11 workstation to the `mydomain.local` domain structure.

### Phase 5: Directory Architecture & User Provisioning
* Established a structured, real-world Organizational Unit (OU) heirarchy within the directory tree: created `Enterprise-Objects` as the root container and a sub-OU named `Staff`.
* Provisioned a standard corporate test employee identity (`jdoe` / John Doe) with strictly configured enterprise complexity passwords.

---

## Environment Validation & Proof of Concept

Hiring managers value visual verification. The screenshots below validate that the entire synchronized backend infrastructure is functional, operational, and securely communicating.

### 1. Active Directory Identity Hierarchy
The Active Directory Users and Computers configuration tree proves the successful creation of the custom Organizational Unit infrastructure and employee account deployment.

![Active Directory Structure](01_active_directory.png)

### 2. DHCP Scope Allocation Verification
The Server-side DHCP management console displays the active network parameter lease successfully claimed by the Windows 11 client workstation.

![DHCP Leases Console](02_dhcp_leases.png)

### 3. Authenticated Domain Client Session
Running the terminal environment validation on the client workstation confirms the user is officially logged into a security session authorized globally by the Domain Controller.

![Domain Session Verification](03_domain_join.png)

---

## Key Technical Competencies Demonstrated
* **Enterprise Directory Design:** Hands-on experience structuring Organizational Units (OUs) and administrative objects.
* **Core Infrastructure Services:** Advanced configuration of underlying network components (DNS zone authority, DHCP scope parameters, static routing configurations).
* **Identity & Access Management (IAM):** Provisioning domain users, establishing credential authentication pathways, and separating administrative accounts from standard client workflows.
* **Troubleshooting & Systems Engineering:** Diagnosing UI shell profile initialization errors, verifying network visibility paths, and executing clean system reboots to clear registry caching anomalies.
