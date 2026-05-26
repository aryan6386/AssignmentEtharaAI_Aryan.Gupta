Prompt
Project Overview
Build a full-stack MERN College Attendance Management System for colleges to digitally manage student attendance, reduce manual register work, and provide a reliable platform for students, teachers, and college management.
The project should include:
•	Secure role-based login system
•	Admin control panel
•	Teacher attendance marking
•	Student attendance summary
•	Charts, analytics, and downloadable reports
________________________________________
Tech Stack
React.js — builds the frontend UI including login page, admin, teacher, and student dashboards, attendance pages, and reports
React Router DOM — handles navigation between pages like login, dashboard, profile, and reports without reloading the browser
Axios — sends requests from the React frontend to backend APIs for actions like login, adding students, marking attendance, and fetching reports
Tailwind CSS — designs a clean, modern, and responsive UI that works across mobile, tablet, and desktop screens
Context API — manages global data such as the logged-in user, role, token, and logout function across the entire app
Chart.js / Recharts — displays attendance data visually through graphs and charts like subject-wise attendance and monthly attendance trends
Node.js — runs JavaScript on the server side and handles all backend logic
Express.js — creates backend APIs for authentication, students, teachers, attendance, classes, subjects, and reports
MongoDB — stores all application data including users, students, teachers, subjects, classes, and attendance records
Mongoose — defines database schemas and models to interact with MongoDB in a structured way
JWT Authentication — secures the login system and enforces role-based access control for admin, teacher, and student
bcrypt.js — hashes passwords before saving them to the database to ensure secure storage
dotenv — stores sensitive configuration values like database URL, JWT secret key, and server port safely outside the codebase
CORS — allows the frontend and backend to communicate with each other when running on different ports
REST APIs — connect the frontend and backend through defined routes such as login, add student, mark attendance, and generate reports
________________________________________
Project Structure
Create 2 separate folders:
bash
attendance-system/
│
├── backend/    → Node.js + Express + MongoDB backend
└── frontend/   → React.js frontend
________________________________________
FEATURES REQUIRED
1. User Authentication

Login Page — displays a clean login form where users enter their email and password, validates the inputs on the frontend before sending the request, and shows an error message if credentials are incorrect
Logout Functionality — clicking logout clears the JWT token and user data from Context API and local storage, ends the session, and redirects the user back to the login page
JWT Token Authentication — after a successful login the server returns a JWT token which is stored in local storage and attached to every API request in the Authorization header so the backend can verify the user's identity
Role-based Access Control — the JWT token contains the user's role which is read by the frontend to show the correct dashboard and by the backend middleware to allow or block access to specific routes based on whether the user is Admin, Teacher, or Student
Store Token Securely via Context API — the JWT token, user details, and role are stored in a global AuthContext so any component in the app can access the logged-in user's data without passing props manually through every level
Protected Routes — a ProtectedRoute component wraps all dashboard pages and checks whether a valid token exists before rendering the page, and redirects unauthenticated users to the login page if no token is found
Session Persistence — when the page is refreshed the token is read back from local storage and the user remains logged in without needing to enter credentials again until the token expires or they manually log out
Show Logged-in User Info — the navbar and sidebar display the logged-in user's name, role, and profile initial or avatar so the user always knows which account they are currently using


2. User Roles
Admin can:

Add, Update, Delete Students and Teachers — create new student and teacher profiles along with linked user accounts, update their details when needed, and permanently remove them along with their user accounts from the system
Create Departments, Classes, Semesters, Sections, and Subjects — set up the complete academic structure of the college by adding departments, defining classes with semester and section details, and creating subjects for each semester
Assign Subjects to Teachers — link a specific subject to a teacher so that teacher becomes responsible for marking attendance and generating reports for that subject
Assign Students to Classes — add students to their respective classes so the correct student list appears when a teacher marks attendance for that class
View All Attendance Records — access a complete list of all attendance records across all departments, classes, subjects, and dates with search and filter options
Generate and Download Reports — generate attendance reports filtered by department, class, subject, or date range and download them as PDF or CSV files
View Low Attendance Students — see a dedicated list of all students across the college whose attendance percentage has dropped below 75% in any subject
Manage User Accounts — view, activate, or deactivate user accounts for students and teachers to control who can log into the system

