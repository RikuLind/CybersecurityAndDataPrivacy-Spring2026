# 1️⃣ Introduction

**Tester(s):**  
- Name:  Riku Lind

**Purpose:**  
- The purpose of this test is to identify vulnerabilities and/or weaknesses in the following areas: 
- Authentication and authorization
- Input validation
- Data encryption

**Scope:**  
- Tested components:  http://localhost:8001
- Exclusions:  Everything else out of scope except http://localhost:8001 and its child directories
- Test approach: Gray-box

**Test environment & dates:**  
- Start:  3.2.2026 19.00
- End:  3.2.2026 23.00
- Test environment details (OS, runtime, DB, browsers): Linux/Debian, Kali Linux, PostgreSQL, Mozilla Firefox inside ZAP, Docker

**Assumptions & constraints:**  
- Docker compose file, which included details about target's services, the environment and credentials.
- Target is a website, more specificly a booking system with registration possibility and a database

---

# 2️⃣ Executive Summary

**Short summary (1-2 sentences):** 

The target possibly has multiple vulnerabilites that could be exploited if not fixed ASAP. 

**Overall risk level:** (Low / Medium / High / Critical)

Critical

**Top 5 immediate actions:**  
1.  Change input validation method so that the application assumes all input is malicious, and then allow a list of acceptable inputs.
2.  Encrypt sensitive user data at rest
3.  Add Anti-CSRF tokens to the HTML submission form
4.  Rewrite the background program using proper deletion of bad character strings
5.  Include necessary headers to help mitigate attack vectors

---

# 3️⃣ Severity scale & definitions

|  **Severity Level**  | **Description**                                                                                                              | **Recommended Action**           |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------- | -------------------------------- |
|      🔴 **High**     | A serious vulnerability that can lead to full system compromise or data breach (e.g., SQL Injection, Remote Code Execution). | *Immediate fix required*         |
|     🟠 **Medium**    | A significant issue that may require specific conditions or user interaction (e.g., XSS, CSRF).                              | *Fix ASAP*                       |
|      🟡 **Low**      | A minor issue or configuration weakness (e.g., server version disclosure).                                                   | *Fix soon*                       |
| 🔵 **Info** | No direct risk, but useful for system hardening (e.g., missing security headers).                                            | *Monitor and fix in maintenance* |


---

# 4️⃣ Findings

> Fill in one row per finding. Focus on clarity and the most important issues.

| ID | Severity | Finding | Description | Evidence / Proof |
|------|-----------|----------|--------------|------------------|
| F-01 | 🔴 High | Path Traversal | URL might be susceptible to be modified to get access to otherwise inaccessible files and directories in the web server | Screenshot in screenshots folder |
| F-02 | 🔴 High | SQL Injection in registration | Username parameter might be vulnerable to SQL injection | Screenshot in screenshots folder | 
| F-03 | 🟠 Medium | Missing Anti-clickjacking Header | The response doesn't protect against Clickjacking attacks | Screenshot in screenshots folder |
| F-04 | 🟠 Medium | Absence of Anti-CSRF Tokens | No Anti-CSRF tokens found, cross-site request forgery is possible | Screenshot in screenshots folder |
| F-05 | 🟠 Medium | Format string error | Data of a string inputted in the username parameter is evaluated as a command | Screenshot in screenshots folder |

---

> [!NOTE]
> Include up to 5 findings total.   
> Keep each description short and clear.

---

# 5️⃣ OWASP ZAP Test Report (Attachment)

**Purpose:**  
- Attach or link your OWASP ZAP scan results (Markdown format preferred).

---

**Instructions:**
1. Check lecture recordings
2. Save the report as `zap_report_round1.md` and link it below.

---
> [!NOTE]
> 📁 **Attach full report:** → `check itslearning` → **Add a link here**

---