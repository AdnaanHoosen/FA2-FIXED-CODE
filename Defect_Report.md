# **TASK 6: DEFECT REPORTING**

| **Bug ID** | **Module** | **Description** | **Severity** | **Priority** | **Status** | **Resolution** |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **BUG-001** | Login | Used `OR` logic gate instead of `AND`. Allowed access with only a password. | **Critical** | **P1** | **Closed** | Changed `||` to `&&` in `FrmLogin.cs`. |
| **BUG-002** | Marks Capture | Average calculation violated BODMAS rules. Only Subject 3 was divided by 3. | **High** | **P1** | **Closed** | Added parentheses to ensure sum is calculated before division. |
| **BUG-003** | Reports | Artificial delay of 4 seconds using `Thread.Sleep`. | **Medium** | **P2** | **Closed** | Commented out the `Thread.Sleep` command for instant performance. |
| **BUG-004** | Reports | Hardcoded average value (169) displayed incorrectly in Marks Report. | **High** | **P2** | **Closed** | Corrected hardcoded value to **74.33** to match report data. |
| **BUG-005** | Marks Capture | System crashes (`FormatException`) when non-numeric text is entered. | **High** | **P2** | **Open** | Identified as missing `double.TryParse` or `try-catch` blocks. |
