# Case Study: Positive Test Scenarios and Test Cases - Online Examination System

**Course:** CSA37 - Software Testing | **Programme:** Computer Science and Engineering | **Institute:** SIMATS Engineering

## 1. Aim
To identify and analyse the requirements of the **Online Examination System** and to prepare **positive** test scenarios and test cases for the application.

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

**Positive tests** use *valid* input and expected usage to check that the system does what the requirement says (the 'happy path').

## 4. Test Design Techniques Used
Equivalence partitioning, boundary value analysis, state-transition testing and error guessing.

## 5. Test Scenarios
| Scenario ID | Requirement | Test Scenario |
|---|---|---|
| TS_EXAMP_01 | R1 | Login with valid credentials |
| TS_EXAMP_02 | R2 | Start exam in scheduled window |
| TS_EXAMP_03 | R3 | Navigate between questions |
| TS_EXAMP_04 | R3 | Options are shuffled |
| TS_EXAMP_05 | R4 | Timer counts down |
| TS_EXAMP_06 | R4 | Auto-submit on timeout |
| TS_EXAMP_07 | R5 | Answer autosave on refresh |
| TS_EXAMP_08 | R6 | Manual submit |
| TS_EXAMP_09 | R6 | Correct scoring |
| TS_EXAMP_10 | R6 | Negative marking applied |
| TS_EXAMP_11 | R7 | View result after publishing |
| TS_EXAMP_12 | R9 | Faculty adds a question |

## 6. Test Cases
| TC ID | Req | Scenario | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|
| TC_EXAMP_01 | R1 | Login with valid credentials | Enter reg. number & password | Valid student | Dashboard with scheduled exams | High |
| TC_EXAMP_02 | R2 | Start exam in scheduled window | Click Start Exam at valid time | Within window | Instructions then first question shown | High |
| TC_EXAMP_03 | R3 | Navigate between questions | Click Next / Previous / palette | - | Correct question shown; earlier answers retained | High |
| TC_EXAMP_04 | R3 | Options are shuffled | Two students start same exam | - | Option order differs; correct mapping preserved | High |
| TC_EXAMP_05 | R4 | Timer counts down | Observe timer | 60-minute exam | Decrements every second accurately | Medium |
| TC_EXAMP_06 | R4 | Auto-submit on timeout | Wait until timer reaches 00:00 | - | Exam auto-submitted with saved answers | Medium |
| TC_EXAMP_07 | R5 | Answer autosave on refresh | Select answer; refresh browser | - | Selected answer still shown | Medium |
| TC_EXAMP_08 | R6 | Manual submit | Click Submit; confirm | - | Confirmation; exam locked | Medium |
| TC_EXAMP_09 | R6 | Correct scoring | Answer 8 of 10 correctly (1 mark each) | 8 correct | Score = 8/10 | Medium |
| TC_EXAMP_10 | R6 | Negative marking applied | 2 wrong answers at -0.25 each | 2 wrong | Score reduced by 0.5 | Medium |
| TC_EXAMP_11 | R7 | View result after publishing | Open Results after publish | - | Score and breakdown displayed | Medium |
| TC_EXAMP_12 | R9 | Faculty adds a question | Add question, 4 options, mark correct; Save | Valid question | Saved and available in bank | Medium |

## 7. Requirement Traceability Matrix
| Req ID | Requirement | Test Cases |
|---|---|---|
| R1 | Login & Authentication | TC_EXAMP_01 |
| R2 | Exam Scheduling | TC_EXAMP_02 |
| R3 | Question Delivery | TC_EXAMP_03, TC_EXAMP_04 |
| R4 | Timer | TC_EXAMP_05, TC_EXAMP_06 |
| R5 | Answer Saving | TC_EXAMP_07 |
| R6 | Submission & Evaluation | TC_EXAMP_08, TC_EXAMP_09, TC_EXAMP_10 |
| R7 | Result Publishing | TC_EXAMP_11 |
| R8 | Anti-malpractice | - |
| R9 | Question Bank | TC_EXAMP_12 |

## 8. Execution Template
| TC ID | Actual Result | Status (Pass/Fail) | Defect ID | Remarks |
|---|---|---|---|---|
| TC_EXAMP_01 |  |  |  |  |
| TC_EXAMP_02 |  |  |  |  |
| TC_EXAMP_03 |  |  |  |  |

## 9. Conclusion
The requirements of the Online Examination System were analysed and **12 positive test scenarios** with corresponding test cases were designed, covering the requirements with valid flows.
