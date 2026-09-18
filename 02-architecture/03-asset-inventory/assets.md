E-Commerce Asset Inventory
Purpose

This document identifies the primary assets that make up the Jackie Design Studio e-commerce environment.

The inventory is used to establish the scope of the security project and identify systems, accounts, services, and data that require protection.

Asset Classification

Assets are grouped into the following categories:

Infrastructure

Applications

Accounts and identities

Data

External services

Infrastructure Assets
Asset	Technology / Service	Purpose	Security Consideration
Domain	Cloudflare DNS	Public identity and DNS resolution	DNS integrity and account security
DNS / Edge	Cloudflare	Traffic routing and edge security	Unauthorized DNS changes, malicious traffic
Web Hosting	Hostinger	Hosts the website and application	Server compromise, unauthorized access
Web Application	WordPress	Website/application platform	Vulnerabilities, authentication, plugins
E-Commerce Platform	WooCommerce	Store and order functionality	Account, order, and application security
Application Assets
WordPress

WordPress is the primary content management system and application framework.

Security-relevant components include:

Authentication

User accounts

Plugins

Themes

Administrative functionality

Configuration

Database-backed application data

WooCommerce

WooCommerce provides the e-commerce functionality.

Security-relevant components include:

Customer accounts

Product information

Orders

Checkout functionality

Store management

Payment integration

Identity Assets

The environment currently uses separate accounts for administrative and store-management activities.

Identity	Purpose	Privilege Level
Administrator	System and WordPress administration	High
Store Manager	Routine e-commerce operations	Limited compared with Administrator

Multi-factor authentication is enabled for privileged access.

Data Assets

The e-commerce environment may process or store information associated with:

Customer accounts

Customer contact information

Product information

Order information

Store configuration

Website content

Security logs

Administrative activity

Payment processing is provided through WooPayments. Sensitive payment information is not intentionally stored in this GitHub repository.

External Service Dependencies

The application relies on external services for critical functionality.

Service	Function	Security Dependency
Cloudflare	DNS, edge security, WAF, TLS	Cloudflare account and configuration security
Hostinger	Web hosting	Hosting account and server security
WooPayments	Payment processing	Payment account and integration security
Security Boundaries

The primary security boundary exists between the public Internet and the application environment.

Traffic to the website is proxied through Cloudflare before reaching the Hostinger hosting environment.

Additional security boundaries exist between:

Public users and authenticated users

Store Manager and Administrator privileges

Cloudflare and the hosting origin

Application functionality and administrative functionality

Asset Protection Priorities

The project will prioritize protection of:

Administrative accounts

Customer and order information

E-commerce functionality

WordPress and WooCommerce application integrity

Domain and DNS configuration

Hosting infrastructure

Payment integration

Security configuration and logs

Inventory Maintenance

This inventory will be updated as the environment changes and additional services, applications, integrations, or security controls are introduced.
