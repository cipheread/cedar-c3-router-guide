# ⚙️ Setup Guide

[← Back to README](../README.md)

---

## Before You Start

**You'll need:**
- Cedar C3 router + power adapter
- Ethernet cable (for WAN connection)
- Up to 3 × Nano-SIM cards
- A computer or phone to access the web UI

---

## Step 1 — Physical Setup

```
1. Insert SIM cards into SIM1, SIM 2and SIM3 slots (Nano-SIM / 4FF size)
   └─ Use a SIM ejector pin or paperclip to open the tray

2. Connect ISP modem/ONT → Cedar C3 WAN port (Ethernet)

3. Connect your device → Cedar C3 LAN port (or use Wi-Fi)

4. Power on — wait 60 seconds for boot
```

---

## Step 2 — Access Web UI

| Setting | Value |
|---|---|
| URL | `http://192.168.1.1` |
| Username | `admin` |
| Password | `admin` |

> 🔒 **Change your password immediately** after first login:  
> `System → Administration → Password`

---

## Step 3 — Configure WAN

```
Network → Interfaces → WAN

Protocol:    DHCP  (most ISPs — try this first)
             Static (if your ISP gave you a fixed IP)
             PPPoE  (if your ISP uses username/password login)

Save & Apply
```

Check status: `Status → Overview → WAN` should show a green IP address.

---

## Step 4 — Configure SIM Cards

**SIM 1:**
```
Network → Mobile → SIM1
  Enable:   ✅
  APN:      [your carrier APN]
  Auth:     None (most carriers) / PAP / CHAP
  PIN:      [if your SIM has a PIN lock]
```

**SIM 2:** Repeat the same for SIM.

Check signal: `Status → Mobile` — should show signal bars and an IP address.

**SIM 3:** Repeat the same for SIM3.

Check signal: `Status → Mobile` — should show signal bars and an IP address.

---

## Step 5 — Enable Load Balancing & Failover

```
Network → Multi-WAN

✅ Enable
Algorithm: Weighted Round Robin

WAN  → Weight: 10, ✅ Active
SIM1 → Weight: 5,  ✅ Active  
SIM2 → Weight: 3,  ✅ Active
SIM3 → Weight: 3,  ✅ Active

Health Check:
  Target IP: 8.8.8.8
  Interval: 5s
  Threshold: 3 failures

Failover Priority:
  1. WAN
  2. SIM1
  3. SIM2
  4. SIM3

Save & Apply
```

---

## Step 6 — Configure Wi-Fi

```
Network → Wireless

SSID:      [your network name]
Password:  [strong password - min 12 chars]
Security:  WPA2-PSK or WPA3
Band:      2.4 GHz (range) + 5 GHz (speed)

Save & Apply
```

---

## Step 7 — Verify Everything Works

```
Status → Overview

WAN:  ● Green — connected
SIM1: ● Green — connected
SIM2: ● Green — connected
SIM3: ● Green — connected

Test failover:
  1. Unplug WAN cable
  2. Wait 15 seconds
  3. Check internet still works via SIM
  4. Replug WAN — should switch back automatically
```

---

## Optional — Advanced Settings

| Feature | Location |
|---|---|
| Port Forwarding | `Network → Firewall → Port Forwards` |
| Static DHCP leases | `Network → DHCP → Static Leases` |
| VPN | `VPN → OpenVPN / IPSec` |
| QoS Traffic Priority | `Network → QoS` |
| VLAN | `Network → Switch → VLANs` |
| Dynamic DNS | `Services → Dynamic DNS` |
| Scheduled Reboot | `System → Scheduled Tasks` |

---

[← Load Balancing](load-balancing.md) · [Next: Troubleshooting →](troubleshooting.md)
