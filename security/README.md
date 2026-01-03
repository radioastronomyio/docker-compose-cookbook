<!--
---
title: "Security"
description: "Authentication, secrets management, and security tools"
author: "VintageDon"
date: "2025-01-02"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: security
---
-->

# Security

Docker Compose recipes for authentication, identity management, secrets management, and security scanning tools.

---

## 1. Contents

```
security/
└── README.md           # This file
```

---

## 2. Planned Recipes

| Recipe | Description | Priority |
|--------|-------------|----------|
| keycloak | Identity and access management | High |
| authelia | SSO and 2FA proxy | High |
| vaultwarden | Bitwarden-compatible password manager | High |
| vault | HashiCorp secrets management | Medium |
| authentik | Identity provider | Medium |
| crowdsec | Collaborative security engine | Medium |
| trivy | Container vulnerability scanning | Low |

---

## 3. Use Cases

| Need | Recommended |
|------|-------------|
| SSO for services | Keycloak or Authentik |
| Reverse proxy auth | Authelia |
| Password management | Vaultwarden |
| Application secrets | HashiCorp Vault |
| Intrusion prevention | CrowdSec |

---

## 4. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [web-application-servers/](../web-application-servers/README.md) | Reverse proxies for auth integration |
| [networking/](../networking/README.md) | VPN and network security |
