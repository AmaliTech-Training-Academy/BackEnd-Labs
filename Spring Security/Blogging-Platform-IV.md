# Blogging Platform

---

### Project Overview

This phase of the Blogging Platform emphasizes building secure, scalable, and production-ready web backends that can safely handle authentication, authorization, and cross-origin requests. Learners will apply Spring Security concepts to secure REST and GraphQL APIs using JWT-based authentication, Google OAuth2 login, and Role-Based Access Control (RBAC).

Additionally, this phase explores security-related Data Structures and Algorithms (DSA) concepts such as hashing, encryption, and secure token validation to enhance data protection and access integrity.

---

### Project Objectives

By the end of this project, learners will be able to:

- Apply Spring Security configurations to enforce authentication, authorization, and access control across REST and GraphQL endpoints
- Implement JWT authentication, Google OAuth2 login, and secure password hashing using BCrypt
- Configure and analyze CORS and CSRF policies for different clients (Postman, browsers, and JavaFX)
- Apply DSA principles such as hashing, encryption, and token validation to strengthen security and session management
- Develop and test Role-Based Access Control (RBAC) and secure endpoint communication for real-world deployment

---

### Epics and User Stories

#### Epic 1: Security Configuration and Access Policies

**User Story 1.1**

> As a developer, I want to configure Spring Security filters so that I can protect all endpoints and define which resources require authentication.

**Acceptance Criteria:**
- `SecurityFilterChain` configured with custom access rules
- Public endpoints (login, registration) and restricted endpoints (admin, author, reader) defined
- Passwords securely stored using `BCryptPasswordEncoder`

**User Story 1.2**

> As a frontend developer, I want to enable secure cross-origin requests so that external clients (e.g., React, JavaFX) can interact safely with the backend.

**Acceptance Criteria:**
- Global CORS configuration allows specific origins, methods, and headers
- Tested with both Postman and a web frontend
- Unauthorized origins correctly blocked with appropriate response codes

---

#### Epic 2: JWT-Based Authentication

**User Story 2.1**

> As a user, I want to log in with valid credentials and receive a JWT token so that I can securely access protected endpoints.

**Acceptance Criteria:**
- `/auth/login` endpoint generates signed JWTs with claims (username, roles, expiry)
- Tokens validated for each protected request
- Expired or tampered tokens rejected with `401 Unauthorized`

**User Story 2.2**

> As a system analyst, I want to verify token structure and claims so that I can validate authentication mechanisms.

**Acceptance Criteria:**
- JWT includes subject, issue time, and expiration claims
- Signed using HMAC SHA-256 or RSA algorithms
- Token payload can be decoded and verified in Postman

---

#### Epic 3: CSRF and Session Security

**User Story 3.1**

> As a security engineer, I want to configure CSRF protection correctly so that the platform is protected from cross-site request forgery attacks.

**Acceptance Criteria:**
- CSRF disabled for stateless JWT APIs
- Explanation provided for enabling CSRF in stateful sessions or form submissions
- Demonstration of CSRF token mechanism for a sample form-based endpoint

**User Story 3.2**

> As a developer, I want to understand and document CORS and CSRF differences so that I can configure them correctly for browser and API clients.

**Acceptance Criteria:**
- Technical documentation explaining CORS vs. CSRF interactions included in README
- Practical tests performed using Postman and browser-based clients

---

#### Epic 4: OAuth2 and Role-Based Access Control (RBAC)

**User Story 4.1**

> As a user, I want to log in with my Google account so that I can access the blogging platform without manual registration.

**Acceptance Criteria:**
- Google OAuth2 login integrated using Spring Security OAuth2 Client
- User details fetched from Google API and persisted in the database
- Roles automatically assigned post-authentication

**User Story 4.2**

> As an administrator, I want to restrict access to certain endpoints based on user roles so that I can enforce role-based permissions.

**Acceptance Criteria:**
- Roles defined: `ADMIN`, `AUTHOR`, `READER`
- Endpoints secured using `@PreAuthorize` or `@Secured` annotations
- Role-based access verified through Postman tests

---

#### Epic 5: DSA and Security Optimization

