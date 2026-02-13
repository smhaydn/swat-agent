# Semih's Offensive Security Guide (Red Team)

> **Mission:** Find vulnerabilities before the bad guys do.
> **Tools:** Burp Suite, OWASP ZAP, SQLMap, Nmap.

---

## 🏴‍☠️ 1. Reconnaissance (Information Gathering)

Before attacking, know your target.

*   **Subdomain Enumeration:** Use `sublist3r` or `amass`. Find hidden admin panels (`dev.site.com`).
*   **Tech Stack Analysis:** Use `Wappalyzer` logic. Is it Next.js? Use `/_next/static` to confirm. Is it PHP? Look for `wp-admin`.

---

## 💉 2. Injection Attacks (SQLi & XSS)

The classics still work.

*   **SQL Injection:** Test inputs with `' OR 1=1 --`. If error returns, use `sqlmap`.
*   **XSS (Reflected):** Test search bars with `<script>alert(1)</script>`.
*   **XSS (Stored):** Test comments sections.

---

## 🔓 3. Broken Access Control (BAC)

The #1 vulnerability today.

*   **IDOR (Insecure Direct Object Reference):**
    *   Change `user_id=100` to `user_id=101` in URL. Can you see their data?
*   **Privilege Escalation:**
    *   Change cookie `role=user` to `role=admin`.
    *   Try accessing `/admin` without logging in.

---

## 🛠️ 4. Automated Scanning (OWASP ZAP)

Don't do everything manually.

1.  Set up **OWASP ZAP** as proxy.
2.  Browse the site normally to build the tree.
3.  Run **Active Scan** on specific endpoints.

**WARNING:** Only scan servers YOU own or have written permission to test. Unauthorized scanning is illegal.

---
*Optimized for Semih Aydın's Security Testing. 2026-02-13*
