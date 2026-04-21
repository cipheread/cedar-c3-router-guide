# 🔧 Troubleshooting

[← Back to README](../README.md)

---

## SIM Not Connecting

**Symptoms:** SIM shows "No Signal" or no IP address

| Check | Solution |
|---|---|
| APN correct? | Confirm with your carrier |
| SIM seated properly? | Remove and reinsert |
| PIN lock enabled? | Enter SIM PIN in mobile settings |
| Signal in your area? | Check carrier coverage map |
| Data plan active? | Call carrier to confirm |
| Try SIM in a phone | Test if SIM works elsewhere |

```
Diagnostic: Status → Mobile → SIM1
  Check: Signal strength, operator name, IP address
```

---

## WAN Not Connecting

| Check | Solution |
|---|---|
| Cable plugged into WAN port? | Check both ends |
| Modem powered on? | Reboot modem |
| ISP outage? | Check ISP status page |
| Wrong protocol? | Try DHCP / Static / PPPoE |
| MAC filtering on modem? | Clone MAC: `Network → WAN → Advanced → MAC` |

---

## Failover Not Working

**WAN drops but no switch to SIM:**

1. Confirm Multi-WAN is enabled: `Network → Multi-WAN → ✅ Enable`
2. Confirm SIM is connected and has an IP
3. Lower the health check threshold: try 2 failures instead of 3
4. Check health check target is reachable: ping `8.8.8.8` manually

---

## Slow Speeds

| Symptom | Likely Cause | Fix |
|---|---|---|
| SIM slow | Poor signal | Reposition router / external antenna |
| WAN slow | ISP issue | Test speed bypassing router |
| Both slow | Congestion | Check QoS settings |
| One device slow | Device issue | Test on multiple devices |

**Check per-link speed:**
```
Status → Multi-WAN → Bandwidth Monitor
```

---

## Can't Access Web UI (192.168.1.1)

1. Make sure you're connected to the router (Wi-Fi or LAN cable)
2. Try a different browser
3. Clear browser cache / try incognito mode
4. Check your device got an IP in the `192.168.1.x` range
5. **Factory reset** (hold reset button 10 seconds) — ⚠️ erases all settings

---

## Router Keeps Rebooting

- Check power adapter — use only the supplied 12V adapter
- Check temperature — ensure ventilation around the unit
- Update firmware: `System → Firmware Upgrade`

---

## Forgot Admin Password

Hold the **reset button** for **10 seconds** until the LED flashes.  
Router resets to factory defaults (password: `admin`).

> ⚠️ This erases all your configuration. Take a backup first if possible:  
> `System → Backup → Download`

---

[← Setup](setup.md) · [Next: FAQ →](faq.md)
