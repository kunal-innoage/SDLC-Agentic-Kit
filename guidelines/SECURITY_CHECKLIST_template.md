# Security Checklist Template

## Project/Feature: [Name]
## Date: [Date]
## Reviewed By: [Name(s)]

*Instructions: Mark each item as Pass (P), Fail (F), Not Applicable (N/A), or To Be Determined (TBD). Add comments for Fail or TBD items.*

| Category                  | Item ID   | Checklist Item                                                                    | Status (P/F/N/A/TBD) | Comments/Mitigation Plan                                                                 |
| :------------------------ | :-------- | :-------------------------------------------------------------------------------- | :------------------- | :--------------------------------------------------------------------------------------- |
| **Authentication**        | AUTH-01   | Are strong password policies enforced (complexity, length, history, expiration)?  |                      |                                                                                          |
|                           | AUTH-02   | Is multi-factor authentication (MFA) implemented for sensitive accounts/actions?  |                      |                                                                                          |
|                           | AUTH-03   | Are brute-force attacks prevented (e.g., account lockout, CAPTCHA, rate limiting)?  |                      |                                                                                          |
|                           | AUTH-04   | Are session management mechanisms secure (e.g., secure cookies, short timeouts)? |                      |                                                                                          |
|                           | AUTH-05   | Are default credentials changed or disabled?                                      |                      |                                                                                          |
| **Authorization**         | AUTHZ-01  | Is the principle of least privilege applied to user roles and permissions?        |                      |                                                                                          |
|                           | AUTHZ-02  | Are access controls enforced consistently across all relevant resources/APIs?     |                      |                                                                                          |
|                           | AUTHZ-03  | Can users elevate privileges inappropriately?                                     |                      | (Should Fail if Yes)                                                                     |
|                           | AUTHZ-04  | Is there a regular review process for user permissions?                           |                      |                                                                                          |
| **Input Validation**      | INP-01    | Is all user-supplied input validated on the server-side?                          |                      |                                                                                          |
|                           | INP-02    | Are inputs validated for type, length, format, and range?                         |                      |                                                                                          |
|                           | INP-03    | Is input validation based on allow-lists rather than block-lists?                 |                      |                                                                                          |
|                           | INP-04    | Is protection against common injection attacks in place (SQLi, XSS, Command Inj.)? |                      |                                                                                          |
| **Data Protection**       | DATA-01   | Is sensitive data encrypted at rest (e.g., PII, credentials)?                   |                      |                                                                                          |
|                           | DATA-02   | Is sensitive data encrypted in transit (using TLS 1.2+)?                        |                      |                                                                                          |
|                           | DATA-03   | Are strong, standard encryption algorithms and key management practices used?   |                      |                                                                                          |
|                           | DATA-04   | Is sensitive data masked or minimized where appropriate (logs, UI)?           |                      |                                                                                          |
|                           | DATA-05   | Are data backups encrypted and stored securely?                                 |                      |                                                                                          |
| **Cryptography**          | CRYPT-01  | Are secure, up-to-date cryptographic algorithms used?                             |                      |                                                                                          |
|                           | CRYPT-02  | Are cryptographic keys managed securely (generation, storage, rotation)?        |                      |                                                                                          |
|                           | CRYPT-03  | Is password hashing implemented using strong, salted algorithms (e.g., Argon2, bcrypt)? |                      |                                                                                          |
| **Error Handling & Logging**| LOG-01    | Are detailed error messages suppressed from users (avoid revealing internals)?  |                      |                                                                                          |
|                           | LOG-02    | Is sufficient logging implemented for security events (login, access changes)?  |                      |                                                                                          |
|                           | LOG-03    | Are logs protected from unauthorized access or modification?                    |                      |                                                                                          |
|                           | LOG-04    | Do logs avoid storing sensitive information (passwords, tokens, PII)?           |                      |                                                                                          |
| **Configuration Mgmt.** | CONF-01   | Are security headers configured appropriately (e.g., CSP, HSTS, X-Frame-Options)? |                      |                                                                                          |
|                           | CONF-02   | Is debugging functionality disabled in production environments?                   |                      |                                                                                          |
|                           | CONF-03   | Are security settings regularly reviewed and updated?                           |                      |                                                                                          |
|                           | CONF-04   | Are third-party dependencies scanned for vulnerabilities and kept up-to-date?   |                      |                                                                                          |
| **API Security**          | API-01    | Are API endpoints properly authenticated and authorized?                          |                      |                                                                                          |
|                           | API-02    | Is rate limiting implemented on APIs to prevent abuse?                            |                      |                                                                                          |
|                           | API-03    | Is input validation performed on API parameters?                                  |                      |                                                                                          |
|                           | API-04    | Are sensitive data exposure minimized in API responses?                         |                      |                                                                                          |
| **Security Testing**      | TEST-01   | Has security testing (e.g., SAST, DAST, penetration testing) been performed?    |                      | (Link to results if available)                                                           |
|                           | TEST-02   | Have identified security vulnerabilities been addressed?                          |                      |                                                                                          |

## Summary

*   **Overall Status:** [e.g., Ready for Release, Needs Remediation]
*   **Key Findings/Risks:** [Summarize major concerns]
*   **Remediation Plan:** [Outline steps to address Fail/TBD items]

## Approvals

*   **Security Reviewer:** [Name/Signature] - Date: _________
*   **Development Lead:** [Name/Signature] - Date: _________ 