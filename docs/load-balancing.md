# ⚡ Load Balancing & Traffic Aggregation

[← Back to README](../README.md)

---

## Do SIM and WAN combine for speed?

**Yes — but with an important detail:**

- ✅ **Total network throughput** is the sum of all active links
- ❌ **A single file download** still uses only one link at a time
- ✅ **Multiple simultaneous users/sessions** benefit from full combined speed

```
Example:
  WAN  = 100 Mbps
  SIM1 =  80 Mbps
  SIM2 =  50 Mbps
  SIM3 =  50 Mbps
         ─────────
  Total = ~280 Mbps combined capacity

User A streaming 4K  ──► WAN  (80 Mbps used)
User B video call    ──► SIM1 (20 Mbps used)
User C large upload  ──► SIM2 (30 Mbps used)
User C large upload  ──► SIM3 (30 Mbps used)
= All happening simultaneously without congestion ✅
```

---

## Load Balancing Modes

### 1. Round Robin
Routes each new session to the next link in rotation.
- **Best for:** Equal-speed connections, general office use
- **Config:** `Weight: equal on all links`

### 2. Weighted (Recommended)
Sends more traffic to faster/cheaper links.
- **Best for:** Mixed-speed connections (fibre + LTE)
- **Example config:**
```
WAN:  Weight 10  (fastest, cheapest)
SIM1: Weight 5
SIM2: Weight 3
SIM3: Weight 3
```

### 3. Least Load
Routes new sessions to whichever link is least busy.
- **Best for:** Unpredictable traffic patterns

### 4. Policy-Based Routing
Custom rules per source IP, destination, or protocol.
- **Best for:** Businesses needing precise traffic control

---

## Policy-Based Routing Examples

Route specific traffic types to specific links:

```
Rule 1: VoIP (port 5060, 5061)    → WAN only    (lowest latency)
Rule 2: Office PCs (192.168.1.x)  → WAN + SIM1  (load balanced)
Rule 3: Guest Wi-Fi               → SIM2 only   (isolated)
Rule 4: IoT devices               → SIM1        (separate)
```

---

## Configuring Load Balancing

```
Network → Multi-WAN → Load Balance

✅ Enable Load Balancing
✅ Enable Failover

WAN:
  ✅ Active
  Weight: 10

SIM 1:
  ✅ Active
  Weight: 5

SIM 2:
  ✅ Active
  Weight: 3
SIM 3:
  ✅ Active
  Weight: 3

Algorithm: Weighted Round Robin
```

---

## Is this SD-WAN?

The Cedar C3 is **not marketed as SD-WAN** but includes the core SD-WAN features:

| SD-WAN Feature | Cedar C3 |
|---|---|
| Multi-link aggregation | ✅ |
| Automatic failover | ✅ |
| Application-aware routing | ✅ (policy-based) |
| Real-time link monitoring | ✅ |
| Centralized cloud management | ❌ (local UI only) |
| Zero-touch provisioning | ❌ |

For small-to-medium deployments, the Cedar C3 delivers the **practical benefits of SD-WAN** without the complexity or cost.

---

[← Failover](failover.md) · [Next: Setup Guide →](setup.md)
