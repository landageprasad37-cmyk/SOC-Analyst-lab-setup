# Day 1 — pfSense Firewall Deployment

## Objective

Build the foundation of the cybersecurity home lab by deploying pfSense as the firewall and connecting client machines through an isolated virtual network.

---

## Environment

### Hypervisor

- VMware Workstation

### Firewall

- pfSense Community Edition

### Client Systems

- Windows 10
- Kali Linux

---

## Tasks Completed

- Installed pfSense
- Configured WAN interface
- Configured LAN interface
- Assigned LAN IP address
- Enabled DHCP server
- Configured DHCP address pool
- Connected Windows 10 to the LAN
- Connected Kali Linux to the LAN
- Verified Internet connectivity
- Verified DNS resolution
- Accessed the pfSense WebGUI
- Verified DHCP leases

---

## Network Information

| Setting | Value |
|---------|-------|
| LAN Network | 192.168.10.0/24 |
| Firewall IP | 192.168.10.1 |
| DHCP Pool | 192.168.10.100 – 192.168.10.199 |

---

## Validation Performed

### Windows 10

- Received DHCP address
- Successfully communicated with pfSense
- Successfully accessed the Internet
- Successfully resolved DNS

### Kali Linux

- Received DHCP address
- Successfully communicated with pfSense
- Successfully accessed the Internet
- Successfully resolved DNS

---

## Challenges

- Understanding VMware virtual networking
- Configuring WAN and LAN interfaces correctly
- Setting the correct DHCP address range

---

## Lessons Learned

- A firewall requires separate WAN and LAN interfaces.
- DHCP automatically assigns IP addresses to clients.
- pfSense can function as a firewall, router, and DHCP server.
- Proper network segmentation improves network organization and security.

---

## Evidence

Relevant screenshots are available in the `screenshots/` directory.

---

## Status

✅ Day 1 Completed