# Enterprise Multi-Router Network Simulation (Cisco Packet Tracer)

A comprehensive, enterprise-grade network infrastructure simulation designed and implemented in **Cisco Packet Tracer**. The network interconnects **5 enterprise routers**, **15 dynamic local area subnets (LANs)**, and over **60 endpoints**, incorporating enterprise routing, dual-mode DHCP architectures, centralized Web/DNS application servers, remote administrative access, and VLAN segmentation.

---

## Network Architecture & Topology

![Enterprise Network Topology](topology.png)

---

## Key Technical Specifications & Topologies

### 1. Core WAN Backbone (5 Interconnected Routers)
* **Topology:** Point-to-point serial WAN links interconnecting all 5 core routers (`Router0` through `Router4`).
* **Routing:** End-to-end multi-hop connectivity ensuring full route propagation and zero packet drop across all subnets (`Successful` end-to-end ping).

### 2. Standardized Dual DHCP Infrastructure (Per Router)
Each router administers three distinct Local Area Networks (LANs):
* **LAN 1 (Router-Based DHCP):** Dynamic IP allocation handled natively via Cisco IOS DHCP pools configured directly on the sub-interfaces/interfaces.
* **LAN 2 (Dedicated Server-Based DHCP):** Addressing serviced through dedicated standalone `Server-PT DHCP` appliances per zone.
* **LAN 3 (Specialized Services / Management):** Customized administrative and application layers.

### 3. Specialized Subnet Deployments
* **Router 1 (Central Services Zone):**
  * Dedicated **HTTP Web Server** hosting enterprise pages.
  * Centralized **DNS Server** mapped to domain records, queried by all hosts across all 15 subnets.
* **Router 2 & Router 3 (Custom Infrastructure Naming):**
  * Custom hostname conventions adhering to institutional network policy and domain hierarchy.
* **Router 4 (Secure Remote Administration):**
  * VTY configuration facilitating secure CLI remote access (Telnet / SSH) restricted to designated management endpoints.
* **Router 5 (Switch Management & VLAN Segmentation):**
  * Switched Virtual Interface (SVI) configuration enabling remote switch administration.
  * **VLAN Deployment:** Logical traffic isolation dividing departmental access (e.g., `IT` and `IT-Management`) using IEEE 802.1Q encapsulation.

---

## IP Addressing & WAN Interconnect Overview

| Link / Subnet | Role / Description | Subnet Range |
| :--- | :--- | :--- |
| **WAN Serial Links** | Inter-Router Serial Interconnects | `9.120.0.0/x`, `9.128.0.0/x`, `9.136.0.0/x`, `9.144.0.0/x` |
| **Router 0 LANs** | Native DHCP, Server DHCP, Web & DNS | `9.0.0.0`, `9.8.0.0`, `9.16.0.0` |
| **Router 1 LANs** | Native DHCP, Server DHCP, Host LAN | `9.24.0.0`, `9.32.0.0`, `9.40.0.0` |
| **Router 2 LANs** | Native DHCP, Server DHCP, Host LAN | `9.48.0.0`, `9.56.0.0`, `9.64.0.0` |
| **Router 3 LANs** | Native DHCP, Server DHCP, Remote Router Admin | `9.72.0.0`, `9.80.0.0`, `9.88.0.0` |
| **Router 4 LANs** | Native DHCP, Server DHCP, Remote Switch & VLANs | `9.96.0.0`, `9.104.0.0`, `9.112.0.0` |

---

## Verification & Testing Checklist

- [x] **Full Reachability:** Verified ICMP ping reachability between any PC in Router 0 and any PC in Router 4.
- [x] **DNS Resolution:** Client PCs resolve the centralized HTTP Web Server using domain names via the Router 0 DNS server.
- [x] **Dual DHCP Operations:** Verified IP leases across client pools from both local IOS DHCP and dedicated Server-PT appliances.
- [x] **Remote Access:** Successful VTY terminal sessions established to core routing and switching gear.
- [x] **VLAN Broadcast Separation:** Isolated broadcast traffic between administrative and operational VLANs on Router 5.

---

## How to Run the Simulation

1. Install **Cisco Packet Tracer** (v8.0 or newer recommended).
2. Clone this repository:
   ```bash
   git clone [https://github.com/EmadTechNet/Enterprise-Multi-Router-Network-Simulation.git](https://github.com/EmadTechNet/Enterprise-Multi-Router-Network-Simulation.git)
