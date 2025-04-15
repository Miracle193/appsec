# Threat Model for OWASP Juice Shop

## Threat Model Information
Application Version:

Description: The OWASP Juice Shop is an intentionally vulnerable web app designed for security training and practice, awareness demos, and CTFs. The app is written in Node.js, Express and Angular. 

Document Owner: Miracle193

Participants: Miracle193

Reviewer: Miracle193

## STRIDE Threat Categories
| STRIDE Category | Potential Threat | Affected Component | 
|---       |---       |---     |
| Spoofing | Threat actor impersonates another through:<br>• Reuse of JWTs<br>• Lack of 2FA<br>• Predictable user IDs (e.g. admin email is disclosed). | Authentication Service |
| Tampering | • Manipulation of API requests (e.g. price or cart data)<br>• Insecure direct object references (IDOR) in search URL. | Rest API, Frontend |
| Repudiation | • Users can delete data without proper logging.<br>• No non-repudiation or audit trails for key actions (e.g., adding item to cart, paying for juice). | Logging System |
| Information Disclosure | • Accessing sensitive data via insecure API endpoints (e.g., see /ftp).<br>• Accessing user details via admin account (e.g a user’s cart). | Rest API, Database |
| Denial of Service | • Repeated API calls to overload resources (checkout, login). | Rest API, Database |
| Elevation of Privilege | • Accessing admin endpoints via direct URL manipulation. | Rest API, Authentication |

## Risk Analysis
