E-Commerce Security Architecture
Overview

Jackie Design Studio is a live e-commerce environment developed and maintained as a hands-on cybersecurity learning project.

The environment uses WordPress and WooCommerce and is hosted on Hostinger. Cloudflare is positioned in front of the hosting environment as the DNS provider and security edge. The primary website traffic is proxied through Cloudflare before reaching the Hostinger origin server.

The architecture follows a layered security approach, with security controls implemented at the DNS/edge, transport, application, and identity layers.

High-Level Architecture
                         INTERNET
                            │
                            ▼
                  ┌────────────────────┐
                  │     CLOUDFLARE     │
                  │                    │
                  │  DNS               │
                  │  WAF               │
                  │  TLS / SSL         │
                  │  Email Security    │
                  │  Edge Protection   │
                  └─────────┬──────────┘
                            │
                         HTTPS
                            │
                            ▼
                  ┌────────────────────┐
                  │     HOSTINGER      │
                  │                    │
                  │  WordPress         │
                  │  WooCommerce       │
                  │  Kadence Security  │
                  └─────────┬──────────┘
                            │
                 ┌──────────┴──────────┐
                 │                     │
                 ▼                     ▼
          ┌──────────────┐      ┌──────────────┐
          │ Administrator│      │ Store Manager│
          │              │      │              │
          │ Privileged   │      │ Store        │
          │ administration│     │ operations   │
          └──────┬───────┘      └──────┬───────┘
                 │                     │
                 └──────────┬──────────┘
                            ▼
                       MFA / 2FA

Architecture Components
Cloudflare

Cloudflare provides the external DNS and security edge for the domain.

The primary website DNS record is configured as Proxied, causing web traffic to pass through Cloudflare before reaching the hosting environment.

Security functions currently implemented include:

DNS management

Web Application Firewall (WAF)

Custom WAF rules

SSL/TLS configuration

Email security controls

Edge traffic filtering

Hostinger

Hostinger provides the underlying web hosting environment.

The server hosts the WordPress application and WooCommerce e-commerce platform.

The hosting environment is intentionally separated from the Cloudflare edge layer so that Cloudflare can provide security controls before traffic reaches the origin environment.

WordPress

WordPress provides the content management system and application framework.

Security controls include:

Account hardening

Administrative account separation

Multi-factor authentication

Security plugin configuration

Additional WordPress hardening measures

WooCommerce

WooCommerce provides the e-commerce functionality, including:

Product management

Shopping cart

Checkout

Order management

Customer accounts

Store administration

WooPayments is used for payment processing.

Identity and Access

Two primary WordPress user roles are maintained:

Administrator — reserved for privileged administrative functions.

Store Manager — used for routine e-commerce management.

The separation is intended to follow the principle of least privilege by avoiding the use of a full administrator account for routine store operations.

Multi-factor authentication is enabled for privileged access.

Security Layers

The current architecture can be viewed as several security layers:

Layer	Technology	Primary Security Purpose
DNS / Edge	Cloudflare	DNS management and traffic control
Web Application Firewall	Cloudflare WAF	Filter selected web requests
Transport	SSL/TLS	Protect data in transit
Hosting	Hostinger	Host the application
Application	WordPress	Application-level security controls
E-Commerce	WooCommerce	Secure store operations
Identity	WordPress roles + MFA	Authentication and authorization
Current Security Philosophy

The project uses a defense-in-depth approach rather than relying on a single security control.

Cloudflare provides security controls before requests reach the origin environment, while WordPress and WooCommerce provide application-level controls. User privileges are separated based on administrative requirements, and MFA provides an additional authentication factor.

Future Architecture Improvements

Future project phases may add:

Security monitoring and centralized logging

Vulnerability assessment

Security testing in an isolated environment

Automated security checks

Security incident documentation

E-commerce workflow automation

AI-assisted workflows

Security controls for AI agents and API access
