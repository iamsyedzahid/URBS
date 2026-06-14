# Jira Workflow and Process Guide

This guide outlines the standard operating procedure for managing the University Room Booking System (URBS) project using Jira. It is designed to help team members track progress, manage tasks, and maintain clear communication throughout the project lifecycle.

## 1. Introduction to Jira Concepts

* **Project:** The overarching workspace (e.g., URBS Development).
* **Issue:** A single unit of work (e.g., a task, a bug, or a user story).
* **Epic:** A large body of work that can be broken down into smaller tasks or user stories (e.g., "Implement Booking Engine").
* **Sprint:** A time-boxed period (e.g., 2 weeks) during which a set amount of work is completed.
* **Board:** The visual representation of the workflow (To Do, In Progress, Done).

## 2. Issue Types Used in URBS

* **Story:** A feature or requirement from the user's perspective (e.g., "As a student, I want to view room availability so I can plan a study session").
* **Task:** Technical work that doesn't directly map to a user story (e.g., "Set up SQLite database").
* **Sub-task:** Smaller pieces of work required to complete a Story or Task.
* **Bug:** A defect or error in the system that needs to be fixed.

## 3. The Standard Workflow

Every issue in Jira follows a specific lifecycle:

1. **To Do / Backlog:** The issue is created and prioritized but work has not yet started.
2. **In Progress:** A team member assigns the issue to themselves and begins working on it.
3. **In Review / Testing:** The code is written and a Pull Request is open, or it is being tested by another team member.
4. **Done:** The issue meets the "Definition of Done" (code merged, tests passed, feature working).

## 4. Sprint Planning Process

1. **Review the Backlog:** The team reviews the list of all pending issues.
2. **Select Issues:** Issues are moved from the Backlog into the upcoming Sprint based on priority and team capacity.
3. **Estimation:** Tasks are estimated (e.g., using story points or hours) to ensure the Sprint is realistic.
4. **Start Sprint:** The Sprint is officially started in Jira.

## 5. Daily Usage Guidelines

* **Assign Yourself:** Before starting work, assign the Jira ticket to yourself.
* **Update Status:** Move the ticket to "In Progress" when you start, and update it as it moves through the workflow.
* **Add Comments:** Use the comment section on the issue to document decisions, ask questions, or link to relevant Pull Requests or documentation.
* **Link Commits:** When committing code to Git, include the Jira Issue Key (e.g., URBS-12) in the commit message to automatically link the code to the issue.

## 6. Definition of Done (DoD)

Before moving a ticket to "Done," ensure the following criteria are met:

* Code is committed and merged via a Pull Request.
* Unit/Integration tests are written and passing.
* Relevant documentation is updated.
* The feature functions correctly in the development/staging environment.
