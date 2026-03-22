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
# 🛡️ API Security Risk Analysis & Threat Assessment
**Future Interns - Cyber Security Track** | **Repository:** `FUTURE_CS_03`

![Status](https://img.shields.io/badge/Status-Completed-success)
![Role](https://img.shields.io/badge/Role-Security_Analyst-blue)
![Focus](https://img.shields.io/badge/Focus-API_Security-critical)

---

## 📊 Executive Summary
This repository contains the comprehensive deliverable for **Task 3**. The objective was to conduct an independent security risk analysis on a public-facing API, evaluate its authentication mechanisms, and translate technical vulnerabilities into actionable business intelligence. 

**Security Analyst:** Nader Abdelgelil

---

## 🎯 Scope of Assessment
* **Target Environment:** JSONPlaceholder API (Sandbox / Demo)
* **Testing Methodology:** Black-box manual API testing
* **Tools Utilized:** Postman, Browser DevTools, REST API analysis
* **Primary Focus:** OWASP API Security Top 10 (Broken Authentication, Excessive Data Exposure, BOLA)

---

## 🚨 Vulnerability Deep Dive: Unauthenticated Data Exposure

| Risk ID | Vulnerability Category | Severity Level | Endpoint Tested |
| :--- | :--- | :--- | :--- |
| **API-V1** | Broken Object Level Authorization (BOLA) | 🔴 **CRITICAL** | `GET /users/{id}` |

### 🔍 Technical Observation
The endpoint responsible for fetching user profile data fails to implement authorization barriers. It accepts requests without validating an `Authorization` header (e.g., Bearer Token, API Key). 

**Simulated Attack Request:**
```http
GET [https://jsonplaceholder.typicode.com/users/1](https://jsonplaceholder.typicode.com/users/1) HTTP/1.1
Host: jsonplaceholder.typicode.com
Accept: application/json
