# FUTURE_CS_03: API Security Risk Analysis 🛡️

## 📌 Project Overview
This repository contains the deliverables for **Task 3** of the Future Interns Cyber Security track. The objective of this project is to conduct a security risk analysis on a public API, identify authentication/authorization vulnerabilities, and translate technical findings into a business-friendly risk report.

**Analyst:** Nader Abdelgelil

## 🛠️ Tools & Technologies Used
* **API Testing:** Postman
* **Target Environment:** JSONPlaceholder API (Testing Sandbox)
* **Documentation:** GitHub, Markdown, PDF

## 🚨 Key Security Findings
During the assessment, a critical vulnerability was identified:

* **Vulnerability:** Broken Object Level Authorization (BOLA) / Unauthenticated Data Exposure.
* **Endpoint Tested:** `GET https://jsonplaceholder.typicode.com/users/1`
* **Status Code:** `200 OK` (Returned without any Auth headers)
* **Description:** The API endpoint exposes sensitive Personal Identifiable Information (PII) such as names, emails, and physical addresses without requiring any form of authentication (e.g., API keys, Bearer Tokens).

## 💼 Business Impact
If deployed in a production SaaS environment, this flaw would allow attackers to automate the extraction of the entire user database. This leads to:
* Severe data breaches.
* Non-compliance with data protection regulations.
* Significant loss of client trust and reputational damage.

## 🛡️ Remediation Strategy
1. **Enforce Authentication:** Implement strict JSON Web Token (JWT) validation on all endpoints handling user data.
2. **Implement Authorization:** Ensure the system verifies that the authenticated user has the explicit right to access the requested resource object.
3. **Rate Limiting:** Deploy API gateways to restrict the number of requests per IP to mitigate automated scraping.

## 📂 Repository Contents