**User Story 5.1**

> As a developer, I want to apply DSA principles to improve security and authentication efficiency.

**Acceptance Criteria:**
- Hashing used for password storage and token verification
- Caching or lookup map implemented for temporary token blacklisting
- In-memory hash map used for revoked tokens or active session tracking

**User Story 5.2**

> As an auditor, I want to monitor and analyze login attempts and access patterns so that I can identify suspicious activities.

**Acceptance Criteria:**
- Logging configured for authentication success/failure events
- Security event reports show token usage and access frequency
- Logs analyzed to detect brute-force or unauthorized access attempts

---

### Technical Requirements

| Area | Description |
|---|---|
| Framework | Spring Boot 3.x (Spring Security, JWT, OAuth2 Client, Validation, Cache) |
| Language | Java 21 |
| Authentication | Username/password with JWT and Google OAuth2 login |
| Authorization | Role-Based Access Control (`ADMIN`, `AUTHOR`, `READER`) |
| Security Features | CORS setup, CSRF demonstration, password hashing with BCrypt |
| Password Encryption | Implemented with `BCryptPasswordEncoder` |
| Database | Extended Week 6 schema with `User` and `Role` entities |
| Testing & Interaction | Tested via Postman, web frontend (React/JavaFX), or GraphQL playground |
| Documentation | OpenAPI documentation including secured and public endpoints |
| DSA Integration | Hashing, token validation, map-based blacklisting, and secure lookup data structures |

---

### Deliverables

| Deliverable | Description |
|---|---|
| Spring Security Integration | Application configured with custom authentication and authorization filters |
| JWT Authentication System | Functional login, token issuance, and validation endpoints |
| CORS & CSRF Configuration | Documented and tested setup for safe client communication |
| OAuth2 (Google Login) | Google login configured with persistent user profiles and mapped roles |
| RBAC Enforcement | Role-based endpoint security implemented and verified |
| Security Event Logging | Logs capturing authentication events and access details |
| DSA Implementation | Applied hashing, token lookup, and caching for secure authentication flow |
| README & OpenAPI Docs | Comprehensive documentation covering setup, configuration, and testing |

---

### Evaluation Criteria

| Category | Description | Points |
|---|---|---|
| Security Configuration (CORS & CSRF) | Correct setup and explanation of CORS, CSRF, and related policies | 15 |
| JWT Implementation | Secure JWT authentication with signed token generation and validation | 20 |
| OAuth2 (Google Integration) | External login configured with user persistence and mapped roles | 15 |
| RBAC and Role Enforcement | Role-based access restrictions correctly applied and tested | 15 |
| DSA in Security | Proper application of hashing, lookup, and caching for secure logic | 15 |
| Testing & Logging | Postman tests, logs, and access monitoring implemented successfully | 10 |
| Code Quality & Documentation | Organized configuration, comments, and complete API documentation | 10 |
| **Total** | | **100 pts** |

---
---

## Module 7.2: Hospital/Healthcare Management System

**Complexity:** Advanced
**Time Estimate:** 10–12 hours

---

### Project Overview

This phase emphasizes building secure, scalable, and production-ready web backends that can safely handle authentication, authorization, and cross-origin requests. Learners will apply Spring Security concepts to secure their application's REST and GraphQL APIs using JWT-based authentication, OAuth2 login (Google), and Role-Based Access Control (RBAC). They will also explore security-related DSA concepts such as hashing, encryption, and secure token validation.

---

### Project Objectives

By the end of this project, learners will be able to:

- Apply Spring Security configurations to enforce authentication, authorization, and access control across REST and GraphQL APIs
- Implement JWT authentication, Google OAuth2 login, and secure password hashing using BCrypt
- Configure and analyze CORS and CSRF policies for different client interactions (Postman, browsers, and JavaFX)
- Apply DSA concepts (hashing, encryption, and token validation) to strengthen data security and session integrity
- Develop and test role-based access control (RBAC) and secure endpoint communication for real-world deployment

---

### Epics and User Stories

#### Epic 1: Security Configuration and Access Policies

**User Story 1.1**