Teacher can:

View Assigned Subjects and Classes — see a list of all subjects and classes currently assigned to them by the admin so they know which groups they are responsible for
Mark and Edit Attendance — select a class, subject, and date, then mark each student as Present, Absent, or Late with optional remarks, and edit any previously submitted attendance record if a mistake was made
View Attendance History — browse all past attendance records they have submitted, filtered by subject, class, or date to review previous sessions
Generate Class-wise Reports — generate a detailed attendance report for a specific class and subject showing each student's attendance percentage and download it as PDF or CSV
View Low Attendance Students — see a filtered list of students in their assigned classes whose attendance has fallen below 75% so they can follow up or notify them

Student can:

View Profile Details — see their personal information including name, roll number, department, semester, section, batch, and assigned subjects on their profile page
View Subject-wise and Overall Attendance Percentage — see a breakdown of their attendance for each subject along with a combined overall attendance percentage calculated from all subjects
View Attendance History — browse a date-wise list of all their attendance records showing the subject, date, and whether they were marked Present, Absent, or Late
Receive Low Attendance Warnings — see a highlighted warning message on their dashboard for any subject where their attendance has dropped below 75% prompting them to attend upcoming classes
Download Attendance Report — download their complete attendance report as a PDF or CSV file containing subject-wise percentages and full attendance history


3. Admin Dashboard

Total Students Count — displays a card showing the total number of students currently registered in the system across all departments and classes
Total Teachers Count — displays a card showing the total number of teachers currently registered in the system
Total Classes Count — displays a card showing how many classes have been created across all departments and semesters
Total Subjects Count — displays a card showing the total number of subjects created in the system across all departments and semesters
Total Departments Count — displays a card showing how many departments have been set up in the college system
Low Attendance Student Count — displays a highlighted card showing the number of students currently below 75% attendance so the admin can take immediate action
Recent Attendance Activity — shows a live feed or table of the most recently submitted attendance records including teacher name, subject, class, and date
Report Generation Options — provides quick buttons or dropdown filters to generate attendance reports by department, class, subject, or date range directly from the dashboard
Quick Links to Manage Students, Teachers, Subjects, and Classes — displays shortcut buttons or icon cards that take the admin directly to the manage students page, manage teachers page, manage subjects page, and manage classes page with a single click


4. Teacher Dashboard

Assigned Classes — displays a list or cards showing all classes currently assigned to the logged-in teacher so they can quickly see which groups they are responsible for
Assigned Subjects — displays a list or cards showing all subjects assigned to the teacher along with the related department and semester details
Mark Attendance Button — shows a prominent button that takes the teacher directly to the attendance marking page where they can select a class, subject, and date to begin marking
Low Attendance Students — displays a list of students from the teacher's assigned classes whose attendance has dropped below 75% so the teacher can monitor and follow up
Class-wise Attendance Summary — shows a summary table or chart displaying the overall attendance percentage for each of the teacher's assigned classes to give a quick overview of class performance
Attendance History — shows a table of all previously submitted attendance records by the teacher with subject, class, date, and total present count for quick reference
Report Generation Options — provides filter options to generate and download class-wise or subject-wise attendance reports directly from the dashboard without navigating to a separate page


5. Student Dashboard

