Security Controls Matrix
Purpose

This document records the security controls currently implemented in the Jackie Design Studio e-commerce environment.

Each control is documented with its security objective, implementation location, and planned validation method.

The purpose is to maintain a clear relationship between identified threats, implemented controls, and security testing.

Control Status

The following status definitions are used:

Implemented — The security control has been configured.

Testing — The control is currently being validated.

Planned — The control has been identified but has not yet been implemented.

Needs Review — The control requires additional investigation or validation.

Cloudflare Controls
ID	Control	Implementation	Security Objective	Status
CF-001	Proxied DNS	Cloudflare DNS	Route web traffic through Cloudflare edge services	Implemented
CF-002	WordPress Login Protection	Cloudflare WAF	Reduce automated attacks against WordPress authentication	Implemented
CF-003	XML-RPC Protection	Cloudflare WAF	Reduce unwanted XML-RPC requests	Implemented
CF-004	Sensitive Path Protection	Cloudflare WAF	Block requests targeting selected sensitive resources	Implemented
CF-005	Automated Traffic Challenge	Cloudflare WAF	Challenge selected unidentified automated traffic	Implemented
CF-006	Fake Crawler Protection	Cloudflare WAF	Block selected traffic impersonating known crawlers	Implemented
CF-007	SSL/TLS Configuration	Cloudflare	Protect web traffic in transit	Implemented
CF-008	Email Security	Cloudflare DNS / email configuration	Improve protection of domain email infrastructure	Implemented
CF-001 — Proxied DNS
Objective

Route public web traffic through Cloudflare before it reaches the hosting environment.

Implementation

The primary website DNS record is configured as Proxied through Cloudflare.

Security Benefit

This allows Cloudflare edge security services, including WAF controls, to process applicable web traffic before it reaches the origin environment.

Validation

Future testing will verify that expected web traffic is being processed through Cloudflare and that the origin configuration is consistent with the intended architecture.

Cloudflare WAF Rules
CF-002 — Protect WordPress Login

Match condition:

URI Path equals /wp-login.php


Action:

Managed Challenge

Objective

Apply an additional challenge to requests targeting the WordPress login endpoint.

Observed Cloudflare Activity

The rule is currently active and has recorded matched requests.

Future testing will determine whether controlled requests produce the expected challenge behavior.

CF-003 — Block XML-RPC

Match condition:

URI Path equals /xmlrpc.php
AND
Known Bots does not equal true


Action:

Managed Challenge

Objective

Reduce unwanted or automated requests targeting the WordPress XML-RPC endpoint.

Validation

Controlled requests will be used to determine whether the rule behaves as intended.

CF-004 — Block System Directories

The rule contains conditions targeting selected sensitive paths and file patterns, including:

/wp-content/uploads/ + .php
/wp-includes/ excluding /wp-includes/js/
/.env
/.git
/readme.html


Action:

Block

Objective

Reduce the risk of unauthorized access to selected sensitive files or directories.

Validation

Controlled requests will be used to verify that the intended paths receive the expected response.

CF-005 — Challenge Unknown Scraping and Automated Tools

The rule evaluates selected characteristics including:

Known Bot status

HTTP version

User-Agent characteristics

Action:

Managed Challenge

Objective

Challenge selected traffic that appears to originate from unidentified automated tools.

Validation

Testing will determine whether representative automated requests trigger the intended challenge behavior without unnecessarily affecting legitimate visitors.

CF-006 — Block Fake Crawlers

The rule evaluates User-Agent information for crawler impersonation and Known Bot status.

Action:

Block

Objective

Reduce traffic from requests attempting to identify themselves as recognized search-engine crawlers without being classified as known bots by Cloudflare.

Validation

Controlled requests with test User-Agent values will be used to validate the rule.

WordPress Controls
ID	Control	Implementation	Security Objective	Status
WP-001	Security Plugin	Kadence Security	Provide additional WordPress security controls	Implemented
WP-002	MFA / 2FA	WordPress accounts	Strengthen authentication	Implemented
WP-003	Administrator Separation	WordPress users	Separate privileged administration from routine operations	Implemented
WP-004	Store Manager Account	WordPress role	Apply reduced privileges for routine store operations	Implemented
WP-005	WordPress Hardening	WordPress configuration	Reduce common application attack surface	Implemented
Identity and Access Controls
IAM-001 — Administrator Account Separation
Objective

Separate highly privileged administrative activity from routine e-commerce management.

Implementation

A dedicated Administrator account is maintained separately from the Store Manager account.

Security Principle

This supports the principle of least privilege and reduces the need to use highly privileged credentials for routine store-management activities.

Validation

Role-based authorization testing will be performed to determine which administrative functions are available to each account.

IAM-002 — Multi-Factor Authentication
Objective

Add an authentication factor beyond the account password.

Implementation

Mobile-based two-factor authentication is enabled for privileged access.

Security Principle

MFA provides an additional authentication requirement if a password is compromised.

Validation

Authentication testing will verify that the expected second-factor requirement is enforced.

Application Security Controls
ID	Control	Technology	Objective	Status
APP-001	WordPress Hardening	WordPress	Reduce application attack surface	Implemented
APP-002	WooCommerce Hardening	WooCommerce	Reduce e-commerce application risks	Implemented
APP-003	Security Configuration Review	WordPress / WooCommerce	Identify configuration weaknesses	Implemented
APP-004	Plugin Security Review	WordPress	Reduce risks from installed extensions	Planned
APP-005	Vulnerability Assessment	WordPress / WooCommerce	Identify known security weaknesses	Planned
Transport Security Controls
TLS-001 — HTTPS / TLS
Objective

Protect web traffic between users and the web application.

Implementation

SSL/TLS is configured through Cloudflare.

The project currently uses TLS 1.2 as the configured minimum version.

Validation

TLS configuration will be independently tested and documented using appropriate security testing tools.

Payment Security
PAY-001 — WooPayments

WooPayments is used as the payment-processing service for the e-commerce environment.

The project does not store payment credentials or sensitive payment secrets in the GitHub repository.

Future documentation will distinguish between:

Security controls implemented by the project.

Security controls provided by the payment service.

Security responsibilities that remain with the project owner.

Control Validation Status

At this stage, the controls above have been documented based on their current configuration.

Implementation does not automatically mean effectiveness has been demonstrated.

The next phase of the project will validate individual controls through controlled security testing.

Testing results will be recorded as evidence and linked back to the relevant control ID.

Planned Validation Workflow
Security Control
       ↓
Test Objective
       ↓
Controlled Test
       ↓
Observed Result
       ↓
Evidence
       ↓
Pass / Needs Improvement
       ↓
Remediation
       ↓
Retest

Change Management

Security controls will be reviewed whenever:

Cloudflare rules are modified.

WordPress configuration changes.

WooCommerce configuration changes.

Plugins are added or removed.

User roles change.

New external integrations are introduced.

AI or automated workflows are introduced.

Changes will be documented in the project repository when appropriate.
