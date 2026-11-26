# Case Study: Positive Test Scenarios and Test Cases - ARMS Portal

**Course:** CSA37 - Software Testing | **Programme:** Computer Science and Engineering | **Institute:** SIMATS Engineering

## 1. Aim
To identify and analyse the requirements of the **ARMS Portal (Academic Records / Resource Management System)** and to prepare **positive** test scenarios and test cases for the application.

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

**Positive tests** use *valid* input and expected usage to check that the system does what the requirement says (the 'happy path').

## 4. Test Design Techniques Used
Equivalence partitioning, boundary value analysis, state-transition testing and error guessing.

## 5. Test Scenarios
| Scenario ID | Requirement | Test Scenario |
|---|---|---|
| TS_ARMSP_01 | R1 | Login with valid student credentials |
| TS_ARMSP_02 | R1 | Login with valid faculty credentials |
| TS_ARMSP_03 | R2 | Logout from the portal |
| TS_ARMSP_04 | R3 | Change password with valid data |
| TS_ARMSP_05 | R4 | View attendance |
| TS_ARMSP_06 | R4 | Faculty marks attendance |
| TS_ARMSP_07 | R5 | View internal marks |
| TS_ARMSP_08 | R5 | Faculty enters valid marks |
| TS_ARMSP_09 | R6 | Register for a course in open window |
| TS_ARMSP_10 | R7 | Pay fee online |
| TS_ARMSP_11 | R8 | Edit allowed profile field |
| TS_ARMSP_12 | R9 | Page load time |

## 6. Test Cases
| TC ID | Req | Scenario | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|
| TC_ARMSP_01 | R1 | Login with valid student credentials | 1. Open ARMS login page 2. Enter valid ID & password 3. Click Login | ID: 192011001 / Pwd: Valid@123 | Student dashboard displayed with student's name | High |
| TC_ARMSP_02 | R1 | Login with valid faculty credentials | Enter valid faculty ID & password; Login | FAC1001 / Valid@123 | Faculty dashboard displayed | High |
| TC_ARMSP_03 | R2 | Logout from the portal | Login; click Logout | Valid session | Session ends, login page shown; Back button does not reopen dashboard | High |
| TC_ARMSP_04 | R3 | Change password with valid data | Profile > Change Password; enter current, new, confirm | Old: Valid@123, New: Newpass@456 | Success message; user can log in with new password | High |
| TC_ARMSP_05 | R4 | View attendance | Login as student; open Attendance | Valid student | Subject-wise attendance % displayed and matches records | Medium |
| TC_ARMSP_06 | R4 | Faculty marks attendance | Faculty opens class; marks present/absent; Submit | Class CSE-A | Attendance saved; student percentages update | Medium |
| TC_ARMSP_07 | R5 | View internal marks | Student opens Marks > Internal | Valid student | Marks for each subject displayed correctly | Medium |
| TC_ARMSP_08 | R5 | Faculty enters valid marks | Enter marks 0-100 for a student; Save | Marks = 85 | Marks saved and visible to student | Medium |
| TC_ARMSP_09 | R6 | Register for a course in open window | Select eligible course; Submit | Course CSA37, credits within limit | Registration confirmed; course in timetable | Medium |
| TC_ARMSP_10 | R7 | Pay fee online | Open Fees; select due; pay with valid card/UPI | Valid test payment | Payment success page and downloadable receipt | Medium |
| TC_ARMSP_11 | R8 | Edit allowed profile field | Profile > Edit phone; Save | Phone: 9876543210 | Profile updated with confirmation | Medium |
| TC_ARMSP_12 | R9 | Page load time | Open dashboard on normal network | Broadband | Dashboard loads within 3 seconds | Medium |

## 7. Requirement Traceability Matrix
| Req ID | Requirement | Test Cases |
|---|---|---|
| R1 | User Login | TC_ARMSP_01, TC_ARMSP_02 |
| R2 | Logout & Session | TC_ARMSP_03 |
| R3 | Password Management | TC_ARMSP_04 |
| R4 | Attendance | TC_ARMSP_05, TC_ARMSP_06 |
| R5 | Marks / Results | TC_ARMSP_07, TC_ARMSP_08 |
| R6 | Course Registration | TC_ARMSP_09 |
| R7 | Fee Payment | TC_ARMSP_10 |
| R8 | Profile | TC_ARMSP_11 |
| R9 | Security & Performance | TC_ARMSP_12 |

## 8. Execution Template
| TC ID | Actual Result | Status (Pass/Fail) | Defect ID | Remarks |
|---|---|---|---|---|
| TC_ARMSP_01 |  |  |  |  |
| TC_ARMSP_02 |  |  |  |  |
| TC_ARMSP_03 |  |  |  |  |

## 9. Conclusion
The requirements of the ARMS Portal were analysed and **12 positive test scenarios** with corresponding test cases were designed, covering the requirements with valid flows.