Overall Attendance Percentage — displays a large percentage value or progress circle showing the student's combined attendance across all subjects so they can see their general standing at a glance
Subject-wise Attendance Percentage — shows a table or set of cards listing each subject with the number of classes conducted, classes attended, and the calculated attendance percentage for that subject
Total Present Classes — displays a count of how many classes the student has been marked Present across all subjects
Total Absent Classes — displays a count of how many classes the student has been marked Absent across all subjects
Total Late Records — displays a count of how many times the student has been marked Late across all subjects
Monthly Attendance Chart — shows a bar chart or line chart displaying the student's attendance trend month by month so they can see if their attendance is improving or declining over time
Low Attendance Warning Message — displays a clearly visible warning banner for any subject where the student's attendance is below 75%, for example: Your attendance in Maths is below 75%. Please attend upcoming classes regularly.


6. Attendance Management
Teacher must select the following before marking attendance:

Department — teacher selects the department to filter the relevant classes and subjects for that department
Semester — teacher selects the semester to narrow down the class list to the correct academic term
Section — teacher selects the section to identify the exact group of students within that semester
Subject — teacher selects the subject for which attendance is being marked on that day
Date — teacher selects or confirms the date for the attendance session, defaulting to today's date
Student List — the system automatically loads the full list of students assigned to the selected class so the teacher can mark each one individually

Attendance status options:

Present — marks the student as present for that class session
Absent — marks the student as absent for that class session
Late — marks the student as late for that class session, which is counted separately from both present and absent in reports

Each attendance record must store:

Student ID — the unique identifier of the student being marked so the record is linked to the correct student profile
Status — the selected attendance status for that student which is either Present, Absent, or Late
Remarks — an optional text field where the teacher can add a short note for that student such as medical leave or prior permission


7. Attendance Calculation

Total Classes Conducted — counts all attendance sessions recorded for a subject so the system knows the total number of classes held for that subject
Total Classes Attended — counts all records where the student was marked Present for a specific subject across all sessions
Total Absent Classes — counts all records where the student was marked Absent for a specific subject across all sessions
Total Late Records — counts all records where the student was marked Late for a specific subject and displays it separately in the student dashboard and reports
Subject-wise Attendance Percentage — calculates the attendance percentage for each subject individually using the formula so the student can see their standing in every subject
Overall Attendance Percentage — calculates a combined attendance percentage across all subjects by dividing total present classes by total conducted classes across all subjects
Low Attendance Status — automatically flags a student as low attendance for any subject where their calculated percentage falls below 75% and triggers the warning message on their dashboard

Formula:
Attendance Percentage = (Total Present Classes / Total Conducted Classes) × 100
Low Attendance Condition:

If attendance percentage is less than 75%, the system marks that subject as low attendance and displays a warning message to the student on their dashboard and to the teacher and admin in the low attendance list
________________________________________
8. DATABASE MODELS
User Model
js
{
  name,
  email,
  password,
  role,       // admin | teacher | student
  isActive
}
Student Model
js
{
  userId,
  student_id,
  name,
  email,
  rollNo,
  department,
  semester,
  section,
  batch
}
Teacher Model
js
{
  userId,
  teacher_id,
  name,
  email,
  employee_id,
  department,
  assigned_subjects
}
Subject Model
js
{
  subject_id,
  subject_name,
  subject_code,
  department,
  semester,
  teacher_id
}
Class Model
js
{
  class_id,
  department,
  semester,
  section,
  batch,
  subjects,
  students
}
Attendance Model
js
{
  attendance_id,
  class_id,
  subject_id,
  teacher_id,
  date,
  attendance_records: [
    { student_id, status, remarks }
  ]
}
// status: ["Present", "Absent", "Late"]
________________________________________
Here is the detailed and specific version of the Backend API section:

9. Backend APIs
Authentication APIs

Register User — accepts name, email, password, and role, hashes the password using bcrypt, creates a new user in the database, and returns a success message
Login User — accepts email and password, verifies credentials, generates a JWT token containing user ID and role, and returns the token with user details
Get Logged-in User Profile — reads the JWT token from the request header, verifies it, and returns the current logged-in user's name, email, and role
Logout User — clears the JWT token from the client side and ends the user session


Admin APIs

