# Test Case Writing Guide

This document provides a standard framework for writing clear, comprehensive, and effective test cases for the University Room Booking System (URBS).

## 1. What is a Test Case?

A test case is a set of conditions or variables under which a tester will determine whether a system under test satisfies requirements or works correctly.

## 2. Standard Test Case Format

Every test case should include the following fields:

*   **Test Case ID:** A unique identifier (e.g., TC-AUTH-01).
*   **Title/Description:** A brief summary of what the test case validates (e.g., "Verify student login with valid credentials").
*   **Pre-conditions:** The state the system must be in before the test can begin (e.g., "User account must exist in the database").
*   **Test Steps:** Clear, numbered actions the tester must perform.
*   **Expected Result:** The exact behavior the system should exhibit if the test passes.
*   **Actual Result:** (Filled out during execution) What actually happened.
*   **Status:** Pass, Fail, or Blocked.

## 3. Best Practices for Writing Test Cases

*   **Keep it Simple and Clear:** Write steps that are easy to understand and follow. Avoid ambiguity.
*   **Test One Thing at a Time:** A single test case should focus on a specific functionality or rule.
*   **Include Edge Cases:** Don't just test the "happy path" (normal use). Test boundaries, invalid inputs, and unexpected user behavior.
*   **Use Realistic Data:** Specify the test data to be used (e.g., "Email: student@urbs.edu, Password: Password123").
*   **Independent:** Ensure test cases can be run independently of one another whenever possible.

## 4. Examples for URBS

### Example 1: Happy Path (Functional)

**Test Case ID:** TC-BOOK-01
**Title:** Verify a student can submit a valid booking request.
**Pre-conditions:**
1. User is logged in as a Student.
2. Room 101 is available on 2026-10-15 from 10:00 to 11:00.
**Test Steps:**
1. Navigate to the "Room Search" page.
2. Select Date: "2026-10-15".
3. Click "Book" on Room 101.
4. Fill Start Time: "10:00", End Time: "11:00", Purpose: "Group Study".
5. Click "Submit Request".
**Expected Result:**
System displays "Booking request submitted successfully" and the booking appears in the user's "My Bookings" list with a "Pending" status.

### Example 2: Negative Testing (Validation)

**Test Case ID:** TC-AUTH-04
**Title:** Verify registration fails with an invalid email format.
**Pre-conditions:** System is running and accessible.
**Test Steps:**
1. Navigate to the Registration page.
2. Enter Name: "John Doe".
3. Enter Email: "johndoe_at_urbs.edu" (missing @ symbol).
4. Enter Password: "Password123".
5. Select Role: "Student".
6. Click "Register".
**Expected Result:**
System prevents registration and displays the error message: "A valid email address is required."
