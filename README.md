# OWASP Juice Shop Web Security Assessment

[![Assessment Type](https://img.shields.io/badge/Assessment-Gray_Box-blue?style=for-the-badge&logo=target)](Security_Assessment_Report.pdf)
[![OWASP Top 10](https://img.shields.io/badge/Scope-OWASP_Top_10-red?style=for-the-badge&logo=owasp)](https://owasp.org/www-project-top-ten/)
[![Tools](https://img.shields.io/badge/Tools-Burp_Suite_|_Browser_Fuzzing-orange?style=for-the-badge&logo=burpsuite)](https://portswigger.net/burp)

A comprehensive Gray Box web application security assessment of **OWASP Juice Shop** conducted as part of an internship. This project identifies, exploits and documents 5 critical/high-risk OWASP Top 10 vulnerabilities along with developer-focused remediation strategies.

---

## Executive Summary

* **Target Platform:** OWASP Juice Shop
* **Assessment Methodology:** Gray Box testing utilizing manual fuzzing, parameter tampering, forced browsing and Burp Suite HTTP interception.
* **Findings Summary:** Identified **5 high/critical vulnerabilities** spanning authentication bypass, broken authorization, DOM-based cross-site scripting and sensitive data leakage.

---

## Testing Methodology & Tools

| Category | Tools / Techniques |
| :--- | :--- |
| **Assessment Type** | Gray Box Web Application Security Testing |
| **Primary Tools** | Burp Suite Community Edition, Browser Developer Tools |
| **Techniques** | Manual Request Fuzzing, Forced Browsing, Parameter Injection, DOM Inspection |

---

## Vulnerability Findings

### 1. SQL Injection (Authentication Bypass)
* **Location:** User Login Functionality
* **Severity:** **CRITICAL** (Likelihood: High | Impact: Critical)
* **Details:** Non-sanitized user input in the login form allowed SQL command injection, enabling authentication bypass to log in as the system administrator without valid credentials.
* **Remediation:** Implement Parameterized Queries / Prepared Statements to separate code from user data.

---

### 2. Broken Access Control (Admin Privilege Escalation)
* **Location:** User Login & Administrative Endpoints
* **Severity:** **CRITICAL** (Likelihood: High | Impact: Critical)
* **Details:** Missing server-side authorization checks on restricted API routes enabled unauthenticated/low-privileged users to access and manipulate administrative resources.
* **Remediation:** Adopt a "Deny by Default" access control policy with explicit server-side role verification per request.

---

### 3. DOM-Based Cross-Site Scripting (DOM XSS)
* **Location:** Application Search Functionality
* **Severity:** **HIGH** (Likelihood: Medium | Impact: High)
* **Details:** Unsanitized input from URL parameters is written directly into the Document Object Model (DOM), enabling arbitrary JavaScript execution in victim sessions.
* **Remediation:** Contextually encode dynamic data before rendering; replace unsafe JavaScript sinks (e.g., `innerHTML`) with secure APIs (`textContent`).

---

### 4. Sensitive Data Exposure (Internal File Access)
* **Location:** About Section File Path Redirect
* **Severity:** **HIGH** (Likelihood: High | Impact: High)
* **Details:** Confidential internal files (`legal.md`) were stored within the public web root directory, allowing unauthenticated direct downloads.
* **Remediation:** Store internal assets outside the web root and serve files strictly through an authenticated controller endpoint.

---

### 5. Information Disclosure (Admin Email Leak)
* **Location:** Product Reviews Component
* **Severity:** **MEDIUM** (Likelihood: High | Impact: Medium)
* **Details:** Verbose system responses and review metadata exposed the system administrator's email address, increasing target reconnaissance exposure for phishing attacks.
* **Remediation:** Suppress detailed internal error traces; sanitize administrative email metadata from public API payloads.

---

## Security Assessment Report

The complete security assessment report containing detailed reproduction steps and developer remediation guidance is available in the repository:
[Security Assessment Report (PDF)](https://github.com/Pranav-Poornachandra-S/owasp-juice-shop-security-assessment/blob/main/Security%20Assessment%20Report.pdf)

---