> As a developer, I want to configure Spring Security filters so that I can protect all endpoints and define which resources require authentication.

**Acceptance Criteria:**
- `SecurityFilterChain` configured with custom access rules
- Public (login, registration) and restricted (admin, doctor, nurse, receptionist) endpoints defined
- Passwords stored using `BCryptPasswordEncoder`

**User Story 1.2**

> As a frontend developer, I want to enable secure cross-origin requests so that external clients can interact with the backend.

**Acceptance Criteria:**
- Global CORS configuration implemented to allow specific origins, methods, and headers
- Configuration tested with both Postman and a web frontend
- Unauthorized origins correctly rejected

---

#### Epic 2: JWT-Based Authentication

**User Story 2.1**

> As a user, I want to log in with valid credentials and receive a JWT token so that I can access restricted endpoints securely.

**Acceptance Criteria:**
- `/auth/login` endpoint generates signed JWTs with claims (username, roles, expiry)
- Tokens validated on each protected request
- Tampered or expired tokens rejected with `401 Unauthorized`

**User Story 2.2**

> As a system analyst, I want to verify token structure and claims so that I can validate security implementation.

**Acceptance Criteria:**
- JWT includes subject, issued time, and expiration claims
- HMAC SHA-256 or RSA algorithm used for signature verification
- Token payload can be viewed in Postman (decoded) for verification

---

#### Epic 3: CSRF and Session Security

**User Story 3.1**

> As a security engineer, I want to configure CSRF protection properly so that the system is secure against cross-site request forgery.

**Acceptance Criteria:**
- CSRF protection disabled for stateless JWT APIs
- Explanation provided for when CSRF should be enabled (stateful sessions, forms)
- CSRF token mechanism demonstrated in one form endpoint for illustration

**User Story 3.2**

> As a developer, I want to understand and document CSRF and CORS differences so that I can configure them correctly for frontend and backend communication.

**Acceptance Criteria:**
- Technical documentation describing CORS and CSRF interaction included in README
- Practical demonstration using Postman and browser client

---

#### Epic 4: OAuth2 and Role-Based Access Control (RBAC)

**User Story 4.1**

> As a user, I want to log in with my Google account so that I can access the system without manual signup.

**Acceptance Criteria:**
- OAuth2 login integrated using Google provider
- User details fetched from Google API and persisted
- Roles assigned after successful OAuth2 authentication

**User Story 4.2**

> As an administrator, I want to restrict access to certain endpoints based on user roles so that I can enforce role-based permissions.

**Acceptance Criteria:**
- Roles defined: `ADMIN`, `DOCTOR`, `NURSE`, `RECEPTIONIST`
- Endpoints annotated with `@PreAuthorize` or `@Secured`
- Role-based access verified using Postman test cases

---

#### Epic 5: DSA and Security Optimization

**User Story 5.1**

> As a developer, I want to apply data structure and algorithm principles to improve security and performance.

**Acceptance Criteria:**
- Hashing used for password security and token validation
- Caching or lookup map implemented for temporary token storage or blacklisting
- Optional use of in-memory map (hash map) for revoked tokens

**User Story 5.2**

> As an auditor, I want to view and analyze security event logs so that I can track login attempts and access patterns.

**Acceptance Criteria:**
- Logging implemented for authentication success/failure events
- Security reports include token usage and endpoint access frequency
- Logs reviewed to detect unusual access or brute-force attempts

---

### Technical Requirements

| Area | Description |
|---|---|
| Framework | Spring Boot 3.x (Spring Security, JWT, OAuth2 Client, Validation, Cache) |
| Language | Java 21 |
| Authentication | Username/password with JWT, OAuth2 login (Google) |
| Authorization | Role-Based Access Control (RBAC) |
| Security Features | CORS setup, CSRF demonstration, password hashing |
| Password Encryption | `BCryptPasswordEncoder` |
| Database | Existing database extended with user and role entities |
| Testing & Interaction | Postman or any web frontend for login and authorization testing |
| Documentation | OpenAPI documentation covering secured and public endpoints |
| DSA Integration | Hashing, token validation, map-based blacklisting, and secure lookup design |

