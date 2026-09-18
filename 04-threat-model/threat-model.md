E-Commerce Threat Model
Purpose

This threat model identifies potential security threats to the Jackie Design Studio e-commerce environment.

The purpose is to identify realistic attack scenarios, understand their potential impact, document existing security controls, and guide future security testing.

The threat model will be updated as the application, infrastructure, and security controls evolve.

Scope

The threat model covers the following components:

Cloudflare DNS and edge services

Cloudflare Web Application Firewall

TLS/SSL configuration

Hostinger hosting environment

WordPress

WooCommerce

WordPress user accounts

Store Manager account

Administrator account

Customer-facing e-commerce functionality

WooPayments integration

Security configuration and logs

Threat Actors

Potential threat actors considered by this project include:

Automated Bots

Automated systems may scan the public website for login pages, vulnerable endpoints, exposed files, or other weaknesses.

Opportunistic Attackers

Attackers may discover the public website through automated scanning or search engines and attempt to exploit common WordPress or web application weaknesses.

Credential Attackers

Attackers may attempt to obtain or guess account credentials through phishing, credential reuse, password attacks, or other methods.

Application Attackers

An attacker may attempt to exploit vulnerabilities in WordPress, WooCommerce, plugins, themes, APIs, or custom application functionality.

Infrastructure Attackers

An attacker who compromises a hosting, DNS, Cloudflare, or administrative account could potentially affect the availability, integrity, or confidentiality of the website.

Threat Scenarios
ID	Threat	Target	Potential Impact	Existing Control	Validation
T-001	Compromised administrator credentials	Administrator account	Unauthorized administrative access	MFA, account separation	Planned
T-002	Automated login attempts	WordPress login	Credential attacks / account abuse	Cloudflare WAF	Planned
T-003	XML-RPC abuse	WordPress XML-RPC endpoint	Automated abuse	Cloudflare WAF	Planned
T-004	Sensitive file access	Web application	Information disclosure	Cloudflare WAF	Planned
T-005	Malicious automated traffic	Public website	Resource abuse / unwanted requests	Cloudflare WAF	Planned
T-006	Excessive Store Manager privileges	Store Manager account	Unauthorized administrative actions	Role separation	Planned
T-007	WordPress vulnerability	WordPress	Application compromise	Hardening / security plugin	Planned
T-008	WooCommerce vulnerability	E-commerce application	Data or functionality compromise	Application hardening	Planned
T-009	Weak transport security	Customer connections	Exposure of data in transit	TLS/SSL	Planned
T-010	DNS account compromise	Domain / DNS	Traffic manipulation or website disruption	Cloudflare account security	Planned
T-011	Hosting account compromise	Hostinger environment	Website compromise or service disruption	Hosting account security	Planned
T-012	Payment integration compromise	WooPayments integration	Payment or transaction impact	Payment provider controls	Planned
Security Objectives

The project focuses on protecting the following security properties.

Confidentiality

Prevent unauthorized access to customer, order, administrative, and configuration information.

Integrity

Prevent unauthorized modification of the website, products, orders, configuration, and other application resources.

Availability

Maintain availability of the e-commerce website and its critical services.

Authentication

Ensure users accessing privileged functions are properly authenticated.

Authorization

Ensure users can perform only the actions appropriate to their assigned role.

Existing Security Controls

The following controls have already been implemented.

Cloudflare

DNS management

Proxied web traffic

Custom WAF rules

WordPress login protection

XML-RPC protection

Sensitive path/file protection

Automated traffic challenge

Fake crawler filtering

SSL/TLS configuration

Email security controls

WordPress / WooCommerce

Security hardening

Security plugin configuration

Multi-factor authentication

Separate Administrator and Store Manager accounts

Role-based access separation

Risk Evaluation

Threats will be evaluated using two primary factors:

Likelihood — How likely the threat is to occur or be attempted.

Impact — The potential effect on confidentiality, integrity, availability, customers, or business operations.

A future risk assessment will classify identified findings using a consistent methodology.

Security Testing Approach

Security testing will be performed against systems controlled by the project owner.

Testing will focus on validating whether implemented security controls behave as intended.

Examples include:

Testing WAF rules against controlled requests

Testing authentication and MFA

Testing role-based authorization

Validating TLS configuration

Reviewing security headers

Assessing WordPress configuration

Assessing WooCommerce configuration

Identifying exposed resources

Reviewing application behavior

Retesting after remediation

Testing that could disrupt production transactions will be performed in an isolated environment whenever practical.

Future Threat Considerations

As the project evolves, additional threats will be considered.

These may include:

API security

Third-party plugin vulnerabilities

Supply-chain risks

Automated e-commerce abuse

Account takeover

Fraud-related activity

Security monitoring

AI agent authentication

AI agent authorization

Prompt injection

Excessive AI agent permissions

Unauthorized automated actions

AI agent audit logging

Limitations

This threat model does not guarantee that all possible threats have been identified or that the environment is completely secure.

The project represents an ongoing learning and security improvement process. Findings and assumptions will be updated as additional testing and research are performed.
