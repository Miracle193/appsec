# Intro to OWASP Top 10 (2021)

Per OWASP, the OWASP Top 10 is a standard awareness document for developers and web application security. It represents a broad consensus about the most critical security risks to web applications. The vulnerabilities are:

1. Broken Access Control
2. Cryptographic Failures
3. Injection (SQL, NoSQL, etc.)
4. Insecure Design
5. Security Misconfiguration
6. Vulnerable/Outdated Components
7. Identification and Authentication Failures
8. Software and Data Integrity Failures
9. Security Logging and Monitoring Failures
10. Server-Side Request Forgery (SSRF)

### AO1:2021-Broken Access Control
Broken Access Control allows attackers to bypass authorisation, allowing them to view sensitive data or perform tasks they aren't supposed to (From TryHackMe's OWASP Top 10 - 2021).

IDOR or Insecure Direct Object Reference refers to an access control vulnerability where you can access resources you wouldn't ordinarily be able to see. This occurs when the programmer exposes a Direct Object Reference, which is just an identifier that refers to specific objects within the server. By object, we could mean a file, a user, a bank account in a banking application, or anything really. We get taken to a URL like this `https://bank.thm/account?id=111111` (From TryHackMe's OWASP Top 10 - 2021).

Real World Example: Viewing another user's account details by changing the user ID in the URL.

### A02:2021-Cryptographic Failures
A cryptographic failure refers to any vulnerability arising from the misuse (or lack of use) of cryptographic algorithms for protecting sensitive information (From TryHackMe's OWASP Top 10 - 2021).

Real World Example: Storing passwords in plaintext or using HTTP instead of HTTPS.

### A03:2021-Injection
These flaws occur because the application interprets user-controlled input as commands or parameters (From TryHackMe's OWASP Top 10 - 2021).

SQL Injection: This occurs when user-controlled input is passed to SQL queries. As a result, an attacker can pass in SQL queries to manipulate the outcome of such queries. This could potentially allow the attacker to access, modify and delete information in a database when this input is passed into database queries. This would mean an attacker could steal sensitive information such as personal details and credentials (From TryHackMe's OWASP Top 10 - 2021).

Command Injection: This occurs when user input is passed to system commands. As a result, an attacker can execute arbitrary system commands on application servers, potentially allowing them to access users' systems (From TryHackMe's OWASP Top 10 - 2021).

Real World Example: SQL, NoSQL, OS command, and LDAP injection.

### A04:2021-Insecure Design
Insecure design refers to vulnerabilities which are inherent to the application's architecture. They are not vulnerabilities regarding bad implementations or configurations, but the idea behind the whole application (or a part of it) is flawed from the start. Most of the time, these vulnerabilities occur when an improper threat modelling is made during the planning phases of the application and propagate all the way up to your final app (From TryHackMe's OWASP Top 10 - 2021).

Real World Example: No business logic limits on critical actions (e.g., transfer funds).

### A05:2021-Security Misconfigurations
Security Misconfigurations are distinct from the other Top 10 vulnerabilities because they occur when security could have been appropriately configured but was not. Even if you download the latest up-to-date software, poor configurations could make your installation vulnerable (From TryHackMe's OWASP Top 10 - 2021).

Real Word Example: Default accounts with unchanged passwords, overly-detailed error messages, not using HTTP security headers.

### A06:2021-Vulnerable/Outdated Components
This includes use of outdated libraries or dependencies with known vulnerabilities.

Real World Example: Running an app with an old version of Log4j.

### A07:2021-Identification and Authentication Failures
This involves weak or flawed authentication mechanisms. If an attacker is able to gain access to a user's account, they may be able to access sensitive information or elevate privileges.

Real World Example: brute force attacks, weak credentials, weak session cookie, no MFA

### A08:2021-Software and Data Integrity Failures
This vulnerability arises from code or infrastructure that uses software or data without using any kind of integrity checks. Since no integrity verification is being done, an attacker might modify the software or data passed to the application, resulting in unexpected consequences (From TryHackMe's OWASP Top 10 - 2021).

Real World Example: Unsigned or unverified software updates.

### A09:2021-Securty Logging and Monitoring Failures
This involves lack of logging, detection, and alerting for security-relevant events.

Real World Example: Breach goes unnoticed because logging was disabled.

### A10:2021-Server-Side Request Forgery (SSRF)
This type of vulnerability occurs when an attacker can coerce a web application into sending requests on their behalf to arbitrary destinations while having control of the contents of the request itself. SSRF vulnerabilities often arise from implementations where our web application needs to use third-party services (From TryHackMe's OWASP Top 10 - 2021).

Real World Example: Attacker causes the server to request internal resources (e.g., metadata service).
