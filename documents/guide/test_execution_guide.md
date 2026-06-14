# Test Execution Guide

This guide outlines the standard procedures for executing test cases within the University Room Booking System (URBS) project environment. It ensures consistency and accuracy during the testing phase.

## 1. Prerequisites for Execution

Before beginning test execution, ensure the following conditions are met:
*   **Environment Readiness:** The application (frontend and backend) is deployed and running in the designated test environment.
*   **Database State:** The test database is seeded with necessary baseline data (e.g., rooms are populated, default admin exists).
*   **Test Cases:** The test suite is approved and accessible (e.g., in a test management tool or spreadsheet).
*   **Tools Required:** Access to a web browser (Chrome/Firefox), API testing tool (Postman), and database client if backend verification is needed.

## 2. Test Execution Workflow

### Step 1: Environment Setup
1. Start the Flask backend server (`python app.py`).
2. Start the React frontend development server (`npm start`).
3. Verify the system is reachable by navigating to `http://localhost:3000` (or the configured port).

### Step 2: Running Automated Tests
1. **Backend Tests:** Navigate to the backend directory and run `pytest tests/`. Ensure all tests pass.
2. **Review Logs:** If any automated tests fail, review the console output to identify the breaking point.

### Step 3: Manual Test Execution
For features requiring manual validation (e.g., UI interactions):
1. Select a test case from the test plan.
2. Read the Pre-conditions and ensure the system state matches.
3. Follow the **Test Steps** exactly as written. Do not deviate or improvise during a formal execution run.
4. Observe the system's behavior.

### Step 4: Recording Results
1. **Pass:** If the Actual Result matches the Expected Result exactly, mark the test as PASS.
2. **Fail:** If the Actual Result deviates from the Expected Result, mark the test as FAIL. Take a screenshot or record a video of the unexpected behavior.
3. **Blocked:** If a test cannot be executed because a previous step or related feature is broken, mark it as BLOCKED.

## 5. Post-Execution Actions

*   **Log Defects:** For every failed test case, immediately log a bug report in Jira (see the Bug Reporting Workflow guide). Link the bug ticket to the failed test case.
*   **Reset Environment:** If a test modifies data (e.g., creates a booking), ensure the environment is reset or that subsequent tests do not rely on the altered data state.
*   **Test Summary Report:** At the end of the test cycle, compile a brief summary detailing the number of tests run, passed, failed, and any critical blockers.
