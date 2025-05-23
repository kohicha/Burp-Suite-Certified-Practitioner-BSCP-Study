---
Title: Testing for CSRF
tags:
  - CSRF
---
CSRF is basically an attack that lets the attacker perform an action on behalf of the victim, usually through a carefully constructed web request.

> [!info] What are the requirements to perform a csrf?
> 1. An action to be performed, e.g, change email, perform a request that can elevate another user's permission, etc.
> 2. A session cookie, this means that in order for an attacker to be able to perform a csrf, the user must be logged in, which requires a session cookie.
> 3. A predictable parameter, for example changing an email only requires you to place an email on the parameter request. An unpredictable parameter could be a password, to change the email.

> [!faq] Where do you deliver these exploits?
> An example of where you can deploy a csrf request, is in a feature of a website that is vulnerable to reflected xss.
> ```html
> <img src="http://vulnerable-site.com/email/change?email=pwned@evil-user.net">
> ```
> This would automatically create the request, upon the victim visiting the site. Another one would be an attacker creating a website of their own, that upon visiting, will redirect the user to a csrf payload.

# COMMON CSRF FLAWS
1. [[CSRF where token validation depends on request method]]
2. [[CSRF where token validation depends on token being present]]















