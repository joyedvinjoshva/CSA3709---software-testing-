# Case Study: Negative Test Scenarios and Test Cases - Banking Application

**Course:** CSA37 - Software Testing | **Programme:** Computer Science and Engineering | **Institute:** SIMATS Engineering

## 1. Aim
To identify and analyse the requirements of the **Banking Application (Net/Mobile Banking)** and to prepare **negative** test scenarios and test cases for the application.

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

**Negative tests** use *invalid, unexpected or boundary-violating* input or sequences to check that the system rejects them gracefully, with proper messages, without crashing, corrupting data or exposing security holes.

## 4. Test Design Techniques Used
Equivalence partitioning, boundary value analysis, state-transition testing and error guessing.

## 5. Test Scenarios
| Scenario ID | Requirement | Test Scenario |
|---|---|---|
| TS_BANKN_01 | R1 | Wrong password |
| TS_BANKN_02 | R1 | Account locks after 3 failures |
| TS_BANKN_03 | R1 | Wrong OTP |
| TS_BANKN_04 | R1 | Expired OTP |
| TS_BANKN_05 | R3 | Amount exceeds balance |
| TS_BANKN_06 | R3 | Amount above daily limit |
| TS_BANKN_07 | R3 | Zero or negative amount |
| TS_BANKN_08 | R3 | Non-numeric amount |
| TS_BANKN_09 | R3 | Non-activated beneficiary |
| TS_BANKN_10 | R3 | Double-click Submit |
| TS_BANKN_11 | R4 | Add beneficiary with invalid IFSC |
| TS_BANKN_12 | R4 | Short account number |
| TS_BANKN_13 | R5 | Bill payment with invalid consumer number |
| TS_BANKN_14 | R6 | Statement range over 1 year |
| TS_BANKN_15 | R6 | From-date after to-date |
| TS_BANKN_16 | R7 | Change PIN with wrong old PIN |
| TS_BANKN_17 | R8 | Back button after logout |

## 6. Test Cases
| TC ID | Req | Scenario | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|
| TC_BANKN_01 | R1 | Wrong password | Enter wrong password | wrong | Error; attempt counter incremented | High |
| TC_BANKN_02 | R1 | Account locks after 3 failures | Wrong password 3 times | x3 | Account locked; contact-bank message | High |
| TC_BANKN_03 | R1 | Wrong OTP | Enter incorrect OTP | 123456 | Login denied; limited retries | High |
| TC_BANKN_04 | R1 | Expired OTP | Enter OTP after expiry | - | 'OTP expired' error | High |
| TC_BANKN_05 | R3 | Amount exceeds balance | Transfer 10000 when balance 5000 | 10000 | Error 'Insufficient funds'; no debit | Medium |
| TC_BANKN_06 | R3 | Amount above daily limit | Amount greater than daily limit | > limit | Limit error; no debit | Medium |
| TC_BANKN_07 | R3 | Zero or negative amount | Enter 0 / -500 | 0, -500 | Validation error | Medium |
| TC_BANKN_08 | R3 | Non-numeric amount | Enter 'abc' | abc | Validation error | Medium |
| TC_BANKN_09 | R3 | Non-activated beneficiary | Transfer within cooling period | New beneficiary | Transfer blocked with message | Medium |
| TC_BANKN_10 | R3 | Double-click Submit | Click Confirm twice quickly | - | Only one debit; duplicate prevented | Medium |
| TC_BANKN_11 | R4 | Add beneficiary with invalid IFSC | Enter wrong IFSC | ABCD0000 | IFSC validation error | Medium |
| TC_BANKN_12 | R4 | Short account number | Enter 5-digit account number | 12345 | Validation error | Medium |
| TC_BANKN_13 | R5 | Bill payment with invalid consumer number | Enter wrong consumer id | 000 | 'Invalid consumer'; no debit | Medium |
| TC_BANKN_14 | R6 | Statement range over 1 year | Pick 18-month range | 18 months | Range error message | Medium |
| TC_BANKN_15 | R6 | From-date after to-date | From > To | - | Date validation error | Medium |
| TC_BANKN_16 | R7 | Change PIN with wrong old PIN | Enter incorrect old PIN | - | PIN change denied | Medium |
| TC_BANKN_17 | R8 | Back button after logout | Logout; press Back | - | Login page; no account data visible | Medium |

## 7. Requirement Traceability Matrix
| Req ID | Requirement | Test Cases |
|---|---|---|
| R1 | Secure Login | TC_BANKN_01, TC_BANKN_02, TC_BANKN_03, TC_BANKN_04 |
| R2 | Balance & Mini-statement | - |
| R3 | Fund Transfer | TC_BANKN_05, TC_BANKN_06, TC_BANKN_07, TC_BANKN_08, TC_BANKN_09, TC_BANKN_10 |
| R4 | Beneficiary Management | TC_BANKN_11, TC_BANKN_12 |
| R5 | Bill Payment | TC_BANKN_13 |
| R6 | Statement Download | TC_BANKN_14, TC_BANKN_15 |
| R7 | Card Management | TC_BANKN_16 |
| R8 | Session & Security | TC_BANKN_17 |
| R9 | Performance | - |

## 8. Execution Template
| TC ID | Actual Result | Status (Pass/Fail) | Defect ID | Remarks |
|---|---|---|---|---|
| TC_BANKN_01 |  |  |  |  |
| TC_BANKN_02 |  |  |  |  |
| TC_BANKN_03 |  |  |  |  |

## 9. Conclusion
The requirements of the Banking Application were analysed and **17 negative test scenarios** with corresponding test cases were designed, covering the requirements with invalid input, boundary violations, security and error handling.
