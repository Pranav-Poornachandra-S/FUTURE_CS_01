This repository documents the completion of Task 1: Web Application Security Testing for the Future Interns Cybersecurity Internship. The goal of this task was to perform a penetration test on a target web application—the intentionally vulnerable OWASP Juice Shop—to identify, exploit, and document critical security flaws.

The primary deliverable is a detailed security assessment report and the documentation of Proof-of-Concept (PoC) steps for each vulnerability found.

Objectives:
1. Vulnerability Identification: Identify vulnerabilities categorized under the OWASP Top 10, including Injection and Broken Access Control.

2. Exploitation: Successfully execute exploits to demonstrate the impact of the flaws.

3. Reporting: Create a professional security assessment report detailing findings and providing actionable mitigation strategies.

Key Vulnerabilities Identified:
During the assessment, five high-impact vulnerabilities were successfully discovered and documented. These findings demonstrate proficiency in identifying fundamental web security weaknesses.

1. SQL Injection (Critical Risk): Successfully bypassed authentication via the login form.

2. Broken Access Control (Critical Risk): Gained unauthorized access to administrator resources by brute forcing the password using the Intruder functionality of Burp Suite.

3. DOM XSS (High Risk): Exploited the search functionality, writing user input directly to the DOM without encoding.

4. Sensitive Data Exposure (High Risk): Found an internal, confidential file publicly accessible due to improper file system configuration.

5. Information Disclosure (Medium Risk): Products' reviews in the home page inadvertently disclosed the administrator's email address along with a few user's emails.
