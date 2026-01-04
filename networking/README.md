<!--
---
title: "Networking"
description: "VPNs, DNS, reverse proxies, and network tools"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
status: "Active"
tags:
  - type: directory-readme
  - category: networking
---
-->

# Networking

Docker Compose recipes for VPNs, DNS servers, reverse proxies, ad blocking, remote access, and network tools.

---

## 1. Contents

```
networking/
├── adguard-home/         # Network-wide ad blocking
├── pihole/               # DNS-based ad blocking
├── wireguard/            # Modern VPN tunnel
├── openvpn/              # Traditional VPN server
├── softethervpn/         # Multi-protocol VPN
├── headscale/            # Self-hosted Tailscale
├── nginx-proxy-manager/  # Reverse proxy with GUI
├── traefik/              # Cloud-native edge router
├── guacamole/            # Remote desktop gateway
├── searxng/              # Privacy search engine
└── README.md             # This file
```

---

## 2. Recipes

| Recipe | Description | Use Case |
|--------|-------------|----------|
| [adguard-home](adguard-home/README.md) | Network-wide ad blocking with DNS | Ad/tracker blocking |
| [pihole](pihole/README.md) | DNS-based ad blocking | Ad blocking |
| [wireguard](wireguard/README.md) | Modern, fast VPN tunnel | Remote access |
| [openvpn](openvpn/README.md) | Traditional VPN server | Legacy compatibility |
| [softethervpn](softethervpn/README.md) | Multi-protocol VPN server | Protocol flexibility |
| [headscale](headscale/README.md) | Self-hosted Tailscale control server | Mesh VPN |
| [nginx-proxy-manager](nginx-proxy-manager/README.md) | Reverse proxy with web GUI | SSL termination |
| [traefik](traefik/README.md) | Cloud-native edge router | Dynamic routing |
| [guacamole](guacamole/README.md) | Clientless remote desktop gateway | Browser-based RDP/VNC/SSH |
| [searxng](searxng/README.md) | Privacy-respecting metasearch engine | Private search |

---

## 3. Recipe Count: 10

---

## 4. Quick Reference

| Need | Recommended |
|------|-------------|
| Network-wide ad blocking | AdGuard Home or Pi-hole |
| Modern VPN | WireGuard |
| Mesh VPN (Tailscale-like) | Headscale |
| Legacy VPN clients | OpenVPN or SoftEther |
| Reverse proxy (GUI) | Nginx Proxy Manager |
| Reverse proxy (config-as-code) | Traefik |
| Remote desktop via browser | Guacamole |
| Private search | SearXNG |

---

## 5. VPN Comparison

| VPN | Protocol | Performance | Ease of Setup |
|-----|----------|-------------|---------------|
| WireGuard | WireGuard | Excellent | Easy |
| Headscale | WireGuard (mesh) | Excellent | Medium |
| OpenVPN | OpenVPN | Good | Medium |
| SoftEther | Multiple | Good | Complex |

---

## 6. Reverse Proxy Comparison

| Feature | Nginx Proxy Manager | Traefik |
|---------|--------------------|---------| 
| Configuration | Web GUI | Labels/Files |
| Auto SSL | ✅ Let's Encrypt | ✅ Let's Encrypt |
| Docker integration | Manual | Automatic discovery |
| Learning curve | Low | Medium |
| Best for | Beginners | DevOps/automation |

---

## 7. Ad Blocking Comparison

| Feature | AdGuard Home | Pi-hole |
|---------|--------------|---------|
| DNS-over-HTTPS | ✅ Built-in | Plugin |
| Web UI | Modern | Classic |
| Resource usage | Low | Low |
| Blocklist management | Easy | Easy |

---

## 8. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [security/](../security/README.md) | Authentication (Authentik) |
| [media-entertainment/](../media-entertainment/README.md) | VPN for *Arr stack |
| [development-ci-cd/](../development-ci-cd/README.md) | Code-server remote access |
