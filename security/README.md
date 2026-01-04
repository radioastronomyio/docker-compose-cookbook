<!--
---
title: "Security"
description: "Authentication, identity management, and secrets"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
status: "Active"
tags:
  - type: directory-readme
  - category: security
---
-->

# Security

Docker Compose recipes for authentication, identity management, SSO, and password/secrets management.

---

## 1. Contents

```
security/
├── authentik/     # Identity provider and SSO
├── vaultwarden/   # Password manager
└── README.md      # This file
```

---

## 2. Recipes

| Recipe | Description | Use Case |
|--------|-------------|----------|
| [authentik](authentik/README.md) | Identity provider and SSO platform | Centralized authentication |
| [vaultwarden](vaultwarden/README.md) | Bitwarden-compatible password manager | Password storage |

---

## 3. Recipe Count: 2

---

## 4. Quick Reference

| Need | Recommended |
|------|-------------|
| Single Sign-On (SSO) | Authentik |
| Password management | Vaultwarden |
| LDAP/SAML provider | Authentik |
| 2FA/TOTP storage | Vaultwarden |

---

## 5. Authentik Capabilities

Authentik provides enterprise-grade identity management:

- **Protocols**: SAML, OAuth2/OIDC, LDAP, SCIM
- **MFA**: TOTP, WebAuthn, SMS, Email
- **Flows**: Customizable authentication workflows
- **Proxy**: Forward auth for reverse proxies

Integration with Traefik/Nginx Proxy Manager enables SSO across all self-hosted services.

---

## 6. Vaultwarden Features

Vaultwarden is a lightweight Bitwarden-compatible server:

- Full Bitwarden client compatibility (browser, mobile, desktop)
- Organizations and sharing
- TOTP authenticator
- File attachments
- Emergency access

---

## 7. Recommended Architecture

```
                  ┌─────────────┐
                  │  Authentik  │  (Identity Provider)
                  └──────┬──────┘
                         │ SSO
         ┌───────────────┼───────────────┐
         │               │               │
    ┌────▼────┐    ┌─────▼─────┐   ┌─────▼─────┐
    │ Traefik │    │  Grafana  │   │ BookStack │
    │ (proxy) │    │           │   │           │
    └─────────┘    └───────────┘   └───────────┘

    ┌─────────────┐
    │ Vaultwarden │  (Credentials storage)
    └─────────────┘
```

---

## 8. Planned Recipes

| Recipe | Description | Priority |
|--------|-------------|----------|
| keycloak | Enterprise identity platform | Medium |
| authelia | Lightweight SSO proxy | Medium |
| vault | HashiCorp secrets management | Low |

---

## 9. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [networking/](../networking/README.md) | Reverse proxy integration |
| [monitoring-logging/](../monitoring-logging/README.md) | Auth for dashboards |
