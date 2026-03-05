# Automated-Hybrid-Zero-Trust-Media-Networking-Lab
My HomeLab✨

جاري الكتابة...
## 📋 نظرة عامة على الخدمات (Services Overview)

| الخدمة (Service) | الوظيفة (Role) | الوصول (Access) |
| :--- | :--- | :---: |
| **[Jellyfin](https://github.com/linuxserver/docker-jellyfin)** | بث الميديا (Media Server) | 🌐 Public (Tunnel) |
| **[Jellyseerr](https://requests.heronyaa.dev)** | واجهة طلبات المحتوى (Requests) | 🌐 Public (Tunnel) |
| **[Homarr](https://home.heronyaa.dev)** | لوحة التحكم المركزية (Dashboard) | 🌐 Public (Tunnel) |
| **[Sonarr](https://github.com/linuxserver/docker-sonarr)** | إدارة وتنظيم المسلسلات (TV) | 🔐 Private (Tailscale) |
| **[Prowlarr](http://100.x.x.x:9696)** | إدارة الفهرسة والبحث (Indexers) | 🔐 Private (Tailscale) |
| **[Transmission](https://github.com/linuxserver/docker-transmission)** | محرك التحميل (Torrent Client) | 🔐 Private (Tailscale) |
| **[Pi-hole](http://100.x.x.x/admin)** | حماية الشبكة وحجب الإعلانات | 🏠 Local (VPN) |
| **[Dashdot](http://100.x.x.x:3001)** | مراقب موارد السيرفر (Real-time) | 🔐 Private (Tailscale) |

---
