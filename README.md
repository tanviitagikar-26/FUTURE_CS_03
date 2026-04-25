# FUTURE_CS_03
Task: API Security Risk Analysis

## 🛡️ Project Overview
This repository contains the documentation for **Task 3** of the Cyber Security Internship at **Future Interns**. The objective of this project is to perform a professional, read-only API Security Risk Analysis on a modern SaaS-based API to identify vulnerabilities that could lead to data exposure or unauthorized access.

- **Target API:** ReqRes SaaS (Mock API)
- **Role:** AppSec Consultant / Security Intern

## 🎯 Project Goals
1. Analyze public API endpoints for security flaws.
2. Evaluate authentication and authorization mechanisms.
3. Identify "Information Disclosure" through error messages.
4. Provide professional remediation steps in simple business language.

## 🛠️ Tools Used
* **Postman:** Used for manual testing of HTTP methods (GET, POST, DELETE) and header inspection.
* **Browser DevTools:** Used for analyzing network traffic and security headers.
* **JSON Formatter:** For structured data analysis.

## 🔍 Key Findings (Summary)
1. Verbose Error Messages (High Risk)
* **Observation:** The API returns extremely detailed error messages when authentication fails.
* **Risk:** It provides a "roadmap" for attackers by revealing required headers (`x-api-key`) and session token formats.
* **OWASP Category:** API7:2023 - Server Misconfiguration.

2. Excessive Metadata Exposure (Low Risk)
* **Observation:** API responses include a `_meta` field revealing internal version numbers and documentation links.
* **Risk:** Helps in system fingerprinting and reconnaissance.

3. Lack of Rate Limiting (Medium Risk)
* **Observation:** No evidence of request throttling during high-frequency tests.
* **Risk:** Vulnerable to Denial of Service (DoS) and brute-force attacks.

## 💡 Remediation Recommendations
* **Hardening Error Responses:** Implement generic "Unauthorized" messages.
* **Metadata Stripping:** Remove system internal details from production responses.
* **Throttling:** Implement rate-limiting at the API Gateway level (e.g., 60 requests/min).
* **Secure Headers:** Add `Strict-Transport-Security` and `X-Content-Type-Options` to all API responses.
