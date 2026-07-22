# Day 02 – Configure Endpoints & Verify Network Connectivity

## Objective

- Update Kali Linux.
- Verify networking tools.
- Configure hostnames.
- Verify DHCP.
- Test connectivity.
- Understand why Ping may fail.
- Verify connectivity using ARP, Nmap and Traceroute.

---

# Lab Topology

```
                Internet
                    │
            VMware NAT (VMnet8)
                    │
                    │
         +----------------------+
         |       pfSense        |
         | WAN : DHCP           |
         | LAN : 192.168.10.1   |
         +----------------------+
                    │
        --------------------------
        │                        │
        │                        │
 Kali Linux                Windows 10
kali-attacker             win10-target
```

---

# Step 1 – Update Kali

Update package lists.

```bash
sudo apt update
```

Upgrade installed packages.

```bash
sudo apt upgrade -y
```

---

# Step 2 – Verify Required Tools

Check Nmap.

```bash
nmap --version
```

Check Wireshark.

```bash
wireshark --version
```

Check Bettercap.

```bash
bettercap --version
```

If any tool is missing, install it before continuing.

---

# Step 3 – Configure Hostnames

## Kali

Check hostname.

```bash
hostnamectl
```

Change hostname.

```bash
sudo hostnamectl set-hostname kali-attacker
```

Restart.

```bash
sudo reboot
```

Verify.

```bash
hostname
```

---

## Windows

Open:

```
Settings
→ System
→ About
→ Rename this PC
```

Rename it to

```
win10-target
```

Restart Windows.

Verify using:

```cmd
hostname
```

---

# Step 4 – Verify IP Configuration

## Kali

```bash
ip a
```

Verify:

- IPv4 Address
- Subnet Mask
- Default Gateway

---

## Windows

```cmd
ipconfig
```

Verify:

- IPv4 Address
- Default Gateway

Both machines should receive their IP addresses from the pfSense DHCP server.

---

# Step 5 – Verify Internet Connectivity

From Kali:

```bash
ping google.com
```

Stop after a few replies.

---

# Step 6 – Test Local Connectivity

Ping Windows.

```bash
ping -c 4 <Windows-IP>
```

If Ping fails, **do not disable Windows Firewall.**

Continue with the next verification steps.

---

# Step 7 – Verify Layer 2 using ARP

Display the ARP table.

```bash
ip neigh
```

or

```bash
arp -a
```

Verify that the Windows IP has a corresponding MAC address.

If the MAC address exists, Layer 2 communication is functioning correctly.

---

# Step 8 – Verify Host Availability using Nmap

Scan the Windows machine.

```bash
nmap <Windows-IP>
```

If ICMP is blocked, use:

```bash
nmap -Pn <Windows-IP>
```

Verify that Nmap reports:

```
Host is up
```

This confirms that the host is reachable even if Ping fails.

---

# Step 9 – Trace the Network Path

Run:

```bash
traceroute google.com
```

Verify:

First hop

```
192.168.10.1
```

This is the pfSense LAN interface.

Second hop

```
VMware NAT Gateway
```

Remaining hops may show:

```
* * *
```

Many Internet routers do not respond to traceroute probes.

---

# Expected Learning Outcomes

After completing this lab, you should understand:

- DHCP
- Hostname configuration
- Default Gateway
- ARP
- ICMP
- Nmap Host Discovery
- Traceroute
- Layer-by-layer troubleshooting using the OSI Model
- Why enterprise environments may block Ping while remaining fully operational

---

# Conclusion

The lab environment is fully operational and ready for the next phase of enterprise networking and SOC analyst exercises.