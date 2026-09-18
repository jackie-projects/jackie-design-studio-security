Security Testing Methodology
Purpose

This document defines the approach used to validate security controls implemented in the Jackie Design Studio e-commerce environment.

The goal is to determine whether security controls behave as intended and to document evidence from controlled testing.

Testing Principles

Testing will follow these principles:

Test only systems and applications controlled by the project owner.

Avoid unnecessary disruption to the live e-commerce environment.

Prefer non-destructive tests.

Document the expected result before testing.

Record the actual result.

Preserve relevant evidence.

Investigate unexpected results.

Retest after remediation.

Production Safety

The Jackie Design Studio website is a live e-commerce store.

Testing performed against production will therefore prioritize low-impact validation.

The following activities will not be performed against production unless an appropriate isolated environment is available:

Destructive testing

Denial-of-service testing

High-volume automated scanning

Password brute-force testing

Exploit attempts that could modify application data

Tests that could affect customer orders or payment processing

Testing Workflow

Each test will follow the same general process:

Control
   ↓
Test Objective
   ↓
Expected Result
   ↓
Controlled Test
   ↓
Observed Result
   ↓
Evidence
   ↓
Assessment
   ↓
Remediation if Required
   ↓
Retest

Test Record

Each security test should document:

Field	Description
Test ID	Unique identifier for the test
Date	Date testing was performed
Control ID	Related security control
Objective	What the test is intended to determine
Method	How the test was performed
Expected Result	Expected security behavior
Actual Result	Observed behavior
Evidence	Screenshot, log, response, or other evidence
Assessment	Whether the observed behavior meets the objective
Follow-up	Remediation or additional testing
Initial Testing Areas
Cloudflare WAF

Testing will validate:

WordPress login protection

XML-RPC protection

Sensitive path protection

Automated traffic challenge

Fake crawler protection

Authentication

Testing will validate:

MFA enforcement

Login behavior

Account separation

Administrative authentication

Authorization

Testing will validate:

Store Manager permissions

Administrator permissions

Access to restricted functionality

Separation of administrative privileges

TLS

Testing will validate:

HTTPS configuration

TLS protocol configuration

Certificate validity

Security-related TLS settings

Application Security

Testing will review:

WordPress configuration

WooCommerce configuration

Installed plugins

Security headers

Publicly accessible resources

Common application security weaknesses

Evidence Handling

Evidence collected during testing will not contain unnecessary customer information, credentials, API keys, payment information, or other sensitive data.

Screenshots and logs included in the project repository will be reviewed and sanitized before publication.

Testing Status
Area	Status
WAF validation	Planned
Authentication testing	Planned
Authorization testing	Planned
TLS validation	Planned
Security headers	Planned
WordPress security review	Planned
WooCommerce security review	Planned
Vulnerability assessment	Planned
Limitations

Testing results represent the conditions observed at the time of testing.

A successful test does not prove that an application is completely secure. Security testing is an ongoing process that should be repeated when the environment, application, plugins, integrations, or security controls change.
