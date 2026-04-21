# 📡 Connectivity Guide — SIM vs WAN

[← Back to README](../README.md)

---

## Overview

The Cedar C3 supports **three simultaneous internet connections**:

| Connection | Type | Interface |
|---|---|---|
| WAN | Wired Ethernet | RJ-45 port |
| SIM 1 | 5G / 4G LTE | Nano-SIM slot 1 |
| SIM 2 | 5G / 4G LTE | Nano-SIM slot 2 |

---

## WAN (Wired Ethernet)

- **Best for:** Primary internet, lowest latency tasks (VoIP, gaming)
- **Speed:** Up to 1 Gbps (limited by your ISP plan)
- **Latency:** 5–20ms typical
- **Reliability:** High — but single point of failure if ISP line cuts

### How to connect WAN
1. Plug an Ethernet cable from your ISP modem/ONT into the **WAN port**
2. Router auto-detects the connection (DHCP by default)
3. Set static IP if required: `Network → WAN → Protocol → Static`

---

## SIM Cards (5G / 4G LTE)

- **Best for:** Backup/failover, load balancing extra bandwidth, remote sites with no wired internet
- **SIM size:** Nano-SIM (4FF)
- **Slots:** 2 independent slots — can use **different carriers**

### Supported Bands
| Technology | Bands |
|---|---|
| 5G Sub-6GHz | n1, n3, n7, n28, n41, n78 |
| 4G LTE | B1, B3, B7, B8, B20, B28 |
| 3G UMTS | B1, B8 (fallback) |

### APN Configuration
Each SIM needs the correct APN from your carrier:

```
Network → Mobile → SIM1 → APN Settings
  APN:      [from your carrier]
  Username: [if required]
  Password: [if required]
  Auth:     None / PAP / CHAP
```

#### Common APNs (South Africa)
| Carrier | APN |
|---|---|
| Vodacom | internet |
| MTN | internet |
| Cell C | internet |
| Telkom | telkominternet |
| Rain | rain.co.za |

> ⚠️ APNs may change. Always confirm with your carrier.

---

## Choosing Your Setup

| Scenario | Recommended Config |
|---|---|
| Office with fibre + cellular backup | WAN = fibre, SIM1 = backup |
| Remote site, no wired internet | SIM1 + SIM2 load balanced |
| Maximum reliability | All 3 active with failover priority |
| Home user, dual ISP | WAN = fibre, SIM1 = LTE secondary |

---

[Next: Failover Guide →](failover.md)
