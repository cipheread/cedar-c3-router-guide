# 📐 Technical Specifications

[← Back to README](../README.md)

---

## Hardware

| Component | Specification |
|---|---|
| CPU | Multi-core ARM processor |
| RAM | 512 MB DDR3 |
| Flash Storage | 256 MB NAND |
| Operating System | OpenWRT-based Linux |

## Ports & Interfaces

| Interface | Details |
|---|---|
| WAN | 1 × Gigabit Ethernet (RJ-45) |
| LAN | 4 × Gigabit Ethernet (RJ-45) |
| SIM Slots | 2 × Nano-SIM (4FF) |
| USB | 1 × USB 3.0 |
| Console | 1 × RJ-45 Serial (optional) |

## Wireless (Wi-Fi)

| Spec | Value |
|---|---|
| Standard | IEEE 802.11 a/b/g/n/ac (Wi-Fi 5) |
| 2.4 GHz | Up to 300 Mbps |
| 5 GHz | Up to 867 Mbps |
| Antennas | 2 × internal / external (model dependent) |

## Cellular

| Technology | Bands |
|---|---|
| 5G Sub-6GHz | n1, n3, n7, n28, n41, n78 |
| 4G LTE | B1, B3, B7, B8, B20, B28 |
| 3G UMTS | B1, B8 |

| Technology | Peak Down | Peak Up |
|---|---|---|
| 5G Sub-6 | ~1 Gbps | ~200 Mbps |
| 4G LTE Cat-20 | ~2000 Mbps | ~200 Mbps |
| 4G LTE Cat-6 | ~300 Mbps | ~50 Mbps |

> Actual speeds depend on carrier, signal strength, and network congestion.

## Power

| Spec | Value |
|---|---|
| Input | 12V DC, 2A |
| Consumption | ~15W typical |
| Connector | DC barrel jack |

## Physical

| Spec | Value |
|---|---|
| Dimensions | ~200 × 130 × 35 mm |
| Weight | ~500g |
| Operating Temp | 0°C to 50°C |
| Storage Temp | -20°C to 70°C |
| Humidity | 5% – 95% non-condensing |

## Software Features

| Feature | Support |
|---|---|
| Multi-WAN Load Balancing | ✅ |
| Automatic WAN Failover | ✅ |
| Policy-Based Routing | ✅ |
| QoS / Traffic Shaping | ✅ |
| VLAN (802.1Q) | ✅ |
| Firewall / NAT / DMZ | ✅ |
| Port Forwarding | ✅ |
| VPN (IPSec, L2TP, OpenVPN) | ✅ |
| Dynamic DNS | ✅ |
| SNMP Monitoring | ✅ |
| SMS Alerts | ✅ |
| GPS / GNSS | ✅ (select models) |
| IPv6 | ✅ |
| Remote Management | ✅ |
| Firmware OTA Updates | ✅ |

---

[← FAQ](faq.md) · [Back to README →](../README.md)
