# 🔥 OPNsense Home Lab


A personal home lab setup running **OPNsense** — an open-source FreeBSD-based firewall and routing platform. This repo documents my configuration, rules, and setup for reference and version control.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Lab Topology](#lab-topology)
- [Hardware](#hardware)
- [OPNsense Version](#opnsense-version)
- [Features Configured](#features-configured)
- [Folder Structure](#folder-structure)
- [Setup Guide](#setup-guide)
- [Firewall Rules](#firewall-rules)
- [VLANs](#vlans)
- [VPN](#vpn)
- [Plugins Installed](#plugins-installed)
- [Backup & Restore](#backup--restore)
- [Resources](#resources)

---

## 🧭 Overview

This home lab uses OPNsense as the main firewall/router to:
- Manage and segment home network traffic
- Provide secure VPN access
- Monitor network activity
- Test cybersecurity concepts in a safe environment

---

## 🗺️ Lab Topology

```
[ISP Modem]
     |
[OPNsense Firewall]
     |
  ┌──┴──────────────┐
  |                 |
[LAN]           [VLAN / DMZ]
  |                 |
[PCs / Devices]  [Servers / VMs]
```

---

## 🖥️ Hardware

| Component     | Details                  |
|---------------|--------------------------|
| Device        | (Your device here)       |
| CPU           | (e.g. Intel i5)          |
| RAM           | (e.g. 8GB)               |
| Storage       | (e.g. 128GB SSD)         |
| NICs          | (e.g. 2x Gigabit LAN)    |
| Hypervisor    | (e.g. Proxmox / Bare Metal) |

---

## 🔖 OPNsense Version

| Item          | Detail               |
|---------------|----------------------|
| Version       | 26.x                 |
| Architecture  | amd64                |
| Base OS       | FreeBSD 14           |
| Release Date  | 2026                 |

---

## ✅ Features Configured

- [x] WAN / LAN interfaces
- [x] DHCP Server
- [x] DNS Resolver (Unbound)
- [x] Firewall Rules
- [x] VLANs
- [x] OpenVPN / WireGuard
- [x] IDS/IPS (Suricata)
- [x] HAProxy (Reverse Proxy)
- [x] Zenarmor (Next-Gen Firewall)

---

## 📁 Folder Structure

```
opnsense-lab/
├── README.md            # This file
├── configs/             # Exported OPNsense config backups (.xml)
├── rules/               # Firewall rules documentation
├── vlans/               # VLAN configuration notes
├── vpn/                 # VPN setup (OpenVPN / WireGuard)
├── plugins/             # Installed plugins list & configs
└── docs/                # Additional documentation & diagrams
```

---

## 🚀 Setup Guide

### 1. Download OPNsense
Download the latest ISO from: https://opnsense.org/download/

### 2. Install OPNsense
- Boot from USB/ISO
- Follow the installer steps
- Set WAN and LAN interfaces

### 3. Initial Configuration
- Access WebGUI at `https://192.168.1.1`
- Default credentials: `root` / `opnsense`
- Run the setup wizard

### 4. Update OPNsense
```
System > Firmware > Updates > Check for Updates
```

---

## 🛡️ Firewall Rules

| Rule | Interface | Source | Destination | Action |
|------|-----------|--------|-------------|--------|
| Allow LAN to WAN | LAN | LAN net | any | Allow |
| Block bogon networks | WAN | bogon | any | Block |
| Allow ICMP | LAN | any | any | Allow |

> Full rules are documented in `/rules/`

---

## 🔀 VLANs

| VLAN ID | Name       | Subnet           | Purpose              |
|---------|------------|------------------|----------------------|
| 10      | LAN        | 192.168.10.0/24  | Main devices         |
| 20      | IoT        | 192.168.20.0/24  | Smart home devices   |
| 30      | DMZ        | 192.168.30.0/24  | Servers / Lab VMs    |

---

## 🔐 VPN

- **Type:** WireGuard / OpenVPN *(update as needed)*
- **Purpose:** Secure remote access to home lab
- **Config files:** stored in `/vpn/` *(private keys NOT included)*

---

## 🧩 Plugins Installed

| Plugin            | Purpose                          |
|-------------------|----------------------------------|
| os-wireguard      | WireGuard VPN                    |
| os-suricata       | IDS/IPS                          |
| os-zerotier       | ZeroTier overlay network         |
| os-haproxy        | Reverse proxy / load balancer    |
| os-zenarmor       | Next-gen firewall                |

---

## 💾 Backup & Restore

### Export Config
```
System > Configuration > Backups > Download configuration
```
Save the `.xml` file to `/configs/` folder in this repo.

### Restore Config
```
System > Configuration > Backups > Restore configuration
```
Upload the `.xml` file from `/configs/`

### Git Backup (Auto)
OPNsense supports automatic config backup to GitHub via:
```
System > Configuration > Backups > Git
```

---

## 📚 Resources

- 🌐 [OPNsense Official Site](https://opnsense.org)
- 📖 [OPNsense Documentation](https://docs.opnsense.org)
- 💻 [OPNsense GitHub](https://github.com/opnsense)
- 🎥 [YouTube - OPNsense Tutorials](https://www.youtube.com/results?search_query=opnsense+tutorial)
- 💬 [OPNsense Forum](https://forum.opnsense.org)
- 🔴 [Reddit r/OPNsense](https://www.reddit.com/r/OPNsense/)

---

## 👤 Author

**Your Name**
- GitHub: [@yourusername](https://github.com/yourusername)

---

> ⚠️ **Note:** No sensitive information (passwords, private keys, or IP addresses) should be committed to this repository.
