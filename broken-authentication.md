# Broken Authentication

## 1. Definition

Broken Authentication describes weaknesses in login, identity
verification, or session management that may allow someone to access an
account or act as another user without proper authorization. In newer
OWASP terminology, related issues are covered by categories such as
Identification and Authentication Failures.

## 2. Common Causes

-   Weak or commonly used passwords.
-   Missing multi-factor authentication where it is needed.
-   No effective rate limiting for repeated login attempts.
-   Insecure session IDs or session handling.
-   Session IDs not being rotated after login or privilege changes.
-   Sessions that remain active for too long.
-   Insecure password reset or account recovery processes.
-   Inadequate protection against credential stuffing.

## 3. Potential Impact

-   Unauthorized account access.
-   Exposure of personal or business information.
-   Account takeover.
-   Abuse of account privileges.
-   Loss of user trust and possible financial or operational damage.

## 4. Safe Testing Approach

Authentication testing must be performed only with permission and test
accounts.

1.  Review the authorized scope and test accounts.
2.  Check whether the application uses secure HTTPS.
3.  Review password and login controls using a small, approved test
    plan.
4.  Check whether repeated failed logins are handled appropriately
    without conducting disruptive attempts.
5.  Inspect session behavior before and after login and logout.
6.  Verify that logout invalidates the session as expected.
7.  Review cookie attributes and session timeouts.
8.  Record evidence without exposing real passwords, session cookies, or
    tokens.

For this Week 6 DVWA task, document this topic as study notes unless
your instructor has specifically included an authentication test in the
authorized scope.

## 5. Mitigation

-   Require strong passwords and block known compromised passwords where
    feasible.
-   Enable multi-factor authentication for sensitive accounts.
-   Apply rate limiting and appropriate protections against automated
    login attempts.
-   Use secure, unpredictable session identifiers.
-   Rotate session IDs after login and privilege changes.
-   Invalidate sessions on logout and after appropriate idle or absolute
    time limits.
-   Set cookie attributes such as `Secure`, `HttpOnly`, and an
    appropriate `SameSite` value.
-   Use secure password reset workflows and store passwords with a
    suitable modern password-hashing algorithm.
-   Monitor authentication events and alert on suspicious patterns.

## 6. Evidence and Reporting

If authentication testing is authorized, document: - The test account
and scope (never its password). - The control being tested. - Expected
behavior and actual behavior. - Evidence with tokens and personal data
redacted. - Impact, risk rating, recommendation, and retest result.

Do not claim a vulnerability exists without supporting evidence.

## 7. Conclusion

Strong authentication and secure session management help prevent account
takeover. Multi-factor authentication, login protections, safe session
handling, and monitoring should work together to protect accounts.