Add Student — accepts student details like name, email, roll number, department, semester, section, and batch, creates a student profile, and also creates a linked user account with the student role
Update Student — accepts updated student details by student ID and updates the matching student record in the database
Delete Student — accepts a student ID, deletes the student profile, and also removes the linked user account from the database
Add Teacher — accepts teacher details like name, email, employee ID, and department, creates a teacher profile, and also creates a linked user account with the teacher role
Update Teacher — accepts updated teacher details by teacher ID and updates the matching teacher record in the database
Delete Teacher — accepts a teacher ID, deletes the teacher profile, and also removes the linked user account from the database
Create Department — accepts department name and code and saves a new department record in the database
Create Class — accepts department, semester, section, and batch details and creates a new class record in the database
Create Subject — accepts subject name, subject code, department, and semester and saves a new subject record in the database
Assign Teacher to Subject — accepts a teacher ID and subject ID and links the teacher to that subject in the database
Assign Students to Class — accepts a class ID and a list of student IDs and adds those students to the selected class
View All Records — returns a complete list of all students, teachers, classes, subjects, and departments stored in the database
Generate Reports — accepts filters like department, class, subject, or date range and returns a full attendance report for admin review and download


Teacher APIs

Get Assigned Classes and Subjects — reads the teacher ID from the token and returns all classes and subjects currently assigned to that teacher
Mark Attendance — accepts department, semester, section, subject, date, and a list of students with their attendance status (Present, Absent, Late) and saves the attendance record in the database
Edit Attendance — accepts an attendance record ID and updated status values for students and updates the existing attendance record in the database
View Attendance History — accepts filters like subject, class, or date and returns all past attendance records marked by that teacher
Generate Class-wise Report — accepts a class ID and subject ID and returns a detailed attendance report for all students in that class for that subject
View Low Attendance Students — reads the teacher's assigned classes and returns a list of students whose attendance percentage has fallen below 75%


Student APIs

View Own Profile — reads the student ID from the token and returns the student's personal details like name, roll number, department, semester, section, and batch
View Subject-wise Attendance — returns a breakdown of attendance for each subject showing total classes conducted, total present, total absent, total late, and attendance percentage per subject
View Overall Attendance — calculates and returns the student's combined attendance percentage across all subjects
View Attendance History — returns a date-wise list of all attendance records for the logged-in student showing subject, date, and status for each entry
Download Report — generates and returns the student's complete attendance report as a downloadable PDF or CSV file containing subject-wise and overall attendance data
________________________________________
10. REPORT GENERATION
The system must generate:
•	Student attendance dashboard
•	Teacher class attendance report
•	Admin-level attendance analytics
•	Subject-wise and class-wise attendance reports
•	Low-attendance student list
•	Downloadable PDF reports
•	Downloadable CSV reports
•	Attendance charts and graphs
________________________________________
11. FILES TO CREATE
BACKEND
bash
backend/
│
├── server.js
├── .env
├── package.json
├── config/
│   └── db.js
├── models/
│   ├── User.js
│   ├── Student.js
│   ├── Teacher.js
│   ├── Subject.js
│   ├── Class.js
│   └── Attendance.js
├── routes/
│   ├── authRoutes.js
│   ├── adminRoutes.js
│   ├── teacherRoutes.js
│   ├── studentRoutes.js
│   └── attendanceRoutes.js
├── controllers/
│   ├── authController.js
│   ├── adminController.js
│   ├── teacherController.js
│   ├── studentController.js
│   └── attendanceController.js
├── middleware/
│   ├── authMiddleware.js
│   ├── roleMiddleware.js
│   └── errorMiddleware.js
└── utils/
    ├── generateToken.js
    └── reportGenerator.js
