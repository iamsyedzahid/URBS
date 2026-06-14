
UNIVERSITY ROOM
BOOKING SYSTEM
Comprehensive Project Details Document
Project Title	University Room Booking System (URBS)
Document Type	Project Details — End Users, Requirements, Components, Tasks
Team Members	Abdullah Sonija (24K-0013)  |  Zahid Hussain (24K-0015)
Methodology	Agile / Scrum  —  5 Sprints
Technology Stack	React.js  |  Python Flask  |  SQLite / MySQL
Version	v2.0  (5-Sprint Revised Plan)

 
Section 1: End Users
This section identifies the primary and secondary target audiences of URBS — the individuals and system actors who interact with, depend on, or are directly impacted by the application.
1.1  Primary End Users
Primary end users are human actors who interact directly with the system through the web interface. Three distinct user roles are supported, each with scoped permissions enforced via role-based access control (RBAC) and JWT middleware.
1.1.1  Student
Students represent the largest user cohort and the most frequent consumers of the booking system.
Attribute	Details
Classification	Primary End User
Access Level	Restricted — booking submission, history, cancellation
Key Interactions	Register/Login, Browse Rooms, Submit Booking Request, View Booking History, Cancel Booking
Constraints	Cannot approve requests; subject to conflict check; no priority override
Primary Goal	Reserve university rooms for study groups, collaborative projects, and academic sessions

1.1.2  Faculty
Faculty members share all student privileges with the addition of a priority room access extension, allowing them to supersede standard booking queues for academic obligations.
Attribute	Details
Classification	Primary End User (Elevated Privileges)
Access Level	Standard + Priority Access Extension
Key Interactions	All student actions + Priority Room Access flag on booking requests
Constraints	Still subject to admin approval; conflict check applies
Primary Goal	Reserve rooms for lectures, research meetings, departmental sessions, and office hours

1.1.3  Administrator
Administrators are privileged system managers responsible for the operational integrity of the booking platform. They possess full read and write access across all entities.
Attribute	Details
Classification	Primary End User (System Manager)
Access Level	Full — room CRUD, approval workflow, utilization dashboard
Key Interactions	Login, Manage Room Inventory, Review/Approve/Reject Requests, Monitor Utilization
Constraints	Must provide remarks on rejection; actions are audit-logged
Primary Goal	Maintain room schedule integrity, process requests efficiently, track utilization metrics

1.2  Secondary / Automated Actor
The System actor is an automated software component, not a human user. It performs background operations triggered by user actions.
System Process	Trigger	Action Performed
Conflict Checker	Booking / Cancellation submitted	Validates time-slot availability; blocks double-booking
Slot Lock Manager	Conflict check passes	Temporarily locks time slot pending admin decision
Notification Engine	Admin approves or rejects	Dispatches status notification to the requesting user
Reservation Ledger	Approval confirmed	Finalizes and persists the reservation record in the database

1.3  Indirect Stakeholders
The following stakeholders are not system users but have an interest in the system outcomes:
•	Course Instructor — Evaluates project artifacts, documentation quality, and functional demonstration
•	University Administration — Prospective institutional adopters who benefit from operational efficiency gains
•	IT Department — Responsible for server infrastructure and deployment environment

 
Section 2: Requirements
This section enumerates the complete functional and non-functional requirements of URBS, derived from the project objectives, stakeholder needs, and the use case specification.
2.1  Functional Requirements
Functional requirements define the specific behaviors, capabilities, and operations the system must support.
2.1.1  User Authentication & Access Control
ID	Requirement	Actor(s)
FR-01	System shall allow users to register with full name, university email, password, and role selection	Student, Faculty, Admin
FR-02	System shall authenticate users via email and password, returning a JWT token on success	All Users
FR-03	System shall enforce role-based access control, restricting each endpoint to authorised roles only	System
FR-04	System shall invalidate sessions on logout or token expiry	All Users

