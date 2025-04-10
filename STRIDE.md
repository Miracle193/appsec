# STRIDE
* This stands for Spoofing, Tampering, Repudiation, Information Disclosure, Elevation of Privilege.
* This is a threat model developed by Microsoft, which helps identify and categorise potential security threats in software development and system design.

| Category | Definition | Policy Violated | 
|---       |---       |---     |
| Spoofing | Unauthorised access or impersonation of a user or system. | Authentication
| Tampering | Unauthorised modification or manipulation of data or code. | Integrity
| Repudiation | Ability to deny having acted, typically due to insufficient auditing or logging. | Non-repudiation
| Information Disclosure | Unauthorised access to sensitive information, such as personal or financial data. | Confidentiality
| Denial of Service | Disruption of the system's availability, preventing legitimate users from accessing it. | Availability
| Elevation of Privilege | Unauthorised elevation of access privileges, allowing threat actors to perform unintended actions. | Authorisation

## STRIDE PROCESS
### 1. System Decomposition
Break down all accounted systems into components, such as applications, networks, and data flows. Understand the architecture, trust boundaries, and potential attack surfaces.

### 2. Apply STRIDE Categories
For each component, analyse its exposure to the six STRIDE threat categories. Identify potential threats and vulnerabilities related to each category.
### 3. Threat Assessment
Evaluate the impact and likelihood of each identified threat. Consider the potential consequences and the ease of exploitation and prioritise threats based on their overall risk level.

### 4. Develop Countermeasures 
Design and implement security controls to address the identified threats tailored to each STRIDE category. For example, to enhance email security and mitigate spoofing threats, implement DMARC, DKIM, and SPF, which are email authentication and validation mechanisms that help prevent email spoofing, phishing, and spamming.

### 5. Validation and Verification
Test the effectiveness of the implemented countermeasures to ensure they effectively mitigate the identified threats. If possible, conduct penetration testing, code reviews, or security audits.

### 6. Continuous Improvement
Regularly review and update the threat model as the system evolves and new threats emerge. Monitor the effective countermeasures and update them as needed.


## References
TryHackMe's Threat Modeling Room