FRONTEND
bash
frontend/
│
├── package.json
├── index.html
└── src/
    ├── main.jsx
    ├── App.jsx
    ├── api/
    │   └── axiosInstance.js
    ├── context/
    │   └── AuthContext.jsx
    ├── routes/
    │   ├── ProtectedRoute.jsx
    │   └── RoleBasedRoute.jsx
    ├── components/
    │   ├── Navbar.jsx
    │   ├── Sidebar.jsx
    │   ├── DashboardCard.jsx
    │   ├── AttendanceChart.jsx
    │   └── Table.jsx
    ├── pages/
    │   ├── Login.jsx
    │   ├── AdminDashboard.jsx
    │   ├── TeacherDashboard.jsx
    │   ├── StudentDashboard.jsx
    │   ├── ManageStudents.jsx
    │   ├── ManageTeachers.jsx
    │   ├── ManageSubjects.jsx
    │   ├── ManageClasses.jsx
    │   ├── MarkAttendance.jsx
    │   ├── AttendanceHistory.jsx
    │   ├── Reports.jsx
    │   ├── LowAttendance.jsx
    │   ├── Profile.jsx
    │   └── Unauthorized.jsx
    └── styles/
        └── index.css
________________________________________
12. Security

Hash Passwords using bcrypt.js — when a user registers or is added by admin, the plain text password is hashed using bcrypt before saving to the database so the original password is never stored directly
JWT Tokens for Authentication — after a successful login, the server generates a JWT token containing the user ID and role, which is sent to the frontend and attached to every protected API request in the Authorization header
Role-based Route Authorization — every protected backend route checks the user's role from the JWT token and only allows access if the role matches, for example only admin can access add student route and only teacher can access mark attendance route
Environment Variables via dotenv — sensitive values like MongoDB connection URL, JWT secret key, bcrypt salt rounds, and server port are stored in a .env file and never written directly in the code
Input Validation on All Forms — every form input on the frontend and every API request on the backend is validated before processing, for example checking that email format is correct, password meets minimum length, and required fields are not empty
Protected API Routes with Middleware — all routes except login and register are protected by an auth middleware that verifies the JWT token on every request and rejects any request with a missing or invalid token
CORS Setup for Frontend-Backend Communication — the backend is configured with CORS to only allow requests from the frontend origin so unauthorized domains cannot access the backend APIs
Unauthorized Access Handling Page — if a user tries to access a route they are not allowed to, such as a student trying to open the admin dashboard, they are automatically redirected to a dedicated Unauthorized Access page with a clear message


13. Performance and Scalability

MongoDB Indexing — frequently queried fields like student ID, teacher ID, class ID, subject ID, and date in the attendance collection are indexed in MongoDB to make database queries faster as data grows
Pagination for Students, Teachers, and Attendance Records — instead of loading all records at once, the backend returns data in pages with a defined limit per page so the application stays fast even with thousands of records
Search and Filter Options — the frontend provides search bars and filter dropdowns so users can quickly find students by name or roll number, filter attendance by subject or date, and filter teachers by department without loading all records
Optimized Database Queries — backend queries use only the required fields using MongoDB projection, avoid unnecessary nested lookups, and use aggregation pipelines where needed to calculate attendance percentages efficiently
Reusable React Components — common UI elements like tables, cards, forms, buttons, and charts are built as separate reusable components so the same component can be used across multiple pages without duplicating code
Modular Backend Folder Structure — the backend is divided into separate folders for models, routes, controllers, middleware, and utilities so each file has a single responsibility and the codebase is easy to navigate and maintain
Role-based Middleware — a dedicated role middleware function checks the user's role after token verification and blocks access to routes that do not match the required role, keeping route protection clean and reusable
Error Handling Middleware — a centralized error handling middleware in the backend catches all errors from routes and controllers and returns a consistent JSON error response with a status code and message instead of crashing the server


14. Modern UI Requirements