2.1.2  Room Search & Availability
ID	Requirement	Actor(s)
FR-05	System shall allow users to search rooms filtered by date, time slot, room type, and minimum capacity	Student, Faculty
FR-06	System shall display real-time availability status (Available / Booked) for each room in search results	Student, Faculty
FR-07	System shall present room details including room number, type, capacity, and active status	Student, Faculty

2.1.3  Booking Request Workflow
ID	Requirement	Actor(s)
FR-08	System shall allow eligible users to submit a booking request specifying room, date, start time, end time, and purpose	Student, Faculty
FR-09	System shall automatically detect and block conflicting reservations at submission time	System
FR-10	Faculty role shall trigger priority access extension, flagging the request for elevated review	Faculty, System
FR-11	System shall set initial booking status to Pending and lock the time slot upon successful submission	System

2.1.4  Admin Approval Workflow
ID	Requirement	Actor(s)
FR-12	Admin shall view all pending booking requests in a dedicated approval queue dashboard	Admin
FR-13	Admin shall be able to approve a pending request, transitioning status to Approved and finalising the reservation record	Admin, System
FR-14	Admin shall be able to reject a pending request with mandatory remarks; system releases the locked time slot	Admin, System
FR-15	System shall dispatch a status notification to the requesting user upon any approval/rejection decision	System

2.1.5  Booking History & Cancellation
ID	Requirement	Actor(s)
FR-16	System shall provide users with a full chronological history of their submitted bookings and statuses	Student, Faculty
FR-17	Users shall be able to cancel an approved or pending booking, triggering a conflict re-check and slot release	Student, Faculty, System
FR-18	Admin shall have view access to the booking history of all users	Admin

2.1.6  Room Inventory Management
ID	Requirement	Actor(s)
FR-19	Admin shall be able to add new rooms with attributes: room number, type, capacity, and active status	Admin
FR-20	Admin shall be able to edit existing room attributes	Admin
FR-21	Admin shall be able to soft-delete (deactivate) rooms without purging historical booking records	Admin
FR-22	Admin shall access a room utilization dashboard displaying occupancy rates and booking frequency	Admin

2.2  Non-Functional Requirements
ID	Category	Requirement	Acceptance Criterion
NFR-01	Security	All protected API endpoints must validate JWT token and role before processing	Unauthenticated requests return HTTP 401
NFR-02	Data Integrity	Database must enforce UNIQUE constraint on (room_id, date, start_time) to prevent race-condition double-bookings	Duplicate inserts return DB constraint error
NFR-03	Validation	All form inputs must be validated at both frontend (React) and backend (Flask) layers	Invalid inputs return descriptive error messages
NFR-04	Usability	UI must be fully responsive and accessible on desktop and mobile browsers	Renders correctly on screen widths >= 375px
NFR-05	Maintainability	Codebase must follow modular architecture with clear separation of frontend, backend, and database layers	New features can be added without cross-layer side effects
NFR-06	Reliability	System must handle concurrent booking submissions without data corruption	Stress test with 10 concurrent submissions passes without duplicate records
NFR-07	Traceability	All booking state transitions must be persisted with timestamps for auditing	Booking history reflects all status changes with creation timestamps

 
Section 3: Components
This section provides a comprehensive breakdown of the system architecture, including functional modules, UI screens, the data model, and the full technology stack.
3.1  Architectural Module Breakdown
URBS is structured as a decoupled three-tier web application with five core functional modules:
Module	Responsibilities	Components Involved
User Management	Registration, login, JWT token issuance, session management, role resolution	React AuthContext, Flask /auth endpoints, User model, JWT middleware
Room Management	Room CRUD operations, availability status computation, inventory listing	Admin Panel UI, Flask /rooms endpoints, Room model, SQLAlchemy
Booking Engine	Booking submission, conflict detection, time-slot locking, cancellation processing	Booking Form UI, Flask /bookings endpoints, Booking model, constraint validation
Approval Workflow	Admin review queue, status state machine (Pending > Approved / Rejected), remarks management	Admin Panel UI, Flask /admin/bookings endpoints, status enum, booking record update
Notification Layer	Post-decision status notifications to users; cancellation confirmations	System-triggered, in-app status banner / notification model (optional email)

