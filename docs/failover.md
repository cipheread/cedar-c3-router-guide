# 🔄 Failover Guide

[← Back to README](../README.md)

---

## Will my internet cut out if WAN goes down?

**Short answer: No — but expect ~10 seconds of interruption during the switch.**

The Cedar C3 continuously monitors all WAN links. When one fails, it automatically reroutes traffic to the next available connection.

---

## Failover Timeline

```
T+0s    WAN link physically drops (cable cut / ISP outage)
T+0–5s  Router detects failed health checks (ping timeouts)
T+5–15s Automatic reroute to SIM 1
T+15s   Internet restored via SIM 1 ✅
...
WAN     Router keeps checking for WAN recovery
WAN ✅  Automatically switches back to WAN (configurable)
```

> **What you'll notice:** A ~10 second pause in internet. Active downloads may resume automatically. VPN tunnels and video calls may need to reconnect.

---

## Failover Priority

You can set the priority order:

```
Network → Multi-WAN → Failover Settings

Priority 1:  WAN (Ethernet)   ← Primary
Priority 2:  SIM 1            ← First backup
Priority 3:  SIM 2            ← Second backup
```

If WAN fails → traffic moves to SIM 1.  
If SIM 1 also fails → traffic moves to SIM 2.  
If all fail → no internet (router shows alert).

---

## Health Check Configuration

The router detects failure by pinging a target IP:

```
Network → Multi-WAN → Health Check

Ping Target:     8.8.8.8  (Google DNS — recommended)
Interval:        5 seconds
Failures before failover: 3
Recovery checks: 5 (before switching back)
```

**Tip:** Use two ping targets (e.g. `8.8.8.8` and `1.1.1.1`) to avoid false failovers when only one DNS server is unreachable.

---

## Failover vs Load Balance Modes

| Mode | Behavior |
|---|---|
| **Active-Passive** | WAN primary; SIMs idle until WAN fails |
| **Active-Active** | All links used simultaneously (load balance) |

> In Active-Active mode, failover still works — if one link dies, its traffic shifts to the remaining links instantly.

---

## Auto-Restore (Failback)

When WAN comes back online, the router can automatically switch back:

```
Network → Multi-WAN → Failback
  ✅ Enable auto-failback
  Restore after: 5 successful health checks
```

Disable this if you prefer to switch back manually (useful if WAN is unstable/flapping).

---

[← Connectivity](connectivity.md) · [Next: Load Balancing →](load-balancing.md)
