# ❓ Frequently Asked Questions

[← Back to README](../README.md)

---

**Q: Will my internet cut out when WAN goes down?**  
A: There will be a brief ~10 second pause during automatic failover to SIM. Then it resumes normally.

---

**Q: Can I use two SIMs from different carriers?**  
A: Yes — and it's recommended. If one carrier has an outage, the other keeps you online.

---

**Q: Does load balancing double my download speed on a single file?**  
A: No. One file = one connection = one link. Load balancing helps when multiple devices/sessions run simultaneously. Total capacity is combined, not per-session speed.

---

**Q: What APN do I use for my SIM?**  
A: Contact your mobile carrier — each has their own APN. See the [Connectivity Guide](connectivity.md) for common South African APNs.

---

**Q: Can I set certain apps to always use WAN, not SIM?**  
A: Yes. Use Policy-Based Routing: `Network → Multi-WAN → Rules`. You can route by IP, port, or protocol.

---

**Q: Is the Cedar C3 an SD-WAN router?**  
A: It has SD-WAN-like features (multi-link, failover, policy routing) but lacks centralized cloud management. See the [Load Balancing Guide](load-balancing.md) for a full comparison.

---

**Q: How many devices can connect simultaneously?**  
A: The router supports up to **128 DHCP clients**. Practical limit depends on your internet speeds and device usage.

---

**Q: Can I connect to the router remotely?**  
A: Yes, via remote access / VPN. Enable under `Services → Remote Access`. Do not expose the admin UI directly to the internet.

---

**Q: Does it support IPv6?**  
A: Yes. Enable under `Network → Interfaces → WAN → IPv6`.

---

**Q: How do I update the firmware?**  
A: `System → Firmware Upgrade → Check for Updates` or upload a file from the Cedar Networks website.

---

[← Troubleshooting](troubleshooting.md) · [Specifications →](specifications.md)
