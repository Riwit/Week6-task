# SQL Injection (SQLi)

## 1. Definition

SQL Injection is a web application vulnerability that occurs when an
application includes untrusted user input directly in an SQL query. An
attacker may be able to change the intended query and access or modify
database information without permission.

## 2. How It Happens

A vulnerable application builds a database query by joining SQL commands
with user-provided input instead of using parameterized queries. The
database may then interpret part of the input as SQL code.

## 3. Example

In an authorized training lab such as DVWA, a tester can compare the
result of submitting a normal User ID (for example, `1`) with the result
of a controlled SQL injection test.

Example payload for the DVWA Low-security training module:

``` sql
' OR '1'='1' #
```

This input attempts to change a quoted condition into an always-true
condition. In MySQL, `#` begins a comment. Results depend on the
application's query and database configuration.

## 4. Potential Impact

-   Unauthorized access to database records.
-   Exposure of sensitive information.
-   Unauthorized modification or deletion of data in some circumstances.
-   Potential authentication or authorization bypass, depending on the
    vulnerable query.

## 5. Testing Approach

1.  Obtain permission and confirm the test scope.
2.  Use a deliberately vulnerable lab such as DVWA.
3.  Submit a normal input and record the baseline result.
4.  Submit the controlled test input in the lab.
5.  Compare the output and inspect the HTTP request and response with
    Burp Suite.
6.  Save evidence and document whether the finding is confirmed, not
    confirmed, or inconclusive.

## 6. Mitigation

-   Use parameterized queries or prepared statements.
-   Avoid constructing SQL statements through string concatenation.
-   Validate input according to expected type and format.
-   Give database accounts only the permissions they need.
-   Handle database errors safely and avoid exposing internal details.
-   Keep application frameworks and database software updated.

## 7. Evidence to Include in the Project

-   Screenshot of the normal input and result.
-   Screenshot of the test input and observed result.
-   Burp Suite request and response with session cookies and tokens
    hidden.
-   Risk rating, impact, recommended fix, and retest result.

## 8. Conclusion

SQL Injection can occur when user input changes the intended meaning of
a database query. Parameterized queries are the primary prevention
method. A tester should report a vulnerability only when the collected
evidence supports the finding.

**Safety note:** Perform testing only in your own lab or on systems for
which you have explicit authorization.
