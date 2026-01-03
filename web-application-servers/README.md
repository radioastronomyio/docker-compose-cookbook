<!--
---
title: "Web & Application Servers"
description: "Reverse proxies, web servers, and load balancers"
author: "VintageDon"
date: "2025-01-02"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: web-application-servers
---
-->

# Web & Application Servers

Docker Compose recipes for reverse proxies, web servers, load balancers, and SSL/TLS termination.

---

## 1. Contents

```
web-application-servers/
└── README.md           # This file
```

---

## 2. Planned Recipes

| Recipe | Description | Priority |
|--------|-------------|----------|
| traefik | Cloud-native reverse proxy | High |
| nginx-proxy-manager | Nginx with web UI | High |
| caddy | Automatic HTTPS web server | High |
| nginx | Nginx web server | Medium |
| haproxy | High-availability load balancer | Medium |

---

## 3. Use Cases

| Need | Recommended |
|------|-------------|
| Docker-native routing | Traefik |
| Easy web UI management | Nginx Proxy Manager |
| Automatic HTTPS | Caddy |
| Traditional web server | Nginx |
| TCP/HTTP load balancing | HAProxy |

---

## 4. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [security/](../security/README.md) | Authelia for authentication |
| [networking/](../networking/README.md) | DNS and network infrastructure |
