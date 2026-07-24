# Student Registration Web Application

This is an ASP.NET Core MVC web application that manages course registration for students. It allows students to browse the course catalog, enroll in a single course, and manage their profile details. It also provides administrators with tools to manage courses and view a directory of registered students.

The application uses ASP.NET Core Identity to handle user accounts, authentication, and role-based access controls. The database is powered by SQL Server and accessed using Entity Framework Core.

---

## Project Overview

The project is designed to demonstrate how to build a web application with user registration, login, and authorization. It includes two primary roles: **Administrator** and **Student**. Each role has specific permissions enforced by controllers and views, ensuring that users can only access their authorized resources.

---

## Features

### Authentication
*   **User Registration:** New users can register for an account and are automatically assigned the "Student" role.
*   **Secure Login:** Users can sign in using their registered email and password.
*   **Layout Awareness:** The navigation bar dynamically displays options and the logged-in user's email based on their authentication status and role.

### Student Features
*   **Course Catalog:** Students can view all courses in the academic catalog.
*   **Course Enrollment:** Students can register for exactly one course.
*   **Profile Management:** Students can view and update their profile details (First Name and Last Name).
*   **Drop Course:** Students can drop their current course registration to sign up for a different one.

### Administrator Features
*   **Course CRUD:** Administrators can create new courses, edit existing course details, and delete courses.
*   **Student Directory:** Administrators can view a list of all registered student users.

### Security
*   **Role-based Authorization:** Restricts access to administrative endpoints and student-specific pages using `[Authorize]` attributes.
*   **Access Denied Redirection:** Redirects unauthorized access attempts to a dedicated "Access Denied" page.
*   **CSRF Protection:** Form submissions validate anti-forgery tokens to protect against cross-site request forgery.

---

## Technology Stack

| Technology | Purpose |
| :--- | :--- |
| **ASP.NET Core 8 MVC** | Application Framework |
| **C#** | Programming Language |
| **Entity Framework Core 8** | Object-Relational Mapper (ORM) |
| **SQL Server** | Relational Database |
| **ASP.NET Core Identity** | Membership and Authentication |
| **Bootstrap 5** | Responsive UI Styling |
| **Razor Views** | Server-Side HTML Rendering |

---

## Project Structure

*   **Controllers:** Handle HTTP requests, process user inputs, and return corresponding Razor views.
*   **Models:** Define the database schemas and entities used in the application.
*   **ViewModels:** Structure data models used specifically to pass information to and from views.
*   **Views:** Razor templates containing HTML and C# code for user interface rendering.
*   **Data:** Includes the database context (`ApplicationDbContext`) and initialization script (`DbInitializer`) to seed roles, a default administrator, and courses.
*   **Migrations:** Code-First migrations tracking changes made to the database schema.
*   **wwwroot:** Static resources like custom styles, scripts, and libraries (Bootstrap, jQuery).
*   **Program.cs:** Configures application dependencies, services, authentication cookies, and the HTTP request middleware pipeline.

---

## User Roles

### Administrator
*   Create, read, update, and delete courses.
*   View the directory of all registered students.

### Student
*   Browse the course catalog.
*   Register for or drop a single course.
*   View and edit their own profile information.

---

## Database

The relational schema is mapped directly to SQL Server:
*   **AspNetUsers:** Custom identity table storing credentials and user details (First Name, Last Name).
*   **AspNetRoles:** System roles catalog, defining Admin and Student groups.
*   **AspNetUserRoles:** Junction table mapping user accounts to their respective roles.
*   **Courses:** Stores the course catalog (Course Code, Title, Description, Credits).
*   **CourseRegistrations:** Maps a student to a registered course. It enforces a unique index on the student identifier to prevent multiple registrations.

---

## Installation

### Prerequisites
*   .NET 8 SDK
*   SQL Server (LocalDB or Express)
*   SQL Server Management Studio (SSMS)

### Clone the Repository
```bash
git clone https://github.com/snaddans/Student-Registration-WebApp.git
cd Student-Registration-WebApp
```

### Restore Packages
```bash
dotnet restore
```

### Update Database
```bash
dotnet ef database update
```
*(Note: Database initialization and migrations run automatically on the first application launch.)*

### Run the Application
```bash
dotnet run
```

---

## Default Administrator

The database initializer creates a default administrator account with the following credentials:
*   **Email:** `admin@studentapp.com`
*   **Password:** `Admin@123`

---

## Screenshots

**Home Page**  
![Home Page](3_anonymous_navigation.png)

**Login**  
*(Add login screenshot path here)*

**Student Dashboard**  
![Student Dashboard](4_successful_login.png)

**Student Profile**  
*(Add student profile screenshot path here)*

**Course Management**  
![Course Management](1_admin_navigation.png)

**Student Directory**  
*(Add student directory screenshot path here)*

**Access Denied**  
![Access Denied](6_access_denied.jpg)

---

## Future Improvements

*   **Email Verification:** Require email confirmation for new user accounts.
*   **Password Reset:** Implement password recovery using secure tokens.
*   **Roster Pagination:** Add pagination to the student directory and course index for scalability.
*   **Course Capacity:** Limit the maximum number of students that can register for a single course.
*   **Enrollment Logs:** Log registration history for auditing purposes.

---

## Learning Outcomes

This project demonstrates:
*   Setting up ASP.NET Core Identity with custom user properties.
*   Designing relational databases and configuring foreign keys and indexes using Entity Framework Core.
*   Implementing role-based security using routing filters and custom access-denied pages.
*   Building responsive server-rendered views with Bootstrap 5.

---

## Author
*   **Author:** Shashank Dubey
*   **Academic Level:** B.Tech Computer Science (AI & ML)
*   **Purpose:** Internship Assignment
