
**Goal:** Transform an ASUS Zenbook i7 into a secure, multi-user private cloud using Ubuntu Server and Docker.

---

## 🛠️ The Architecture (The "How-To")
*Use this section to explain the technical layers of your project.*

### 1. Hardware & OS
* **Device:** ASUS Zenbook (Intel i7, 16GB RAM, 1TB SSD).
* **OS:** Ubuntu 24.04 LTS (Headless).
* **Optimization:** Modified `logind.conf` to disable lid-sleep, allowing 24/7 "server mode".

### 2. Storage Management 
* **Problem:** Ubuntu LVM only allocated ~100GB by default.
* **Solution:** Used `lvextend` and `resize2fs` to expand the logical volume to the full 1TB capacity.
* **Command Reference:**
  `sudo lvextend -l +100%FREE /dev/ubuntu-vg/ubuntu-lv && sudo resize2fs /dev/ubuntu-vg/ubuntu-lv`

### 3. Networking & Security
* **Internal:** Assigned static IP via router (192.168.1.122).
* **VPN:** Tailscale Mesh VPN for encrypted "backdoor" access from MacBook Air M2.
* **Public Access:** Cloudflare Tunnels for SSL-secured subdomains (e.g., `cloud.mageba.dev`) without port forwarding.

---

## 🚀 Services (The App Stack)
*Every time you cross a "bridge," add the Docker Compose logic here.*

| Service                   | Purpose                 | Tech       | Status    |
| :------------------------ | :---------------------- | :--------- | :-------- |
| **CasaOS**                | Management Dashboard    | Docker     | ✅ Live    |
| **Immich**                | Multi-user Photo Backup | Docker     | ⏳ Planned |
| **[[00 Jellyfin]]**       | Media Streaming         | Docker     | ✅ Live    |
| **Uptime Kuma**           | System Monitoring       | Docker     | ✅ Live    |
| **n8n**                   | SaaS Automation         | Docker     | ⏳ Planned |
| **[[00 Windows VM]]**     | Safe Testing Zone       | KVM/Docker | ✅ Live    |
| **[[00 Homenetwork CA]]** |                         |            |           |

---

## 📸 Proof of Concept (Screenshots/Visuals)
*Store your "receipts" here for your LinkedIn post later.*

- [ ] **Terminal:** Screenshot of the `ip addr` and `df -h` after storage expansion.
- [ ] **Dashboard:** Screenshot of the CasaOS main UI showing active containers.
- [ ] **Remote Access:** Photo of streaming Jellyfin on a Smart TV or phone via Tailscale.
- [ ] **Diagram:** 

---

## 📝 Professional Summary (For LinkedIn/Portfolio)
*Copy and paste this once the project is stable.*

> "Architected and deployed a private cloud infrastructure on bare-metal ASUS hardware. Managed a 1TB LVM-based storage pool and orchestrated a suite of Dockerized services including automation (n8n), media streaming (Jellyfin), and multi-user storage (Immich). Implemented a zero-trust remote access model using Cloudflare Tunnels and Tailscale VPN, eliminating the need for traditional port forwarding while maintaining enterprise-grade security."

---

## 🔗 Links
- **Live Status Page:** `[Link to your Uptime Kuma public page]`
