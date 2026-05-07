# **TASK 2: TEST CASE DESIGN**

**Project:** ULMS WinForms App Client  
**Module:** Software Testing  
**Total Test Cases:** 15  

---

## **2.1 Feature: Student Login Validation**

| **Test Case ID** | **Description** | **Input** | **Expected Output** | **Actual Output** | **Status** |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-LOGIN-01** | Verify login with valid administrative credentials. | Username: **admin**<br>Password: **1234** | "Login Successful!" and redirect to Dashboard. | "Login Successful!" | **PASS** |
| **TC-LOGIN-02** | Verify login failure with invalid username. | Username: **wronguser**<br>Password: **1234** | "Invalid login credentials." message box. | "Invalid login credentials." | **PASS** |
| **TC-LOGIN-03** | Verify login failure with empty fields. | Username: [Empty]<br>Password: [Empty] | "Invalid login credentials." message box. | "Invalid login credentials." | **PASS** |
| **TC-LOGIN-04** | **Security Loophole:** Verify if only the password field grants access. | Username: **unknown**<br>Password: **1234** | Should fail (Expected), but code allows it via `OR` logic. | "Login Successful!" | **FAIL** |
| **TC-LOGIN-05** | **Case Sensitivity:** Verify if username is case sensitive. | Username: **ADMIN**<br>Password: **1234** | Should fail if strictly lowercase "admin" is expected. | "Login Successful!" | **FAIL** |

---

## **2.2 Feature: Course Enrollment**

| **Test Case ID** | **Description** | **Input** | **Expected Output** | **Actual Output** | **Status** |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-ENROLL-01** | Verify standard enrollment with all fields populated. | ID: **STU001**<br>Name: **John Doe**<br>Course: **Software Eng** | Enrollment success message displayed in output. | "Enrollment completed successfully!" | **PASS** |
| **TC-ENROLL-02** | Verify behavior when course selection is missing. | ID: **STU002**<br>Name: **Jane Smith**<br>Course: [None] | System should prompt to select a course. | "Enrollment completed successfully!" | **FAIL** |
| **TC-ENROLL-03** | **Duplicate Check:** Verify if the same student can enroll twice. | ID: **STU001**<br>Name: **John Doe**<br>Course: **Software Eng** | System should block duplicate enrollment records. | "Enrollment completed successfully!" | **FAIL** |

---

## **2.3 Feature: Marks Capture & Average Calculation**

| **Test Case ID** | **Description** | **Input** | **Expected Output** | **Actual Output** | **Status** |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-MARKS-01** | **Numeric Validation:** Verify system response to letters. | Subject 1: **"fail"** | System should prevent crash via error handling. | System Crash (FormatException) | **FAIL** |
| **TC-MARKS-02** | **Boundary Test:** Verify average for passing marks. | Sub1: **50**, Sub2: **50**, Sub3: **50** | Average: **50**<br>Status: **"PASS"** | Average: 116.66 | **FAIL** |
| **TC-MARKS-03** | **Logic Accuracy:** Verify operator precedence (BODMAS). | Sub1: **10**, Sub2: **10**, Sub3: **10** | Average: **10** | Average: 23.33 | **FAIL** |
| **TC-MARKS-04** | **Negative Input:** Verify handling of negative marks. | Sub1: **-10**, Sub2: **50**, Sub3: **50** | System should reject negative values. | Average: 12.33 | **FAIL** |
| **TC-MARKS-05** | **Zero Value Test:** Verify calculation with zero marks. | Sub1: **0**, Sub2: **0**, Sub3: **0** | Average: **0**<br>Status: **"FAIL"** | Average: 0 | **PASS** |

---

## **2.4 Feature: Report Generation**

| **Test Case ID** | **Description** | **Input** | **Expected Output** | **Actual Output** | **Status** |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-REPORT-01** | **Output Correctness:** Verify "Marks Report" data accuracy. | Type: **Marks Report** | Average in report must be (78+65+80)/3 = **74.3**. | "Average: 169" | **FAIL** |
| **TC-REPORT-02** | **Empty Selection:** Verify report when no type is selected. | Type: [Empty] | Message: "No report type selected." | "No report type selected." | **PASS** |
