The goal of this README is to provide a clear mapping between the API security maturity questions and the `.api-security.yaml` file. This guide will help developers and security engineers understand how to properly fill out the YAML file to ensure a consistent and auditable security posture for all APIs.

---

### API Security Maturity Validation Guide

This document maps the API security maturity questionnaire to the fields in the `.api-security.yaml` file. The score for each item should be either **`1`** (if the practice is implemented) or **`0`** (if it's not).

The GitHub Actions workflow will check this file on every pull request. If the total score falls below the minimum required threshold, the PR will be blocked.

### `api_security_maturity`

This is the top-level object in the YAML file. All security categories are nested under this key.

---

### I. Authentication and Authorization

This section of the YAML file evaluates how your API handles access control.

-   **Question:** Do all API endpoints require authentication?
    -   **YAML Field:** `authentication_authorization.all_endpoints_require_auth`
-   **Question:** Are you using a modern, industry-standard authentication protocol like OAuth 2.0 or OpenID Connect?
    -   **YAML Field:** `authentication_authorization.use_oauth2_oidc`
-   **Question:** Do all API tokens have a short lifespan and are they revocable?
    -   **YAML Field:** `authentication_authorization.tokens_are_short_lived`
-   **Question:** Is an authorization check performed on every request to ensure the user has the correct permissions?
    -   **YAML Field:** `authentication_authorization.authorization_per_request`
-   **Question:** Are you using a fine-grained access control model (e.g., Role-Based Access Control) to limit what users can do?
    -   **YAML Field:** `authentication_authorization.fine_grained_access_control`
-   **Question:** Is your authentication logic protected against brute-force and credential stuffing attacks (e.g., with rate limiting or CAPTCHA)?
    -   **YAML Field:** `authentication_authorization.protection_against_brute_force`

---

### II. Data Security

This section assesses how you protect sensitive data, both in transit and at rest.

-   **Question:** Is all API traffic encrypted using TLS 1.2 or higher with strong cipher suites?
    -   **YAML Field:** `data_security.traffic_is_encrypted`
-   **Question:** Do you have a strict input validation and sanitization process to prevent injection attacks (SQLi, XSS, etc.)?
    -   **YAML Field:** `data_security.input_validation_and_sanitization`
-   **Question:** Do you limit the data returned in API responses to only what is absolutely necessary for the client?
    -   **YAML Field:** `data_security.limit_data_in_responses`
-   **Question:** Are sensitive data and personally identifiable information (PII) encrypted at rest in your database?
    -   **YAML Field:** `data_security.data_encrypted_at_rest`
-   **Question:** Are there measures in place to prevent **Broken Object Level Authorization (BOLA)** attacks, where a user can access another user's data by simply changing an ID in the URL?
    -   **YAML Field:** `data_security.protection_against_bola`

---

### III. Threat and Vulnerability Management

This section covers the proactive and reactive measures you have in place to defend your API.

-   **Question:** Are your APIs protected by a Web Application Firewall (WAF) or an API Gateway?
    -   **YAML Field:** `threat_vulnerability_management.protected_by_waf`
-   **Question:** Have you implemented rate limiting to protect against Denial-of-Service (DoS) attacks and API abuse?
    -   **YAML Field:** `threat_vulnerability_management.rate_limiting_is_implemented`
-   **Question:** Do you regularly scan your APIs and their dependencies for known vulnerabilities?
    -   **YAML Field:** `threat_vulnerability_management.regular_vulnerability_scans`
-   **Question:** Do you have a process to prevent **Server-Side Request Forgery (SSRF)**, where an attacker can force your server to make a request to an internal resource?
    -   **YAML Field:** `threat_vulnerability_management.protection_against_ssrf`

---

### IV. Operational Security

This section focuses on the operational practices that support API security.

-   **Question:** Are all security-related events (authentication failures, authorization errors, etc.) logged and monitored?
    -   **YAML Field:** `operational_security.security_events_are_logged`
-   **Question:** Do you have an established process for managing API keys and secrets, including secure storage and rotation?
    -   **YAML Field:** `operational_security.secure_secrets_management`
-   **Question:** Do your error messages avoid leaking sensitive information about the application's internal structure?
    -   **YAML Field:** `operational_security.no_sensitive_info_in_errors`
-   **Question:** Do you have a documented incident response plan specifically for API security incidents?
    -   **YAML Field:** `operational_security.documented_incident_response`
-   **Question:** Are security checks integrated into your CI/CD pipeline to automatically find and fix vulnerabilities?
    -   **YAML Field:** `operational_security.security_in_ci_cd`