3.2  UI Screen Inventory
The following screens constitute the complete user interface surface of URBS:
Screen	Access Role	Key UI Elements
Login / Register	All	Email/password fields, role selector, validation messages, submit CTA
Student/Faculty Dashboard	Student, Faculty	Booking status summary cards, quick search shortcut, upcoming reservations list
Room Search	Student, Faculty	Date/time/type/capacity filter bar, room cards with availability badge, Book Now CTA
Booking Form	Student, Faculty	Pre-filled room info, date picker, time range selector, purpose textarea, conflict warning
Booking History	Student, Faculty	Sortable table of past/active bookings, status badge (Pending/Approved/Rejected), Cancel button
Admin Dashboard	Admin	Utilization KPI cards, pending request counter, recent activity feed
Admin — Room Mgmt	Admin	Room inventory table, Add/Edit/Deactivate controls, capacity and type filters
Admin — Approval Queue	Admin	Pending requests list, requester info, room/time detail, Approve/Reject action with remarks modal

3.3  Data Model (Entity-Relationship Summary)
The database consists of three primary entities with the following structure and relationships:
Entity	Key Attributes	Constraints & Notes
USER	user_id (PK), full_name, email (UK), password_hash, role ENUM, created_at	Email must be unique university address; role restricted to Student / Faculty / Admin
ROOM	room_id (PK), room_number (UK), room_type, capacity, is_active	is_active enables soft deletion; room_number unique system-wide
BOOKING	booking_id (PK), user_id (FK), room_id (FK), booking_date, start_time, end_time, purpose, status ENUM, admin_remarks, created_at	UNIQUE(room_id, booking_date, start_time) prevents double-booking at DB level; status: Pending / Approved / Rejected
Relationships: USER (1) submits (M) BOOKING  |  ROOM (1) is reserved via (M) BOOKING  |  USER/Admin (1) reviews (M) BOOKING

3.4  Technology Stack
Layer	Technology	Role & Justification
Frontend	React.js + Tailwind CSS	Component-based SPA architecture; Tailwind provides utility-first responsive styling without custom CSS overhead
Backend	Python Flask + Flask-RESTful	Lightweight REST API framework; minimal boilerplate; ideal for 2-person team delivering an MVP within 5 sprints
Authentication	Flask-JWT-Extended	Stateless JWT tokens eliminate server-side session state; role claims embedded in token payload for RBAC enforcement
ORM	SQLAlchemy	Declarative model definitions map directly to ER entities; query abstraction reduces raw SQL exposure
Database	SQLite (dev) / MySQL (prod)	SQLite enables zero-config local development; MySQL provides production-grade concurrency and constraint enforcement
Version Control	Git + GitHub	Branch-per-feature strategy; each sprint closes with a tagged release commit; enables parallel frontend/backend development
Project Mgmt	Trello	Scrum board with To Do / In Progress / Done columns; sprint backlog tracked per milestone
Diagrams	Draw.io / Lucidchart	UML, ER diagrams, architecture diagrams, and wireframes produced as formal project artifacts

 
Section 4: Tasks & Agile Sprint Plan
This section maps all major development tasks to a five-sprint Agile/Scrum execution plan. Sprint 4 consolidates full-stack development (frontend + backend) into a single sprint, reducing the original six-sprint structure to five, reflecting the team's capacity and the MVP scope.
4.1  Sprint Overview
Sprint	Phase	Weeks	Primary Deliverable
S1	Planning & Proposal	Wk 6–8	Project Proposal, Risk Register, Gantt Chart, Scrum Setup
S2	Requirements & SRS	Wk 8–10	SRS Document, Use Case & ER Diagrams, FR/NFR Tables
S3	System Design	Wk 10–12	Architecture, DB Schema, Wireframes, Class/Sequence/Activity Diagrams
S4	Full-Stack Build	Wk 12–14	Complete Backend API + Frontend UI + API Integration + Alpha Release
S5	QA, Delivery & PM	Wk 14–16	Final Tested Application, Project Report, Presentation, PM Evidence