---

### Deliverables

| Deliverable | Description |
|---|---|
| Spring Security Integration | Application configured with authentication and authorization filters |
| JWT Authentication System | Fully functional login, token generation, and validation endpoints |
| CORS & CSRF Configuration | Working setup with documentation and demonstrations for safe client access |
| OAuth2 (Google Login) | Social login configured with user persistence and mapped roles |
| RBAC Enforcement | Role-based access control implemented on key endpoints |
| Security Event Logging | Logs capturing authentication and access details |
| DSA Implementation | Applied hashing, caching, and lookup optimization within security flow |
| README & OpenAPI Docs | Comprehensive documentation covering setup, testing, and configuration notes |

---

### Evaluation Criteria

| Category | Description | Points |
|---|---|---|
| Security Configuration (CORS & CSRF) | Correct configuration and explanation of CORS, CSRF, and their use cases | 15 |
| JWT Implementation | Functional JWT authentication with secure token generation and validation | 20 |
| OAuth2 (Google Integration) | External login configured with consistent user mapping and persistence | 15 |
| RBAC and Role Enforcement | Role-based restrictions implemented accurately across endpoints | 15 |
| DSA in Security | Application of hashing, lookup, or caching for security logic | 15 |
| Testing & Logging | Postman tests, security event logs, and error tracking implemented | 10 |
| Code Quality & Documentation | Organized configuration, clear comments, and complete API documentation | 10 |
| **Total** | | **100 pts** |

---
---

## Module 7.3: Smart E-Commerce System

**Complexity:** Advanced
**Time Estimate:** 10–12 hours

---

### Project Overview

This phase emphasizes building secure, scalable, and production-ready web backends that can safely handle authentication, authorization, and cross-origin requests. Learners will apply Spring Security concepts to secure their application's REST and GraphQL APIs using JWT-based authentication, OAuth2 login (Google), and Role-Based Access Control (RBAC). They will also explore security-related DSA concepts such as hashing, encryption, and secure token validation.

---

### Project Objectives

By the end of this project, learners will be able to:

- Apply Spring Security configurations to enforce authentication, authorization, and access control across REST and GraphQL APIs
- Implement JWT authentication, Google OAuth2 login, and secure password hashing using BCrypt
- Configure and analyze CORS and CSRF policies for different client interactions (Postman, browsers, and JavaFX)
- Apply DSA concepts (hashing, encryption, and token validation) to strengthen data security and session integrity
- Develop and test role-based access control (RBAC) and secure endpoint communication for real-world deployment

---

### Epics and User Stories

#### Epic 1: Security Configuration and Access Policies

**User Story 1.1**

> As a developer, I want to configure Spring Security filters so that I can protect all endpoints and define which resources require authentication.

**Acceptance Criteria:**
- `SecurityFilterChain` configured with custom access rules
- Public (login, registration) and restricted (admin, customer) endpoints defined
- Passwords stored using `BCryptPasswordEncoder`

**User Story 1.2**

> As a frontend developer, I want to enable secure cross-origin requests so that external clients can interact with the backend.

**Acceptance Criteria:**
- Global CORS configuration implemented to allow specific origins, methods, and headers
- Configuration tested with both Postman and a web frontend
- Unauthorized origins correctly rejected

---

#### Epic 2: JWT-Based Authentication

**User Story 2.1**

> As a user, I want to log in with valid credentials and receive a JWT token so that I can access restricted endpoints securely.

**Acceptance Criteria:**
- `/auth/login` endpoint generates signed JWTs with claims (username, roles, expiry)
- Tokens validated on each protected request
- Tampered or expired tokens rejected with `401 Unauthorized`

**User Story 2.2**

> As a system analyst, I want to verify token structure and claims so that I can validate security implementation.

**Acceptance Criteria:**
- JWT includes subject, issued time, and expiration claims
- HMAC SHA-256 or RSA algorithm used for signature verification
- Token payload can be viewed in Postman (decoded) for verification

---

#### Epic 3: CSRF and Session Security

**User Story 3.1**

