# Case Study: Negative Test Scenarios and Test Cases - Online Examination System

**Course:** CSA37 - Software Testing | **Programme:** Computer Science and Engineering | **Institute:** SIMATS Engineering

## 1. Aim
To identify and analyse the requirements of the **Online Examination System** and to prepare **negative** test scenarios and test cases for the application.

## 2. System Overview
A web application for timed online exams: faculty create question banks and exams, students attempt exams under a timer, followed by auto-evaluation and result publishing.

**Actors:** Student, Faculty/Examiner, Administrator

## 3. Requirement Analysis
| Req ID | Requirement | Description |
|---|---|---|
| R1 | Login & Authentication | Student logs in with registration number and password. |
| R2 | Exam Scheduling | Exam startable only within the scheduled window. |
| R3 | Question Delivery | Questions shown with navigation; options randomised. |
| R4 | Timer | Countdown timer; auto-submit when time ends. |
| R5 | Answer Saving | Answers autosaved; can change before submit. |
| R6 | Submission & Evaluation | Manual/auto submit; automatic scoring; negative marking as configured. |
| R7 | Result Publishing | Result visible only after faculty publishes. |
| R8 | Anti-malpractice | Single active session; tab-switch warnings; copy/paste disabled. |
| R9 | Question Bank | Faculty adds/edits/deletes questions with options and correct answer. |

**Analysis notes:** every requirement is testable, uniquely identified and traceable to at least one test scenario. Where limits, time-outs or messages are not given, the values stated in the descriptions are assumed.

**Negative tests** use *invalid, unexpected or boundary-violating* input or sequences to check that the system rejects them gracefully, with proper messages, without crashing, corrupting data or exposing security holes.

## 4. Test Design Techniques Used
Equivalence partitioning, boundary value analysis, state-transition testing and error guessing.

## 5. Test Scenarios
| Scenario ID | Requirement | Test Scenario |
|---|---|---|
| TS_EXAMN_01 | R1 | Login with wrong password |
| TS_EXAMN_02 | R1 | Concurrent login from second device |
| TS_EXAMN_03 | R2 | Start exam before scheduled time |
| TS_EXAMN_04 | R2 | Start exam after window closed |
| TS_EXAMN_05 | R2 | Re-attempt after submission |
| TS_EXAMN_06 | R3 | Direct question URL without login |
| TS_EXAMN_07 | R4 | Change system clock to extend time |
| TS_EXAMN_08 | R5 | Network loss during exam |
| TS_EXAMN_09 | R6 | Submit with no answers |
| TS_EXAMN_10 | R8 | Switch browser tab |
| TS_EXAMN_11 | R8 | Copy/paste question text |
| TS_EXAMN_12 | R7 | View result before publishing |
| TS_EXAMN_13 | R9 | Add question without correct answer |
| TS_EXAMN_14 | R9 | Add question with duplicate options |
| TS_EXAMN_15 | R9 | Student opens faculty question bank URL |

## 6. Test Cases
| TC ID | Req | Scenario | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|
| TC_EXAMN_01 | R1 | Login with wrong password | Enter wrong password | wrong | Error; no login | High |
| TC_EXAMN_02 | R1 | Concurrent login from second device | Login same user on 2 devices | - | First session terminated / second denied | High |
| TC_EXAMN_03 | R2 | Start exam before scheduled time | Click Start early | T-10 min | Start disabled / 'Exam not started' | High |
| TC_EXAMN_04 | R2 | Start exam after window closed | Click Start after end time | After end | 'Exam closed' message | High |
| TC_EXAMN_05 | R2 | Re-attempt after submission | Open submitted exam again | - | Not allowed; already submitted | Medium |
| TC_EXAMN_06 | R3 | Direct question URL without login | Paste question URL in new session | - | Redirected to login | Medium |
| TC_EXAMN_07 | R4 | Change system clock to extend time | Modify device time | - | Timer is server-side; no extra time | Medium |
| TC_EXAMN_08 | R5 | Network loss during exam | Disconnect then reconnect | 30 s outage | Answers preserved; correct remaining time | Medium |
| TC_EXAMN_09 | R6 | Submit with no answers | Submit immediately | - | Warning about unanswered; score 0 if confirmed | Medium |
| TC_EXAMN_10 | R8 | Switch browser tab | Open another tab | - | Warning shown; count logged; auto-submit after limit | Medium |
| TC_EXAMN_11 | R8 | Copy/paste question text | Press Ctrl+C / right-click | - | Action blocked | Medium |
| TC_EXAMN_12 | R7 | View result before publishing | Open Results early | - | 'Result not published' message | Medium |
| TC_EXAMN_13 | R9 | Add question without correct answer | Save without selecting key | - | Validation error | Medium |
| TC_EXAMN_14 | R9 | Add question with duplicate options | Two identical options | A=B | Validation error | Medium |
| TC_EXAMN_15 | R9 | Student opens faculty question bank URL | Edit URL | Role = student | Access denied | Medium |

## 7. Requirement Traceability Matrix
| Req ID | Requirement | Test Cases |
|---|---|---|
| R1 | Login & Authentication | TC_EXAMN_01, TC_EXAMN_02 |
| R2 | Exam Scheduling | TC_EXAMN_03, TC_EXAMN_04, TC_EXAMN_05 |
| R3 | Question Delivery | TC_EXAMN_06 |
| R4 | Timer | TC_EXAMN_07 |
| R5 | Answer Saving | TC_EXAMN_08 |
| R6 | Submission & Evaluation | TC_EXAMN_09 |
| R7 | Result Publishing | TC_EXAMN_12 |
| R8 | Anti-malpractice | TC_EXAMN_10, TC_EXAMN_11 |
| R9 | Question Bank | TC_EXAMN_13, TC_EXAMN_14, TC_EXAMN_15 |

## 8. Execution Template
| TC ID | Actual Result | Status (Pass/Fail) | Defect ID | Remarks |
|---|---|---|---|---|
| TC_EXAMN_01 |  |  |  |  |
| TC_EXAMN_02 |  |  |  |  |
| TC_EXAMN_03 |  |  |  |  |

## 9. Conclusion
The requirements of the Online Examination System were analysed and **15 negative test scenarios** with corresponding test cases were designed, covering the requirements with invalid input, boundary violations, security and error handling.