4.2  Sprint 1 — Planning & Proposal  (Weeks 6–8)
Establishes project governance, team structure, and the formal project proposal submitted as Milestone 1.
Task	Abdullah (24K-0013)	Zahid (24K-0015)
Define system scope and MVP boundaries	Lead	Support
Select and justify technology stack	Lead	Review
Identify stakeholders and define actors	Support	Lead
Draft and format project proposal document	Support	Lead
Develop Risk Register (7 risks with mitigations)	Lead	Support
Create Gantt Chart (Wk 6–16)	Support	Lead
Configure Trello Scrum board and GitHub repository	Lead	Support
Milestone Deliverable: M1 — Project Proposal, Gantt Chart, Risk Register, Scrum Board (Week 8)
4.3  Sprint 2 — Requirements & SRS  (Weeks 8–10)
Captures and documents all system requirements in IEEE 830 format, producing formal UML artifacts for Milestone 2.
Task	Abdullah (24K-0013)	Zahid (24K-0015)
Conduct requirements elicitation (interviews / surveys)	Shared	Shared
Write Functional Requirements (FR-01 to FR-22)	Lead	Review
Write Non-Functional Requirements (NFR-01 to NFR-07)	Lead	Review
Produce IEEE 830 SRS document	Support	Lead
Draw Use Case Diagram (4 actors, 12 use cases)	Support	Lead
Draft initial Entity-Relationship (ER) Diagram	Lead	Support
Milestone Deliverable: M2 — SRS Document, Use Case Diagram, ER Diagram (Week 10)
4.4  Sprint 3 — System Design  (Weeks 10–12)
Translates requirements into formal engineering design artifacts: architectural diagrams, refined DB schema, wireframes, and all remaining UML diagrams for Milestone 3.
Task	Abdullah (24K-0013)	Zahid (24K-0015)
Finalise DB schema with full constraints and indexes	Lead	Review
Design REST API specification (endpoints, methods, payloads)	Lead	Review
Create System Architecture / Deployment Diagram	Support	Lead
Draw Class Diagram (User, Room, Booking entities + methods)	Lead	Support
Draw Sequence Diagram (booking request flow)	Support	Lead
Draw Activity Diagram (full reservation workflow)	Support	Lead
Produce UI Wireframes for all 9 screens	Review	Lead
Milestone Deliverable: M3 — Architecture, DB Schema, Class/Sequence/Activity Diagrams, Wireframes (Week 12)
 
4.5  Sprint 4 — Full-Stack Development  (Weeks 12–14)
This is the consolidated development sprint combining backend API development, frontend UI construction, and API integration into a single execution phase. The sprint concludes with an alpha release for stakeholder feedback.
4.5.1  Backend Development Track  (Abdullah — 24K-0013)
Backend Task	Week	Status Target
Initialise Flask project, configure SQLAlchemy, SQLite dev DB, and CORS	Wk 12	Done by Wk 12
Implement User model + /auth/register and /auth/login endpoints with JWT issuance	Wk 12	Done by Wk 12
Implement Room model + /rooms CRUD endpoints (Admin-gated via JWT middleware)	Wk 12–13	Done by Wk 13
Implement Booking model + /bookings POST endpoint with conflict detection logic	Wk 13	Done by Wk 13
Implement /bookings GET (user history) and DELETE (cancellation + slot release)	Wk 13	Done by Wk 13
Implement /admin/bookings endpoints: list pending, approve, reject with remarks	Wk 13–14	Done by Wk 14
Write unit tests for conflict detection, authentication, and approval workflow	Wk 14	Done by Wk 14