Smooth Scrolling on All Pages — all pages use CSS smooth scrolling behavior so navigation between sections feels fluid and natural instead of jumping abruptly
Hover Effects in the Navigation Bar — navbar and sidebar links have smooth hover animations like color changes, underline transitions, or background highlights to give visual feedback when the user moves the cursor over them
Clean and Modern Dashboard Layout — all dashboards use a structured layout with a fixed sidebar on the left, a top navbar, and a main content area displaying cards and tables in a well-spaced grid
Responsive Design for Mobile, Tablet, and Desktop — the layout adapts to all screen sizes using Tailwind CSS responsive utility classes so the application is fully usable on phones, tablets, laptops, and large monitors
Sidebar Navigation for Dashboards — each dashboard has a fixed sidebar with links to all relevant pages for that role, for example admin sidebar shows students, teachers, classes, subjects, reports, and settings
Cards for Summary Data — key statistics like total students, total teachers, total classes, and low attendance count are displayed in individual styled cards on the dashboard for quick visibility
Charts and Graphs for Attendance Analytics — attendance data is shown visually using bar charts for subject-wise attendance, line charts for monthly attendance trends, and pie charts for present versus absent ratio using Chart.js or Recharts
Loading States — whenever data is being fetched from the backend, a loading spinner or skeleton screen is shown so the user knows the application is working and not frozen
Empty States — when a list or table has no data to show, a friendly empty state message with an icon is displayed instead of showing a blank or broken layout
Error Messages — if an API call fails or form validation fails, a clear and specific error message is shown near the relevant field or at the top of the form so the user knows exactly what went wrong
Toast Notifications — short popup notifications appear at the corner of the screen to confirm successful actions like attendance marked, student added, or report downloaded, and also to show error alerts without interrupting the user's flow


15. Code Requirements

Clean Modular Code — each feature is broken into its own file or component so the codebase is organized, easy to read, and simple to update without affecting unrelated parts of the application
Comments Throughout — every major function, route, middleware, and component has a short comment above it explaining what it does, what parameters it accepts, and what it returns
Async/Await — all asynchronous operations like database queries, API calls, and file generation use async/await syntax with try/catch blocks instead of callbacks or promise chains for cleaner and more readable code
Separate API Utilities — all Axios API call functions on the frontend are written in a dedicated api or services folder so components do not contain raw API logic and the base URL is managed in one place using an Axios instance
Proper Folder Structure — the project follows the defined folder structure with separate folders for models, routes, controllers, middleware, utils on the backend and components, pages, context, routes, api, and styles on the frontend
Beginner-friendly Explanations in Comments — comments are written in simple language so that a beginner reading the code can understand what each section does, why it is needed, and how it connects to the rest of the application

________________________________________
16. FINAL OUTPUT REQUIRED
Provide:
•	Complete project code
•	Backend and frontend folder structure
•	MongoDB schema models
•	Authentication system with JWT
•	Role-based access control
•	All three dashboards (Admin, Teacher, Student)
•	Attendance marking and calculation logic
•	Low-attendance warning logic
•	Report generation (PDF + CSV)
•	Charts and graphs
•	Setup instructions
•	MongoDB connection guide
•	How to run backend and frontend
•	Postman testing instructions
•	Deployment guidance
________________________________________
DEVELOPMENT FLOW
Build the project step-by-step in this order:
1.	Backend setup
2.	MongoDB connection
3.	User authentication APIs
4.	Role-based middleware
5.	Student, Teacher, Subject, and Class models
6.	Admin management APIs
7.	Attendance marking APIs
8.	Attendance calculation logic
9.	Report generation APIs
10.	Frontend setup with React
11.	Routing with React Router DOM
12.	Login page
13.	Admin dashboard
14.	Teacher dashboard
15.	Student dashboard
16.	Attendance marking page
17.	Reports and charts
18.	PDF / CSV download
19.	Final testing and polishing
________________________________________
FINAL GOAL
The final application should work as a complete production-ready College Attendance Management System with:
•	Secure login
•	Role-based dashboards
•	Admin control panel
•	Teacher attendance marking
•	Student attendance summary
•	Subject-wise and class-wise reports
•	Low-attendance warnings
•	Charts and analytics
•	PDF / CSV report downloads
•	Responsive modern UI
•	Scalable backend architecture
