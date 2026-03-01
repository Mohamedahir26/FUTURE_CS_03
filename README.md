# 🛡️ API Security Risk Analysis: Project Overview

This project presents a comprehensive security assessment conducted on a public REST API (**JSONPlaceholder**). The primary objective was to identify and simulate real-world API vulnerabilities to understand their impact on data integrity and system availability.

---

## 🛠️ Tools Used
The following tools and environments were utilized to perform reconnaissance and vulnerability testing:
* **Postman:** For building API requests, managing collections, and automating security test runs.
* **JSONPlaceholder API:** Used as a controlled test environment to simulate real-world data interactions.
* **Browser-based DevTools:** Used for initial endpoint inspection and header analysis.

---

## 🔍 Key Security Findings
The assessment identified several high-risk vulnerabilities that directly compromise the **CIA Triad** (Confidentiality, Integrity, and Availability):

### 1. Broken Authentication
* **Finding:** The API does not require any credentials (JWT, API Keys, or Bearer Tokens) to access sensitive data.
* **Risk:** **High**. Any unauthorized user can retrieve internal system data simply by sending a request.

### 2. Excessive Data Exposure (PII)
* **Finding:** API responses return full user profiles, including private emails, physical addresses, and geo-location coordinates.
* **Risk:** **High**. This exposes **Personally Identifiable Information (PII)**, which can lead to identity theft and privacy violations.

### 3. Lack of Rate Limiting
* **Finding:** The system processes an unlimited number of requests from a single source without throttling or blocking.
* **Risk:** **Medium**. The API is highly vulnerable to **Denial of Service (DoS)** attacks and automated data scraping.

### 4. Injection / Lack of Input Validation
* **Finding:** The API accepts unsanitized script inputs in request payloads (POST/PUT).
* **Risk:** **High**. This creates a gateway for **Cross-Site Scripting (XSS)** and other malicious code execution.

---

## 🛡️ Remediation & Security Recommendations
To secure the environment and mitigate the identified risks, the following industry-standard strategies are recommended:

| Vulnerability | Remediation Strategy |
| :--- | :--- |
| **Authentication** | Implement **OAuth2** or **JWT (JSON Web Tokens)** for all private endpoints. |
| **Data Exposure** | Apply **Response Filtering** to return only necessary fields; enforce **RBAC**. |
| **Rate Limiting** | Deploy an API Gateway to enforce **Request-per-Minute (RPM)** limits. |
| **Input Validation** | Use **Schema Validation** and strictly sanitize all user-supplied data. |

---

## 🧪 Conclusion
The analysis concludes that while the API is functional for testing, it lacks the fundamental security layers required for production. Implementing the recommended controls will significantly reduce the attack surface and protect the integrity of the system and its users.

