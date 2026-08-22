# Dayflow HRMS

## About the Project

**Dayflow HRMS** is a Human Resource Management System designed to simplify and manage common HR activities through a single web-based application.

The system allows employees and HR personnel to manage employee information, attendance, leave requests, and payroll information. It provides different access levels for **Employees** and **HR**, ensuring that users can access the features relevant to their role.

## Features

### Employee

* Register and log in securely
* View personal profile information
* Update profile details
* Check in and check out for attendance
* View attendance records
* Submit leave requests
* View leave request status
* View payroll information

### HR

* Log in as an HR user
* View employee information
* View employee attendance
* Review and approve/reject leave requests
* Add and update payroll information
* Manage employee-related information

## Technologies Used

* **Frontend:** HTML, CSS, JavaScript
* **Backend:** C
* **Database:** MySQL
* **Networking:** C socket programming
* **Authentication:** Session-based authentication
* **Password Security:** SHA-256 hashing

## System Architecture

```text
             ┌─────────────────────┐
             │      Frontend       │
             │  HTML / CSS / JS    │
             └──────────┬──────────┘
                        │
                   HTTP Requests
                        │
                        ▼
             ┌─────────────────────┐
             │     C Backend       │
             │                     │
             │  HTTP Server        │
             │  API Handling       │
             │  Authentication     │
             │  Business Logic     │
             └──────────┬──────────┘
                        │
                  MySQL C API
                        │
                        ▼
             ┌─────────────────────┐
             │    MySQL Database   │
             │                     │
             │ Employees           │
             │ Attendance          │
             │ Leave               │
             │ Payroll             │
             │ Sessions            │
             └─────────────────────┘
```

## Backend

The backend is implemented in **C**. It creates a socket-based HTTP server that accepts client connections and processes requests using separate threads.

The backend provides API endpoints for registration, login, profile management, attendance, leave management, employee management, and payroll.

The backend communicates directly with MySQL using the MySQL C API. It also handles session authentication and role-based access for employees and HR users.

## Database

**MySQL** is used to store and manage the application's persistent data.

The database stores information related to:

* User accounts
* Employee details
* Attendance
* Leave requests
* Payroll
* Login sessions

MySQL is suitable for the project because the HRMS contains structured and related data that needs to be stored, retrieved, updated, and managed efficiently.

## Authentication and Security

The system provides login-based authentication using sessions.

Passwords are processed using **SHA-256 hashing** before being stored in the database. After successful login, the backend creates a session token that is used to identify the authenticated user.

The system also provides role-based access, separating **HR** and **Employee** functionality.

## Main API Operations

| API                   | Method | Purpose                      |
| --------------------- | ------ | ---------------------------- |
| `/api/register`       | POST   | Register a new user          |
| `/api/login`          | POST   | Authenticate a user          |
| `/api/logout`         | POST   | Log out the user             |
| `/api/me`             | GET    | Get current user information |
| `/api/profile`        | POST   | Update profile               |
| `/api/attendance`     | GET    | View attendance              |
| `/api/checkin`        | POST   | Mark check-in                |
| `/api/checkout`       | POST   | Mark check-out               |
| `/api/leave`          | POST   | Submit a leave request       |
| `/api/leaves`         | GET    | View leave requests          |
| `/api/leave/review`   | POST   | Approve or reject leave      |
| `/api/employees`      | GET    | View employees               |
| `/api/payroll`        | GET    | View payroll                 |
| `/api/payroll/update` | POST   | Update payroll               |

## How the System Works

1. The user interacts with the frontend.
2. The frontend sends an HTTP request to the C backend.
3. The backend receives and processes the request.
4. The backend communicates with the MySQL database when data needs to be stored or retrieved.
5. MySQL returns the required data to the backend.
6. The backend sends a response back to the frontend.
7. The frontend displays the result to the user.

## Project Objective

The main objective of Dayflow HRMS is to provide a simple and centralized platform for managing essential HR operations while reducing the need for separate manual processes.

## Conclusion

Dayflow HRMS combines a web-based frontend, a C-based backend server, and a MySQL database to create an integrated Human Resource Management System. The system provides separate functionality for employees and HR while managing important HR operations such as employee information, attendance, leave, authentication, and payroll.
