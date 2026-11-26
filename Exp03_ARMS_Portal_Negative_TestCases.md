# Case Study: Negative Test Scenarios and Test Cases - ARMS Portal

**Course:** CSA37 - Software Testing | **Programme:** Computer Science and Engineering | **Institute:** SIMATS Engineering

## 1. Aim
To identify and analyse the requirements of the **ARMS Portal (Academic Records / Resource Management System)** and to prepare **negative** test scenarios and test cases for the application.

## 2. System Overview
The ARMS portal is the web application through which students, faculty and administrators manage academic activity: login, profile, attendance, internal/semester marks, timetable, course registration, fee payment and requests. (Adapt module names to the exact ARMS version used in your lab.)

**Actors:** Student, Faculty, Administrator

## 3. Requirement Analysis
| Req ID | Requirement | Description |
|---|---|---|
| R1 | User Login | Registered users log in with a valid user ID and password; role decides the dashboard. |
| R2 | Logout & Session | Users can log out; session expires after inactivity (e.g., 15 min). |
| R3 | Password Management | Users can change/reset password; new password must meet policy (min 8 chars, letter+digit+special). |
| R4 | Attendance | Student views subject-wise attendance %; faculty marks attendance. |
| R5 | Marks / Results | Student views internal and semester marks; faculty enters marks (0-100). |
| R6 | Course Registration | Student registers for courses within the open window and credit limit. |
| R7 | Fee Payment | Student views dues and pays online; receipt generated. |
| R8 | Profile | User views/edits permitted profile fields (phone, email, address). |
| R9 | Security & Performance | Account locks after 5 failed attempts; pages load within 3 s; HTTPS. |

**Analysis notes:** every requirement is testable, uniquely identified and traceable to at least one test scenario. Where limits, time-outs or messages are not given, the values stated in the descriptions are assumed.

**Negative tests** use *invalid, unexpected or boundary-violating* input or sequences to check that the system rejects them gracefully, with proper messages, without crashing, corrupting data or exposing security holes.

## 4. Test Design Techniques Used
Equivalence partitioning, boundary value analysis, state-transition testing and error guessing.

## 5. Test Scenarios
| Scenario ID | Requirement | Test Scenario |
|---|---|---|
| TS_ARMSN_01 | R1 | Login with wrong password |
| TS_ARMSN_02 | R1 | Login with unregistered ID |
| TS_ARMSN_03 | R1 | Login with empty fields |
| TS_ARMSN_04 | R1 | Login with only spaces |
| TS_ARMSN_05 | R1 | SQL injection in login |
| TS_ARMSN_06 | R9 | Account lock after 5 failed attempts |
| TS_ARMSN_07 | R2 | Session timeout |
| TS_ARMSN_08 | R2 | Access dashboard URL without login |
| TS_ARMSN_09 | R3 | Change password - mismatched confirmation |
| TS_ARMSN_10 | R3 | Change password - weak password |
| TS_ARMSN_11 | R5 | Faculty enters marks above 100 |
| TS_ARMSN_12 | R5 | Faculty enters non-numeric marks |
| TS_ARMSN_13 | R6 | Register beyond credit limit |
| TS_ARMSN_14 | R6 | Register after window closed |
| TS_ARMSN_15 | R7 | Payment with invalid card |
| TS_ARMSN_16 | R8 | Profile - invalid email format |
| TS_ARMSN_17 | R4 | Student opens faculty attendance page |

## 6. Test Cases
| TC ID | Req | Scenario | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|
| TC_ARMSN_01 | R1 | Login with wrong password | Enter valid ID, wrong password; Login | 192011001 / wrong | Error 'Invalid credentials'; no login | High |
| TC_ARMSN_02 | R1 | Login with unregistered ID | Enter unknown ID; Login | 999999999 / Valid@123 | Error 'Invalid credentials' | High |
| TC_ARMSN_03 | R1 | Login with empty fields | Leave ID and password blank; Login | (blank) | Validation 'ID and password required' | High |
| TC_ARMSN_04 | R1 | Login with only spaces | Enter spaces in both fields | '   ' / '   ' | Validation error; login rejected | High |
| TC_ARMSN_05 | R1 | SQL injection in login | Enter ' OR '1'='1 in ID field | ID: ' OR '1'='1 / any | Login rejected; input sanitised; no DB error shown | Medium |
| TC_ARMSN_06 | R9 | Account lock after 5 failed attempts | Wrong password 5 times, then correct password | Valid ID + wrong x5 | Account locked; correct password also refused until unlock | Medium |
| TC_ARMSN_07 | R2 | Session timeout | Login; idle > 15 min; click any link | Idle 16 min | Redirected to login with 'session expired' | Medium |
| TC_ARMSN_08 | R2 | Access dashboard URL without login | Paste dashboard URL in a new browser | Direct URL | Redirected to login page | Medium |
| TC_ARMSN_09 | R3 | Change password - mismatched confirmation | Enter different new and confirm | New: A@12345, Confirm: B@12345 | Error 'Passwords do not match' | Medium |
| TC_ARMSN_10 | R3 | Change password - weak password | New password 'abc' | abc | Error showing password policy | Medium |
| TC_ARMSN_11 | R5 | Faculty enters marks above 100 | Enter 150; Save | Marks = 150 | Validation error; not saved | Medium |
| TC_ARMSN_12 | R5 | Faculty enters non-numeric marks | Enter 'abc'; Save | Marks = abc | Validation error; not saved | Medium |
| TC_ARMSN_13 | R6 | Register beyond credit limit | Select courses exceeding limit; Submit | Credits > max | Error 'Credit limit exceeded' | Medium |
| TC_ARMSN_14 | R6 | Register after window closed | Open registration after deadline | Date > deadline | Registration disabled / error message | Medium |
| TC_ARMSN_15 | R7 | Payment with invalid card | Pay with invalid/expired card | 4111 1111 1111 1112 | Payment fails; fee status remains 'Due' | Medium |
| TC_ARMSN_16 | R8 | Profile - invalid email format | Enter 'abc@' in email; Save | abc@ | Validation error; not saved | Medium |
| TC_ARMSN_17 | R4 | Student opens faculty attendance page | Student edits URL to faculty page | Role = student | Access denied (403) / redirect | Medium |

## 7. Requirement Traceability Matrix
| Req ID | Requirement | Test Cases |
|---|---|---|
| R1 | User Login | TC_ARMSN_01, TC_ARMSN_02, TC_ARMSN_03, TC_ARMSN_04, TC_ARMSN_05 |
| R2 | Logout & Session | TC_ARMSN_07, TC_ARMSN_08 |
| R3 | Password Management | TC_ARMSN_09, TC_ARMSN_10 |
| R4 | Attendance | TC_ARMSN_17 |
| R5 | Marks / Results | TC_ARMSN_11, TC_ARMSN_12 |
| R6 | Course Registration | TC_ARMSN_13, TC_ARMSN_14 |
| R7 | Fee Payment | TC_ARMSN_15 |
| R8 | Profile | TC_ARMSN_16 |
| R9 | Security & Performance | TC_ARMSN_06 |

## 8. Execution Template
| TC ID | Actual Result | Status (Pass/Fail) | Defect ID | Remarks |
|---|---|---|---|---|
| TC_ARMSN_01 |  |  |  |  |
| TC_ARMSN_02 |  |  |  |  |
| TC_ARMSN_03 |  |  |  |  |

## 9. Conclusion
The requirements of the ARMS Portal were analysed and **17 negative test scenarios** with corresponding test cases were designed, covering the requirements with invalid input, boundary violations, security and error handling.