4.5.2  Frontend Development Track  (Zahid — 24K-0015)
Frontend Task	Week	Status Target
Bootstrap React app with Tailwind CSS, React Router, and Axios HTTP client	Wk 12	Done by Wk 12
Implement AuthContext (JWT storage, role-based routing guards)	Wk 12	Done by Wk 12
Build Login / Register screen with validation and error messaging	Wk 12–13	Done by Wk 13
Build Room Search screen with filter bar and availability badge cards	Wk 13	Done by Wk 13
Build Booking Form screen with date picker, time selector, conflict warning	Wk 13	Done by Wk 13
Build Booking History screen with status badge and cancel action	Wk 13–14	Done by Wk 14
Build Admin Panel: room inventory CRUD, approval queue, remarks modal	Wk 14	Done by Wk 14

4.5.3  Integration & Alpha Release
Integration Task	Assigned To	Week
Connect all React API calls to live Flask endpoints via Axios	Zahid	Wk 14
End-to-end test: registration > search > book > approve > notify flow	Both	Wk 14
Bug-fix pass: backend edge cases and frontend responsive issues	Abdullah	Wk 14
Deploy alpha build locally; conduct structured user feedback sessions	Both	Wk 14
Milestone Deliverable: M4 — Working Alpha Application, User Feedback Report, Change Log (Week 14)
4.6  Sprint 5 — QA, Delivery & PM  (Weeks 14–16)
The final sprint incorporates user feedback, completes comprehensive testing, polishes the application, and produces all final documentation and project management evidence.
Task	Abdullah (24K-0013)	Zahid (24K-0015)
Incorporate alpha feedback: prioritised change log implementation	Backend fixes	Frontend fixes
Integration testing: booking + approval module end-to-end	Shared	Shared
System testing: full reservation workflow validation	Lead	Support
User Acceptance Testing (UAT) with >= 3 real university users	Support	Lead
Write code documentation and API reference	Lead	Review
Write final project report (strengths, challenges, lessons)	Support	Lead
Produce presentation slides for final demo	Support	Lead
Compile PM Evidence: Trello screenshots, sprint retrospectives, GitHub history	Shared	Shared
Project evaluation report: retrospective analysis	Shared	Shared
Milestone Deliverables: M5 Final Application + Report + Presentation  |  M6 Evaluation Report  |  M7 PM Evidence (Week 16)

4.7  Gantt Chart Summary
Task / Sprint	W6	W7	W8	W9	W10	W11	W12	W13	W14	W15	W16
S1: Planning & Proposal	█	█	█								
S2: Requirements & SRS			█	█	█						
S3: System Design					█	█	█				
S4: Full-Stack Build							█	█	█		
S5: QA, Delivery & PM									█	█	█

4.8  Definition of Done (DoD)
A sprint task is considered complete only when ALL of the following conditions are met:
•	Code is committed to the feature branch and merged to main via a reviewed pull request on GitHub
•	Associated unit or integration tests are written and passing
•	All form inputs relevant to the feature are validated at both frontend and backend layers
•	Feature is demonstrated and accepted in the sprint review session
•	Trello card is moved to Done column and the sprint retrospective note is updated

 
Document Summary
This document provides the complete engineering foundation for the University Room Booking System (URBS), covering all four required dimensions:
Section	Coverage	Key Output
1. End Users	3 primary roles + 1 automated actor + indirect stakeholders	Role definitions with access levels, interaction maps, and constraint tables
2. Requirements	22 FRs across 6 categories + 7 NFRs with acceptance criteria	Traceable, testable requirements baseline for all sprints
3. Components	5 modules, 9 UI screens, 3-entity data model, 8-layer tech stack	Architectural blueprint for system implementation
4. Tasks	5 Agile sprints with task-level assignments, Gantt chart, and DoD	Executable project plan with clear milestone deliverable mapping

The revised five-sprint structure improves execution efficiency by unifying the full-stack development effort in Sprint 4, enabling tighter feedback loops between backend API delivery and frontend integration, and preserving a dedicated final sprint for quality assurance, stakeholder demonstration, and project management documentation.
