# QA & Testing Process Documentation

This document provides a high-level overview of the Quality Assurance (QA) philosophy and the overall testing process for the University Room Booking System (URBS). It defines how the team ensures the software meets its specified requirements and quality standards.

## 1. QA Objectives

The primary objectives of the QA process in the URBS project are:
*   To identify and resolve defects early in the development lifecycle.
*   To ensure the application meets all documented Functional and Non-Functional Requirements (FRs and NFRs).
*   To validate that the system is secure, stable, and user-friendly.
*   To prevent regressions when new features are added.

## 2. Testing Phases

The testing process is integrated into the Agile sprints and consists of several phases:

### A. Unit Testing (Developer Level)
*   **Scope:** Testing individual functions, methods, or components in isolation.
*   **Responsibility:** Software Developers (Backend and Frontend).
*   **Tools:** `pytest` for Flask backend; Jest/React Testing Library for Frontend.
*   **Goal:** Ensure foundational code logic is correct before integration.

### B. Integration Testing
*   **Scope:** Testing the interaction between different modules (e.g., Frontend API calls interacting with Backend endpoints and the Database).
*   **Responsibility:** Developers and QA.
*   **Goal:** Verify data flows correctly across architectural boundaries.

### C. System Testing
*   **Scope:** End-to-end testing of the fully assembled application.
*   **Responsibility:** QA / Testing Team.
*   **Goal:** Validate complete workflows (e.g., Registration -> Search -> Booking -> Admin Approval -> Notification).

### D. User Acceptance Testing (UAT)
*   **Scope:** Testing conducted by intended end-users (Students, Faculty, Admins).
*   **Responsibility:** Selected end-users guided by the project team.
*   **Goal:** Confirm the system meets business needs and is intuitive for everyday use.

## 3. Continuous Integration / Continuous Testing

*   All code submitted via Pull Requests (PRs) must pass automated unit and integration tests before being merged into the main branch.
*   If a test fails, the PR is blocked until the code is rectified.

## 4. Defect Management Strategy

*   No defect is considered resolved until it has been independently verified by a team member other than the developer who fixed it.
*   Regression testing must be performed around the area of a bug fix to ensure the fix did not inadvertently break existing functionality.

## 5. QA Deliverables

Throughout the project lifecycle, the QA process produces the following artifacts:
*   **Test Plan:** Strategy and scope of testing for a specific milestone.
*   **Test Cases:** Detailed steps for validation.
*   **Defect Reports:** Logged bugs in Jira.
*   **Test Summary Report:** A final document outlining the quality status of the release, including known issues and overall stability metrics.
