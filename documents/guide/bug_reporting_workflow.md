# Bug Reporting Workflow

This document standardizes how bugs and defects should be reported, triaged, and resolved within the University Room Booking System (URBS) project. A well-written bug report is crucial for developers to quickly understand and fix the issue.

## 1. What Makes a Good Bug Report?

A good bug report is clear, concise, and reproducible. It provides the developer with all the necessary context to recreate the error on their own machine.

## 2. Standard Bug Report Structure

When logging a bug in Jira (or your issue tracker), use the following format:

*   **Title:** A concise summary of the issue. (Format: [Component] - Brief Description).
    *   *Example: [Booking] System allows overlapping bookings for the same room.*
*   **Environment:** Where did the bug occur?
    *   *OS:* Windows 11 / macOS / Linux
    *   *Browser:* Chrome v115 / Firefox v113
    *   *App Version:* v1.0-alpha
*   **Pre-conditions:** Any setup required before the bug can be triggered.
*   **Steps to Reproduce:** A numbered list of exact actions to trigger the bug.
    1. Log in as Student.
    2. Go to 'Room Search' and select Room 101.
    3. Enter start time '10:00' and end time '11:00'.
    4. Click 'Submit'.
*   **Expected Result:** What *should* have happened.
    *   *System should display a conflict error message.*
*   **Actual Result:** What *actually* happened.
    *   *System accepted the booking and displayed a success message.*
*   **Severity/Priority:** (See section 3 below).
*   **Attachments:** Screenshots, screen recordings, or backend console error logs. **(Crucial)**

## 3. Severity and Priority Definitions

**Severity** (Impact on the system):
*   **Critical:** System crash, data loss, or core functionality completely broken (e.g., Cannot log in).
*   **Major:** Important feature is broken, but a workaround exists (e.g., Cannot filter rooms by capacity).
*   **Minor:** UI glitch, typo, or minor functional issue that doesn't halt workflow.

**Priority** (How soon it needs to be fixed):
*   **High:** Must be fixed immediately. Blocks further development or testing.
*   **Medium:** Should be fixed in the current sprint.
*   **Low:** Can be deferred to a later sprint.

## 4. The Bug Lifecycle

1.  **New:** Bug is logged by QA or a team member.
2.  **Triaged:** The project lead reviews the bug, confirms it is valid, and assigns Priority.
3.  **In Progress:** A developer is actively working on a fix.
4.  **Ready for Test:** The developer has committed a fix and deployed it to the test environment.
5.  **Testing:** QA attempts to reproduce the bug using the original steps.
    *   If fixed: Move to **Done/Closed**.
    *   If not fixed: Move back to **In Progress** with a comment explaining what failed.
