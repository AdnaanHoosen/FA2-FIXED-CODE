# 🎓 TASK 1: SOFTWARE TESTING STRATEGY DESIGN

**Course:** Software Testing Module  
**Project:** Umoja Learning Management System (ULMS) WinForms App  
**Institution:** CTU Training Solutions (PTY) Ltd  

---

## 1.1 Testing Objectives

### System Purpose
The **ULMS WinForms App** is a desktop-based management system designed to streamline academic administration. Its primary purpose is to allow staff to manage student identities, handle course enrollments, capture academic results (marks), and generate analytical reports through a secure, user-friendly interface.

### Testing Goals
*   **Reliability:** Ensure the application performs consistently under various user interactions.
*   **Data Integrity:** Verify that student and marks data are processed and stored accurately without corruption.
*   **Security:** Confirm that sensitive academic records are only accessible to authenticated users.
*   **User Experience (UX):** Ensure that the navigation flow (Login -> Dashboard -> Modules) is logical and error-free.

### Scope of Testing
*   **In-Scope:** All frontend forms (`FrmLogin`, `FrmDashboard`, `FrmStudentRegistration`, `FrmCourseEnrollment`, `FrmMarksCapture`, `FrmReports`), input validation logic, and session management (Login/Logout).
*   **Out-of-Scope:** Underlying Windows OS performance, network latency (unless a remote SQL server is used), and third-party hardware drivers.

---

## 1.2 Testing Types Identification

| Testing Type | Example / Application in ULMS |
| :--- | :--- |
| **Functional testing** | **Login Validation:** Verifying that entering correct credentials in `FrmLogin` successfully opens `FrmDashboard`. |
| **Input validation** | **Marks Entry:** Ensuring that `FrmMarksCapture` rejects non-numeric characters or values outside the 0–100 range. |
| **Integration testing** | **Course Allocation:** Verifying that a student registered in `FrmStudentRegistration` appears correctly in the dropdown list in `FrmCourseEnrollment`. |
| **Performance testing** | **Report Loading:** Measuring the system response time when retrieving and displaying data in `FrmReports` with a high volume of records. |
| **Usability testing** | **Navigation:** Ensuring that every sub-form (e.g., Registration) has a clear "Back" button to return to the Dashboard. |
| **Security testing** | **Authentication:** Verifying that the Dashboard cannot be accessed via direct instantiation if the `IsAuthenticated` flag is false. |

---

## 1.3 Testing Environment Setup

### Hardware Requirements
*   **Processor:** Intel Core i5 / AMD Ryzen 5 or higher.
*   **Memory (RAM):** 8GB minimum (16GB recommended for running Visual Studio simultaneously).
*   **Storage:** 500MB of free space for application binaries and test datasets.

### Software Requirements
*   **Operating System:** Windows 10 or Windows 11 (Desktop Environment).
*   **Framework:** .NET 10.0 Runtime.

### Tools & Setup
*   **IDE:** Visual Studio 2026 (recommended) or Visual Studio 2022.
*   **Database:** SQL Server (localdb) for simulated data storage.
*   **Test Data Sets:**
    *   `Valid_Students_CSV`: 50 records of valid student data for bulk registration tests.
    *   `Boundary_Marks_JSON`: Test cases for 0, 100, -1, and 101 to verify marks validation logic.
    *   `Security_BruteForce_List`: Set of incorrect passwords to test login lockout/error handling.
