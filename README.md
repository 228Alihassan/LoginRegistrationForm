# C# WinForms Login and Registration System

## Project Overview

This project is a basic Login and Registration system built using C# Windows Forms and a SQL Server (LocalDB) database. It allows users to create new accounts and log in with existing credentials. The application demonstrates fundamental concepts of UI design with WinForms, event handling, and database interaction in C#.

## Features

*   **User Registration:** New users can sign up by providing an email, username, and password.
*   **User Login:** Existing users can authenticate using their username and password.
*   **Password Visibility:** Option to toggle password character visibility on both login and signup forms.
*   **Database Integration:** User credentials are stored and validated against a local SQL Server database.
*   **Form Navigation:** Users can easily switch between the Login and Signup forms. A Main form is displayed upon successful login.
*   **Custom UI:** Includes basic UI elements like colored panels, icons, and custom button styles.
*   **Error Handling:** Basic error messages for invalid input or database connection issues.

## Technologies Used

*   **Language:** C#
*   **Framework:** .NET Framework 4.7.2
*   **IDE:** Microsoft Visual Studio
*   **User Interface:** Windows Forms (WinForms)
*   **Database:** SQL Server LocalDB (`loginData.mdf`)
*   **Data Access:** ADO.NET (`SqlConnection`, `SqlCommand`, `SqlDataAdapter`)

## Setup & Prerequisites

1.  **Visual Studio:** Ensure you have Visual Studio (e.g., 2019 or 2022) installed with .NET desktop development workload.
2.  **.NET Framework:** The project targets .NET Framework 4.7.2.
3.  **SQL Server LocalDB:** This is typically installed with Visual Studio. If not, ensure you have a SQL Server instance available.
4.  **Icons (Optional):** The user icon (`icons8_user_male_circle_104px_2.png`) is sourced from icons8.com and is located in the `LoginRegistrationForm/Asset/` folder.

## Database Setup

1.  **Create the Database:**
    *   In Visual Studio, open **Server Explorer** (View > Server Explorer).
    *   Right-click on "Data Connections" and select "Add Connection..."
    *   Change Data source to "Microsoft SQL Server Database File (SqlClient)".
    *   For "Database file name (new or existing)", click "Browse..." and navigate to where you want to save your database file (e.g., within your project's `App_Data` folder or `Documents` folder). Name it `loginData.mdf`.
    *   Click "OK". Visual Studio will ask if you want to create it. Click "Yes".
2.  **Create the `admin` Table:**
    *   In Server Explorer, expand your `loginData.mdf` connection.
    *   Right-click on "Tables" and select "Add New Table" OR "New Query".
    *   If using "Add New Table", define the columns as specified below.
    *   If using "New Query", paste and execute the following SQL script:

    ```sql
    CREATE TABLE admin (
        id INT PRIMARY KEY IDENTITY(1,1),
        email VARCHAR(MAX) NULL,
        username VARCHAR(MAX) NULL,
        password VARCHAR(MAX) NULL,
        date_created DATE NULL
    );
    ```

3.  **Update Connection String (if necessary):**
    *   The connection string in `Form1.cs` and `Signup.cs` is hardcoded:
        ```csharp
        SqlConnection connect = new SqlConnection(@"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=C:\Users\WINDOWS 10\Documents\loginData.mdf;Integrated Security=True;Connect Timeout=30");
        ```
    *   **You MUST update the `AttachDbFilename` path to where you saved your `loginData.mdf` file on your system.** For better practice in larger projects, consider storing the connection string in `App.config`.

## How to Run

1.  Clone the repository or download the source code.
2.  Open the `LoginRegistrationForm.sln` file in Visual Studio.
3.  Ensure the database is set up as described above and the connection string is correct.
4.  Build the solution (Build > Build Solution).
5.  Run the project (Debug > Start Debugging, or press F5).

## Usage

*   **Login Form (`Form1`):**
    *   Enter your username and password.
    *   Click the "LOGIN" button.
    *   You can toggle password visibility using the "Show Password" checkbox.
    *   If you don't have an account, click "Register here."
    *   Click 'X' to close the application.
*   **Signup Form (`Signup`):**
    *   Enter your email, a desired username, and a password.
    *   Click the "SIGNUP" button.
    *   Password visibility can also be toggled here.
    *   If you already have an account, click "Login here."
    *   Click 'X' to close the application.
*   **Main Form (`MainForm`):**
    *   This form appears after a successful login, welcoming the user.

## Screenshots

*(Optional: Add screenshots of your Login, Signup, and Main forms here. You can upload images to your GitHub repo and link them, e.g., `![Login Form](screenshots/login_form.png)`)*

## Known Issues / Limitations

*   **Plaintext Passwords:** Passwords are currently stored in plaintext in the database. This is **highly insecure** for a real application and should be replaced with strong password hashing (e.g., BCrypt).
*   **Basic Input Validation:** Input validation is minimal (checks for empty fields). More robust validation for email format, password complexity, etc., should be added.
*   **Hardcoded Connection String:** The database connection string is hardcoded. It's better to use `App.config` for configurability.
*   **Limited Error Details:** Database error messages shown to the user might be too technical.

## Future Enhancements

*   Implement password hashing.
*   Add more comprehensive input validation.
*   Move database logic to a separate Data Access Layer (DAL).
*   Implement a "Forgot Password" feature.
*   Add user roles and permissions.
*   Improve UI/UX design.

---
