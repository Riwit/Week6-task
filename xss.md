# Cross-Site Scripting (XSS)

## 1. Definition

Cross-Site Scripting (XSS) is a web application vulnerability in which
untrusted content is handled in a way that allows script code to execute
in a user's browser. Depending on the context, XSS may allow page
manipulation, phishing, or actions performed in the context of the
affected site.

## 2. Main Types of XSS

### Reflected XSS

The submitted input is returned in the immediate HTTP response and is
interpreted unsafely by the browser. It is not necessarily saved by the
application.

### Stored XSS

The submitted content is saved by the application, such as in a comment
or guestbook entry, and is later displayed to users. If rendered
unsafely, the script may execute whenever the affected content is
viewed.

### DOM-Based XSS

Client-side JavaScript handles untrusted data in an unsafe way, causing
script execution in the browser's Document Object Model (DOM). The
problem may occur primarily in client-side code.

## 3. Safe Training-Lab Example

In the local DVWA lab, testers may use a harmless proof-of-concept such
as:

``` html
<script>alert('XSS')</script>
```

Use this only in your own intentionally vulnerable training environment.
Observe whether the input is blocked, displayed as text, or executed. Do
not test payloads on websites without permission.

## 4. Potential Impact

-   Manipulation of page content.
-   Display of misleading forms or links.
-   Actions performed as the affected user in some circumstances.
-   Exposure of information accessible to browser scripts, depending on
    application protections.
-   Damage to user trust and application reputation.

## 5. Testing Approach

1.  Confirm authorization and scope.
2.  In DVWA, open the Reflected XSS module.
3.  Submit a normal value and record the result.
4.  In the lab, submit the harmless test payload and record what
    happens.
5.  Open the Stored XSS module and test the guestbook or message field.
6.  Reload the page to check whether the stored entry persists.
7.  Inspect relevant requests and responses in Burp Suite.
8.  Capture evidence and report the actual result accurately.

## 6. Mitigation

-   Apply context-aware output encoding.
-   Use safe templating methods that encode untrusted values by default.
-   Sanitize HTML when users are intentionally allowed to submit HTML.
-   Avoid unsafe DOM APIs and use safe alternatives.
-   Apply a suitable Content Security Policy (CSP) as an additional
    layer, not as the only fix.
-   Use secure cookie settings, including HttpOnly where appropriate, to
    reduce some cookie exposure risks.

## 7. Evidence to Include

-   Screenshot of the submitted test input.
-   Screenshot of the observed browser output.
-   For Stored XSS, screenshot showing whether the entry remains after
    reloading.
-   Relevant Burp request/response with sensitive values redacted.
-   Risk, impact, remediation, and retest result.

## 8. Conclusion

XSS occurs when untrusted content is interpreted as executable script.
Reflected and stored XSS differ mainly in how the input reaches the
victim. Safe output encoding and secure rendering are central defenses.

**Safety note:** Perform XSS testing only in your own lab or on systems
for which you have explicit authorization.
