# Security Audit of OWASP Juice Shop

Black-box web application security assessment mapped to OWASP Top 10 (2021).
Part of the Cyber Security Internship (Batch 2) Major Project.

## Overview
- **Target:** OWASP Juice Shop (Docker, `bkimminich/juice-shop`) on a Kali Linux VM, host-only lab network
- **Tools:** Kali Linux, Burp Suite Community (Proxy, Repeater, Decoder), Nmap, Firefox, curl
- **Approach:** Setup → Recon & Mapping → Testing → Documentation → Deliverables

## Findings
| ID | Finding | OWASP 2021 | Severity | CVSS |
|---|---|---|---|---|
| F6 | SQL Injection → Admin Login Bypass | A03 Injection | Critical | 9.8 |
| F7 | DOM-Based XSS in Search | A03 Injection | High | 6.1 |
| F8 | IDOR on Shopping Basket | A01 Broken Access Control | High | 6.5 |
| F4 | Admin Config Exposed Without Auth | A01 / A05 | Medium | 5.3 |
| F5 | No Brute-Force Protection on Login | A07 Auth Failures | Medium | 5.3 |
| F2 | Password Hash Exposed in JWT | A02 Crypto Failures | Medium | 5.3 |
| F1 | Credentials Over Plain HTTP | A02 Crypto Failures | Medium | N/A |
| F3 | Missing Security Headers / Wildcard CORS | A05 Misconfiguration | Low-Med | N/A |

## Highlights
- **SQL Injection:** a classic `' OR 1=1--` payload in the login email field returned an admin token without any valid password
- **DOM-Based XSS:** the backend response was empty, confirming the flaw is purely client-side
- **IDOR:** changing `/rest/basket/1` to `/rest/basket/2` returned another user's basket

Every finding includes the endpoint, payload, impact, evidence and remediation advice.

## Repository Contents
- Security Audit of OWASP Juice Shop - Audit Report (PDF)
- OWASP Juice Shop - Vulnerability Matrix (PDF)
- Security Audit of OWASP Juice Shop - Presentation Deck (PDF)
- Major_Project_Presentation_Naitik_Dubey (PPTX)

## Disclaimer
Juice Shop is an intentionally vulnerable training application. All testing was performed on my own
local instance inside an isolated lab network.
