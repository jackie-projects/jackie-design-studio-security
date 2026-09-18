CF-002 — WordPress Login WAF Test
Test Information
Field	Value
Test ID	CF-002-TEST-001
Control	CF-002 — Protect WordPress Login
Target	/wp-login.php
Test Type	Low-impact functional validation
Environment	Production
Status	Investigation Required
Objective

Determine whether the Cloudflare WAF rule protecting the WordPress login endpoint applies the configured Managed Challenge to requests for /wp-login.php.

Configuration Under Test

Match condition:

URI Path equals /wp-login.php


Configured action:

Managed Challenge

Test Method

A normal browser request was made to:

https://jackiedesignstudio.com/wp-login.php


The request was performed from a private/incognito browser session without attempting authentication.

No password guessing, brute-force activity, or other intrusive testing was performed.

Expected Result

The request should encounter the Cloudflare Managed Challenge before access to the WordPress login page is provided.

After successfully completing the challenge, the expected behavior should be consistent with the intended WordPress login workflow.

Observed Result

The browser displayed a Cloudflare-branded processing screen.

The resulting page displayed the message:

"This has been disabled."

The normal WordPress login page was not displayed during this test.

Initial Assessment

The observation indicates that the request was processed by a Cloudflare challenge flow.

However, the result is not yet classified as Pass or Fail because the source of the "This has been disabled." message has not yet been established.

Further investigation is required before changing the WAF configuration.

Next Investigation Steps

Determine whether the message originates from Cloudflare or WordPress.

Review the Cloudflare Security Events for the test request.

Confirm which WAF rule matched the request.

Review the action recorded for the matching event.

Determine whether the configured Managed Challenge is behaving as intended.

Repeat the test after any required configuration changes.

Evidence

Evidence to be collected:

Screenshot of the observed browser response.

Cloudflare Security Events entry for the test request.

Matching WAF rule and action.

Timestamp of the test.

Sensitive information should be removed or redacted before evidence is published to the public repository.