> As a security engineer, I want to configure CSRF protection properly so that the system is secure against cross-site request forgery.

**Acceptance Criteria:**
- CSRF protection disabled for stateless JWT APIs
- Explanation provided for when CSRF should be enabled (stateful sessions, forms)
- CSRF token mechanism demonstrated in one form endpoint for illustration

**User Story 3.2**

> As a developer, I want to understand and document CSRF and CORS differences so that I can configure them correctly for frontend and backend communication.

**Acceptance Criteria:**
- Technical documentation describing CORS and CSRF interaction included in README
- Practical demonstration using Postman and browser client

---

#### Epic 4: OAuth2 and Role-Based Access Control (RBAC)

**User Story 4.1**

> As a user, I want to log in with my Google account so that I can access the system without manual signup.

**Acceptance Criteria:**
- OAuth2 login integrated using Google provider
- User details fetched from Google API and persisted
- Roles assigned after successful OAuth2 authentication

**User Story 4.2**

> As an administrator, I want to restrict access to certain endpoints based on user roles so that I can enforce role-based permissions.

**Acceptance Criteria:**
- Roles defined: `ADMIN`, `CUSTOMER`, `STAFF`
- Endpoints annotated with `@PreAuthorize` or `@Secured`
- Role-based access verified using Postman test cases

---

#### Epic 5: DSA and Security Optimization

**User Story 5.1**

> As a developer, I want to apply data structure and algorithm principles to improve security and performance.

**Acceptance Criteria:**
- Hashing used for password security and token validation
- Caching or lookup map implemented for temporary token storage or blacklisting
- Optional use of in-memory map (hash map) for revoked tokens

**User Story 5.2**

> As an auditor, I want to view and analyze security event logs so that I can track login attempts and access patterns.

**Acceptance Criteria:**
- Logging implemented for authentication success/failure events
- Security reports include token usage and endpoint access frequency
- Logs reviewed to detect unusual access or brute-force attempts

---

### Technical Requirements

| Area | Description |
|---|---|
| Framework | Spring Boot 3.x (Spring Security, JWT, OAuth2 Client, Validation, Cache) |
| Language | Java 21 |
| Authentication | Username/password with JWT, OAuth2 login (Google) |
| Authorization | Role-Based Access Control (RBAC) |
| Security Features | CORS setup, CSRF demonstration, password hashing |
| Password Encryption | `BCryptPasswordEncoder` |
| Database | Existing database extended with user and role entities |
| Testing & Interaction | Postman or any web frontend for login and authorization testing |
| Documentation | OpenAPI documentation covering secured and public endpoints |
| DSA Integration | Hashing, token validation, map-based blacklisting, and secure lookup design |

---

### Deliverables

| Deliverable | Description |
|---|---|
| Spring Security Integration | Application configured with authentication and authorization filters |
| JWT Authentication System | Fully functional login, token generation, and validation endpoints |
| CORS & CSRF Configuration | Working setup with documentation and demonstrations for safe client access |
| OAuth2 (Google Login) | Social login configured with user persistence and mapped roles |
| RBAC Enforcement | Role-based access control implemented on key endpoints |
| Security Event Logging | Logs capturing authentication and access details |
| DSA Implementation | Applied hashing, caching, and lookup optimization within security flow |
| README & OpenAPI Docs | Comprehensive documentation covering setup, testing, and configuration notes |

---

### Evaluation Criteria

| Category | Description | Points |
|---|---|---|
| Security Configuration (CORS & CSRF) | Correct configuration and explanation of CORS, CSRF, and their use cases | 15 |
| JWT Implementation | Functional JWT authentication with secure token generation and validation | 20 |
| OAuth2 (Google Integration) | External login configured with consistent user mapping and persistence | 15 |
| RBAC and Role Enforcement | Role-based restrictions implemented accurately across endpoints | 15 |
| DSA in Security | Application of hashing, lookup, or caching for security logic | 15 |
| Testing & Logging | Postman tests, security event logs, and error tracking implemented | 10 |
| Code Quality & Documentation | Organized configuration, clear comments, and complete API documentation | 10 |
| **Total** | | **100 pts** |
