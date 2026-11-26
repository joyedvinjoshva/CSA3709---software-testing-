# Experiment 10: Test Plan - Library Management System

**Document ID:** TP-LMS-001 | **Version:** 1.0 | **Standard:** IEEE 829 (adapted) | **Course:** CSA37 Software Testing

## 1. Introduction
This plan defines the approach to test the **Library Management System (LMS)** used by librarians and members to manage books, memberships, issue/return, fines, reservations and reports.

### 1.1 Objectives
- Verify that all functional requirements are implemented correctly.
- Find defects early and report them with traceability.
- Validate non-functional qualities: performance, security, usability, compatibility.
- Provide objective exit criteria for release.

## 2. Test Scope
### 2.1 In scope
- Login and role-based access
- Member registration and validation
- Book add/edit/delete and copy count
- Search and filters
- Issue, return, renew with limit rules
- Fine calculation and payment
- Reservation and notifications
- Reports and export
- Performance for 200 concurrent users and basic security

### 2.2 Out of scope
- Third-party e-mail/SMS gateway internals
- Barcode scanner hardware
- Data migration from legacy system

## 3. Test Items
| Module | Description |
|---|---|
| Member Management | Register, update, deactivate members |
| Book Catalogue | Add/edit/delete books, categories, copies |
| Search | By title/author/ISBN/category |
| Issue / Return | Issue up to 3 books for 14 days; return; renew |
| Fine Management | Rs.2/day after due date; payment |
| Reservation | Reserve issued books; notification |
| Reports | Issued, overdue, fine collection |
| Authentication | Librarian/Admin/Member roles |

## 4. Test Strategy and Approach
### 4.1 Test levels
| Level | Responsible | Focus |
|---|---|---|
| Unit testing | Developers | Methods/classes with JUnit (white-box: statement, branch, path coverage) |
| Integration testing | Developers + QA | Interfaces between modules, database, services |
| System testing | QA team | End-to-end functional and non-functional validation (black-box) |
| Acceptance testing (UAT) | Client / end users | Business scenarios, sign-off |
| Regression testing | QA team | Re-run affected and core cases after each fix/build; automated with Selenium |

### 4.2 Test design techniques
| Technique | Where applied |
|---|---|
| Equivalence partitioning | Input fields (valid/invalid classes) |
| Boundary value analysis | Numeric/date/length limits |
| Decision table testing | Business rules combinations |
| State transition testing | Status life cycles |
| Use-case testing | End-to-end user flows |
| Error guessing / exploratory | Experience-based and security probes |
| Structure-based (white-box) | Unit tests: statement, decision, condition coverage |

### 4.3 Types of testing
Functional, UI/usability, compatibility (Chrome, Firefox, Edge), performance/load (JMeter), security (authentication, authorisation, SQL injection, XSS), smoke, sanity, regression and exploratory testing.

## 5. Test Execution Strategy
- **Cycle 1:** smoke test of the build, then all High-priority cases.
- **Cycle 2:** full functional and integration cases; defects logged and retested.
- **Cycle 3:** regression, performance and security tests; UAT.
- A build is accepted only after a passing **smoke test**.
- Defects are logged in a tracker (Jira/Bugzilla) with severity and priority; daily triage.

### 5.1 Defect severity
| Severity | Meaning | Example |
|---|---|---|
| Critical | Crash / data loss / security breach | Cannot log in; wrong stock or money posted |
| High | Major feature broken, no workaround | Search returns nothing |
| Medium | Partly broken, workaround exists | Wrong sort order |
| Low | Cosmetic / minor | Typo, alignment |

## 6. Test Environment
| Item | Specification |
|---|---|
| Hardware | Client: i5, 8 GB RAM; Server: 4 vCPU, 16 GB RAM |
| Software | Windows 11/Ubuntu, Chrome/Firefox/Edge latest, MySQL/PostgreSQL, Java 17 |
| Test data | Masked production-like data plus generated boundary data |
| Tools | Selenium WebDriver, JUnit, Apache JMeter, Jira, Postman, JaCoCo |

## 7. Entry, Exit and Suspension Criteria
### Entry criteria
- Requirements approved and baselined; test cases reviewed.
- Build deployed to test environment and smoke test passed.
- Test data and user accounts ready.

### Exit (test completion) criteria
- 100% of planned test cases executed; at least 95% passed.
- No open Critical/High defects; Medium defects have an agreed plan.
- Requirement coverage 100% (traceability matrix); unit-test code coverage at least 80%.
- Performance targets met (e.g. 95% of requests under 3 s).
- Test summary report signed off.

### Suspension / resumption criteria
- Suspend if the build fails the smoke test, the environment is down, or a blocking defect stops more than 30% of test cases.
- Resume after the fix is verified and a new build is deployed.

## 8. Roles and Responsibilities
| Role | Responsibility |
|---|---|
| Test Manager | Planning, tracking, reporting, risk management |
| Test Lead | Design review, allocation, defect triage |
| Test Engineers | Write/execute test cases, log defects |
| Automation Engineer | Selenium/JMeter scripts, regression suite |
| Developers | Unit tests, defect fixes |
| Business Analyst / Client | Requirement clarification, UAT sign-off |

## 9. Schedule
| Activity | Duration | Deliverable |
|---|---|---|
| Test planning | 3 days | Test plan |
| Test case design | 7 days | Test cases, RTM |
| Environment and data setup | 3 days | Ready environment |
| Execution cycle 1 | 5 days | Daily status, defects |
| Execution cycle 2 | 7 days | Defect reports |
| Regression, performance, UAT | 5 days | Test summary report |

## 10. Risks and Mitigation
| Risk | Impact | Mitigation |
|---|---|---|
| Requirements change late | High | Change control; keep RTM updated |
| Incomplete test data for fines/dates | Medium | Date-shifted data sets; system clock stubs |
| Limited test environment time | Medium | Prioritise High-risk cases; automate regression |
| Defects in fine calculation | High | Boundary tests on due dates; decision tables |

## 11. Sample Test Cases
| TC ID | Feature | Test Steps | Expected Result | Priority |
|---|---|---|---|---|
| TC_LIB_01 | Login | Login as librarian with valid ID/password | Dashboard displayed | High |
| TC_LIB_02 | Issue book | Issue an available book to an active member | Issued; due = today+14; copies -1 | High |
| TC_LIB_03 | Issue limit | Issue 4th book to member holding 3 | Error 'Limit of 3 books reached' | High |
| TC_LIB_04 | Fine | Return a book 5 days late | Fine = Rs.10 shown | High |
| TC_LIB_05 | Return | Return an issued book on time | Returned; copies +1; no fine | High |
| TC_LIB_06 | Reserve | Reserve a book with zero copies | Reservation recorded; member notified later | Medium |
| TC_LIB_07 | Search | Search with partial title | Matching books listed | Medium |
| TC_LIB_08 | Expired member | Issue book to expired membership | Blocked with message | High |
| TC_LIB_09 | Duplicate ISBN | Add book with existing ISBN | Error / copy count incremented per rule | Medium |
| TC_LIB_10 | SQL injection | Enter ' OR 1=1-- in search | No data leak; input sanitised | High |

## 12. Test Deliverables
Test plan, test scenarios and cases, requirement traceability matrix, test data, automation scripts, defect reports, daily status reports, test summary report.

## 13. Metrics
Test case pass %, defect density, defect leakage, requirement coverage, execution progress, defect removal efficiency.

## 14. Approvals
| Name | Role | Signature | Date |
|---|---|---|---|
|  | Test Manager |  |  |
|  | Project Manager |  |  |
|  | Client Representative |  |  |

