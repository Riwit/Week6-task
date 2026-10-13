# Security Misconfiguration

## 1. Definition

Security Misconfiguration occurs when an application, server, framework,
database, or cloud service is configured insecurely. It can happen at
any level of a technology stack and may expose information or
functionality that should not be available.

## 2. Common Examples

-   Default accounts or credentials remain enabled.
-   Debug mode is enabled in a production environment.
-   Detailed error messages reveal internal paths or software details.
-   Directory listing is enabled unnecessarily.
-   Unneeded services or ports are exposed.
-   Security headers are missing or incorrectly configured.
-   Software or components are outdated.
-   Permissions are broader than required.
-   Test files, sample applications, or backups are publicly accessible.

## 3. Potential Impact

-   Disclosure of system or application information.
-   Unauthorized access to administrative features.
-   Increased attack surface.
-   Exposure of files or data.
-   Greater chance that another vulnerability can be exploited.

The impact depends on the exact configuration issue, exposure, and
available protections.

## 4. Testing Approach

1.  Confirm the authorized scope and identify the lab target.
2.  Review the application's visible configuration and security
    settings.
3.  Run OWASP ZAP against the authorized local DVWA target.
4.  Review the Alerts tab and record each relevant alert.
5.  Check the affected URL, evidence, confidence, risk level, and
    remediation advice.
6.  Validate important findings manually where appropriate.
7.  Export the report and document limitations.

A scanner alert is not automatically proof of a vulnerability. Confirm
the evidence and avoid treating every missing header as a high-risk
issue.

## 5. Mitigation

-   Use a secure configuration baseline.
-   Remove default accounts, sample files, and unnecessary services.
-   Disable debug mode and avoid exposing detailed errors to users.
-   Apply security patches promptly.
-   Restrict access using least privilege.
-   Configure security headers appropriately for the application.
-   Disable directory listing unless specifically required.
-   Review cloud storage, network access, and permissions.
-   Automate configuration checks and perform periodic reviews.

## 6. Evidence to Include

-   Screenshot of the relevant ZAP alert.
-   Affected URL and alert description.
-   Evidence and confidence reported by the tool.
-   Risk rating justified by impact and context.
-   Recommended configuration change.
-   Retest result after remediation, if a fix was applied.

## 7. Conclusion

Secure configuration reduces unnecessary exposure and helps prevent
avoidable weaknesses. Regular reviews, patching, least privilege, and
validated security scans help keep applications and servers secure.

**Safety note:** Scan only your own lab or systems for which you have
explicit authorization.
