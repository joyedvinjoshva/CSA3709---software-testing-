# Experiment 15: Test Plan - Inventory Management System

**Document ID:** TP-IMS-001 | **Version:** 1.0 | **Standard:** IEEE 829 (adapted) | **Course:** CSA37 Software Testing

## 1. Introduction
This plan defines the scope, test design techniques, execution strategy and completion criteria for testing the **Inventory Management System (IMS)** that tracks products, suppliers, purchases, stock, sales and reports.

### 1.1 Objectives
- Verify that all functional requirements are implemented correctly.
- Find defects early and report them with traceability.
- Validate non-functional qualities: performance, security, usability, compatibility.
- Provide objective exit criteria for release.

## 2. Test Scope
### 2.1 In scope
- Product SKU creation and validation
- Purchase order and GRN updating stock
- Sales/issue reducing stock; no negative stock
- Reorder level alerts
- Stock adjustment and warehouse transfer
- Valuation calculation
- Reports accuracy and export
- Role-based access
- Performance (bulk upload of 10,000 SKUs) and basic security

### 2.2 Out of scope
- Accounting software integration internals
- Barcode printer hardware
- Mobile app (separate plan)

## 3. Test Items
| Module | Description |
|---|---|
| Product Master | Add/edit/deactivate products, SKU, unit, reorder level |
| Supplier Management | Supplier details, purchase history |
| Purchase / GRN | Purchase orders, goods received notes, stock increase |
| Sales / Issue | Sales orders, stock decrease, invoices |
| Stock Control | Real-time stock, reorder alerts, adjustment, warehouse transfer |
| Valuation | FIFO / weighted-average valuation |
| Reports | Stock, low-stock, movement, valuation |
| Users and Roles | Admin, store keeper, sales, auditor |

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
| Tools | Selenium WebDriver, JUnit, Apache JMeter, Postman, Jira, SQL client |

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
| Stock mismatch due to concurrency | High | Concurrency/load tests; transaction rollback tests |
| Wrong valuation method | High | Hand-calculated oracle with FIFO/WAC data |
| Large data volume slows reports | Medium | JMeter performance tests on bulk data |
| Unstable test data | Medium | Scripted data refresh before each cycle |

## 11. Sample Test Cases
| TC ID | Feature | Test Steps | Expected Result | Priority |
|---|---|---|---|---|
| TC_INV_01 | Add product | Add product with unique SKU, qty 0, reorder level 10 | Product saved | High |
| TC_INV_02 | Duplicate SKU | Add product with existing SKU | Error 'SKU exists' | High |
| TC_INV_03 | GRN | Receive 100 units against PO | Stock +100; PO updated | High |
| TC_INV_04 | Sale | Sell 30 units from stock of 100 | Stock = 70; invoice created | High |
| TC_INV_05 | Insufficient stock | Sell 150 from stock of 100 | Error; stock unchanged | High |
| TC_INV_06 | Reorder alert | Reduce stock below reorder level | Low-stock alert generated | Medium |
| TC_INV_07 | Adjustment | Adjust stock -5, reason 'damaged' | Stock reduced; audit entry | Medium |
| TC_INV_08 | Transfer | Transfer 20 units between warehouses | W1 -20, W2 +20 | Medium |
| TC_INV_09 | Negative quantity | Enter -10 as purchase quantity | Validation error | High |
| TC_INV_10 | Valuation (FIFO) | Buy 10@Rs.5 then 10@Rs.7; sell 12 | Closing value = 8 x Rs.7 = Rs.56 | High |

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

