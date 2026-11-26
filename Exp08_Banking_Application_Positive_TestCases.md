# Case Study: Positive Test Scenarios and Test Cases - Banking Application

**Course:** CSA37 - Software Testing | **Programme:** Computer Science and Engineering | **Institute:** SIMATS Engineering

## 1. Aim
To identify and analyse the requirements of the **Banking Application (Net/Mobile Banking)** and to prepare **positive** test scenarios and test cases for the application.

## 2. System Overview
A net/mobile banking application allowing customers to log in securely, check balance and statements, transfer funds, pay bills, manage beneficiaries and cards.

**Actors:** Customer, Bank Admin, Payment Switch (NEFT/IMPS/UPI)

## 3. Requirement Analysis
| Req ID | Requirement | Description |
|---|---|---|
| R1 | Secure Login | Customer ID + password + OTP; lock after 3 failed attempts. |
| R2 | Balance & Mini-statement | Show current balance and last 10 transactions. |
| R3 | Fund Transfer | Transfer to registered beneficiary; amount <= balance and <= daily limit; OTP confirmation. |
| R4 | Beneficiary Management | Add (24h activation) / delete beneficiary after validating account number and IFSC. |
| R5 | Bill Payment | Pay utility bills from account; receipt generated. |
| R6 | Statement Download | Statement for selected date range (max 1 year) as PDF. |
| R7 | Card Management | Block/unblock card, change PIN. |
| R8 | Session & Security | Auto logout after 5 min inactivity; encrypted data; audit log. |
| R9 | Performance | Transaction response within 5 s; 99.9% availability. |

**Analysis notes:** every requirement is testable, uniquely identified and traceable to at least one test scenario. Where limits, time-outs or messages are not given, the values stated in the descriptions are assumed.

**Positive tests** use *valid* input and expected usage to check that the system does what the requirement says (the 'happy path').

## 4. Test Design Techniques Used
Equivalence partitioning, boundary value analysis, state-transition testing and error guessing.

## 5. Test Scenarios
| Scenario ID | Requirement | Test Scenario |
|---|---|---|
| TS_BANKP_01 | R1 | Login with valid credentials + OTP |
| TS_BANKP_02 | R2 | View balance |
| TS_BANKP_03 | R2 | View mini statement |
| TS_BANKP_04 | R3 | Transfer to registered beneficiary |
| TS_BANKP_05 | R3 | Transfer up to daily limit |
| TS_BANKP_06 | R4 | Add beneficiary |
| TS_BANKP_07 | R4 | Delete beneficiary |
| TS_BANKP_08 | R5 | Pay electricity bill |
| TS_BANKP_09 | R6 | Download 3-month statement |
| TS_BANKP_10 | R7 | Block debit card |
| TS_BANKP_11 | R7 | Change card PIN |
| TS_BANKP_12 | R8 | Auto logout after inactivity |

## 6. Test Cases
| TC ID | Req | Scenario | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|
| TC_BANKP_01 | R1 | Login with valid credentials + OTP | Enter ID, password; enter correct OTP | Valid customer | Account dashboard displayed | High |
| TC_BANKP_02 | R2 | View balance | Accounts > Balance | Valid account | Correct available balance displayed | High |
| TC_BANKP_03 | R2 | View mini statement | Open Mini Statement | - | Last 10 transactions in date order | High |
| TC_BANKP_04 | R3 | Transfer to registered beneficiary | Select beneficiary; amount 1000; confirm OTP | Amount 1000 (balance 5000) | Success; balance reduced by 1000; reference number generated | High |
| TC_BANKP_05 | R3 | Transfer up to daily limit | Transfer amount equal to daily limit | = limit | Transaction succeeds | Medium |
| TC_BANKP_06 | R4 | Add beneficiary | Enter name, valid account no., IFSC; Submit | Valid details | Beneficiary added; active after cooling period | Medium |
| TC_BANKP_07 | R4 | Delete beneficiary | Select; Delete; confirm | - | Beneficiary removed | Medium |
| TC_BANKP_08 | R5 | Pay electricity bill | Select biller; enter consumer no.; pay | Valid consumer number | Payment success; receipt generated | Medium |
| TC_BANKP_09 | R6 | Download 3-month statement | Choose range; Download PDF | Last 3 months | PDF with correct transactions | Medium |
| TC_BANKP_10 | R7 | Block debit card | Cards > Block; confirm OTP | Active card | Card status 'Blocked' | Medium |
| TC_BANKP_11 | R7 | Change card PIN | Enter old and new PIN | Valid PINs | PIN changed message | Medium |
| TC_BANKP_12 | R8 | Auto logout after inactivity | Login; idle 5 min | Idle 5 min | Session ends; login page displayed | Medium |

## 7. Requirement Traceability Matrix
| Req ID | Requirement | Test Cases |
|---|---|---|
| R1 | Secure Login | TC_BANKP_01 |
| R2 | Balance & Mini-statement | TC_BANKP_02, TC_BANKP_03 |
| R3 | Fund Transfer | TC_BANKP_04, TC_BANKP_05 |
| R4 | Beneficiary Management | TC_BANKP_06, TC_BANKP_07 |
| R5 | Bill Payment | TC_BANKP_08 |
| R6 | Statement Download | TC_BANKP_09 |
| R7 | Card Management | TC_BANKP_10, TC_BANKP_11 |
| R8 | Session & Security | TC_BANKP_12 |
| R9 | Performance | - |

## 8. Execution Template
| TC ID | Actual Result | Status (Pass/Fail) | Defect ID | Remarks |
|---|---|---|---|---|
| TC_BANKP_01 |  |  |  |  |
| TC_BANKP_02 |  |  |  |  |
| TC_BANKP_03 |  |  |  |  |

## 9. Conclusion
The requirements of the Banking Application were analysed and **12 positive test scenarios** with corresponding test cases were designed, covering the requirements with valid flows.
