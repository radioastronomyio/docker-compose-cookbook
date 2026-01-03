<!--
---
title: "Networking"
description: "Network infrastructure, VPNs, DNS, and ad blocking solutions"
author: "VintageDon"
date: "2025-01-02"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: networking
---
-->

# Networking

Docker Compose recipes for network infrastructure including VPN servers, DNS services, ad blocking, and network security tools.

---

## 1. Contents

```
networking/
├── adguard-home/       # Network-wide ad blocking and DNS
├── openvpn/            # OpenVPN server
├── pihole/             # Pi-hole DNS sinkhole
├── softethervpn/       # Multi-protocol VPN
├── wireguard/          # Modern VPN protocol
└── README.md           # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [adguard-home/](adguard-home/README.md) | AdGuard Home - network-wide ad and tracker blocking | ✅ Active |
| [openvpn/](openvpn/README.md) | OpenVPN - established open-source VPN | ✅ Active |
| [pihole/](pihole/README.md) | Pi-hole - DNS-level ad blocking | ✅ Active |
| [softethervpn/](softethervpn/README.md) | SoftEther VPN - multi-protocol VPN server | ✅ Active |
| [wireguard/](wireguard/README.md) | WireGuard - fast, modern VPN | ✅ Active |

---

## 3. Use Cases

| Tool | Best For |
|------|----------|
| AdGuard Home | Whole-network ad blocking with DoH/DoT support |
| Pi-hole | DNS sinkhole, network statistics |
| WireGuard | Fast VPN with minimal overhead |
| OpenVPN | Broad compatibility, established protocol |
| SoftEther | Multi-protocol support, complex deployments |

---

## 4. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [security/](../security/README.md) | Authentication and access control |
| [web-application-servers/](../web-application-servers/README.md) | Reverse proxies |
