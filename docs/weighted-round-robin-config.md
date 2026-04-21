# Weighted Round Robin (WRR) Configuration Guide

## Production-Ready Example for Cedar C3

This configuration is tested and validated for the Cedar C3 with **3 SIMs + 1 WAN** setup.

---

## Configuration

Navigate to: **Network → Multi-WAN**

```yaml
✅ Enable Load Balancing

Algorithm: Weighted Round Robin

┌──────────┬──────────┬──────────┐
│  Link    │  Weight  │  Active  │
├──────────┼──────────┼──────────┤
│  WAN     │    10    │    ✅    │
│  SIM1    │    5     │    ✅    │
│  SIM2    │    3     │    ✅    │
│  SIM3    │    3     │    ✅    │
└──────────┴──────────┴──────────┘

Traffic Flow Visualization:

WAN  ████████████████████████████████████████ (48%)
SIM1 ████████████████████                     (24%)
SIM2 ████████████                             (14%)
SIM3 ████████████                             (14%)

Understanding Weighted Round Robin
How It Works
The router distributes connections in a round-robin cycle based on weights:
Cycle Example (weights 10:5:3:3):

WAN → WAN → WAN → WAN → WAN → WAN → WAN → WAN → WAN → WAN → (10 times)
SIM1 → SIM1 → SIM1 → SIM1 → SIM1 → (5 times)
SIM2 → SIM2 → SIM2 → (3 times)
SIM3 → SIM3 → SIM3 → (3 times)
└─────────────── Repeat ───────────────┘
Weight Formula
Traffic % per link = (Link Weight) / (Sum of All Weights) × 100
Example for WAN: 10 / 21 × 100 = 47.6%
