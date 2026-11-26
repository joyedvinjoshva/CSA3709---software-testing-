# Case Study: Negative Test Scenarios and Test Cases - Railway Reservation System

**Course:** CSA37 - Software Testing | **Programme:** Computer Science and Engineering | **Institute:** SIMATS Engineering

## 1. Aim
To identify and analyse the requirements of the **Railway Reservation System** and to prepare **negative** test scenarios and test cases for the application.

## 2. System Overview
An online system to search trains, check seat availability, book/cancel tickets, pay online, and check PNR status.

**Actors:** Passenger, Railway Admin, Payment Gateway

## 3. Requirement Analysis
| Req ID | Requirement | Description |
|---|---|---|
| R1 | Registration & Login | Passenger registers and logs in to book tickets. |
| R2 | Train Search | Search by source, destination, date; shows trains, classes, fare, availability. |
| R3 | Booking | Enter 1-6 passengers (name, age, gender, berth pref); confirm; generate PNR. |
| R4 | Seat Allocation | Confirmed/RAC/Waiting list by availability; senior citizen quota. |
| R5 | Payment | Pay by card/UPI/net banking within 10 minutes of booking. |
| R6 | Cancellation & Refund | Cancel ticket; refund by time-based rules. |
| R7 | PNR Status | Show booking status for a valid 10-digit PNR. |
| R8 | Advance Reservation | Booking allowed up to 120 days before journey. |
| R9 | Performance | Handle peak (Tatkal) load; response < 5 s. |

**Analysis notes:** every requirement is testable, uniquely identified and traceable to at least one test scenario. Where limits, time-outs or messages are not given, the values stated in the descriptions are assumed.

**Negative tests** use *invalid, unexpected or boundary-violating* input or sequences to check that the system rejects them gracefully, with proper messages, without crashing, corrupting data or exposing security holes.

## 4. Test Design Techniques Used
Equivalence partitioning, boundary value analysis, state-transition testing and error guessing.

## 5. Test Scenarios
| Scenario ID | Requirement | Test Scenario |
|---|---|---|
| TS_RAILN_01 | R1 | Login with wrong password |
| TS_RAILN_02 | R2 | Same source and destination |
| TS_RAILN_03 | R2 | Past journey date |
| TS_RAILN_04 | R2 | Invalid station name |
| TS_RAILN_05 | R3 | Passenger name empty |
| TS_RAILN_06 | R3 | Age out of range |
| TS_RAILN_07 | R3 | More than 6 passengers |
| TS_RAILN_08 | R3 | Name with digits/symbols |
| TS_RAILN_09 | R5 | Payment after 10-min timeout |
| TS_RAILN_10 | R5 | Payment failure |
| TS_RAILN_11 | R6 | Cancel an already cancelled ticket |
| TS_RAILN_12 | R6 | Cancel after chart preparation |
| TS_RAILN_13 | R7 | PNR with 9 digits |
| TS_RAILN_14 | R7 | PNR with letters |
| TS_RAILN_15 | R8 | Book 121 days in advance |
| TS_RAILN_16 | R9 | Book when sold out |

## 6. Test Cases
| TC ID | Req | Scenario | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|
| TC_RAILN_01 | R1 | Login with wrong password | Enter wrong password | wrong | Error; not logged in | High |
| TC_RAILN_02 | R2 | Same source and destination | Select same station in both fields | Chennai - Chennai | Error 'Source and destination cannot be same' | High |
| TC_RAILN_03 | R2 | Past journey date | Select yesterday | Yesterday | Error 'Invalid date' | High |
| TC_RAILN_04 | R2 | Invalid station name | Type 'xyzabc' | xyzabc | 'No station found' | High |
| TC_RAILN_05 | R3 | Passenger name empty | Leave name blank | (blank) | Mandatory field error | Medium |
| TC_RAILN_06 | R3 | Age out of range | Enter age 0 / 150 | 0, 150 | Age validation error | Medium |
| TC_RAILN_07 | R3 | More than 6 passengers | Add 7th passenger | 7 | 'Maximum 6 passengers' error | Medium |
| TC_RAILN_08 | R3 | Name with digits/symbols | Name 'R@m123' | R@m123 | Name validation error | Medium |
| TC_RAILN_09 | R5 | Payment after 10-min timeout | Wait 11 min then pay | - | Session timed out; booking not confirmed | Medium |
| TC_RAILN_10 | R5 | Payment failure | Use declined card | Declined card | Payment failed; seats released; no ticket | Medium |
| TC_RAILN_11 | R6 | Cancel an already cancelled ticket | Cancel same PNR twice | Cancelled PNR | Error 'Ticket already cancelled' | Medium |
| TC_RAILN_12 | R6 | Cancel after chart preparation | Cancel after chart prepared | - | Not allowed / no refund as per rule | Medium |
| TC_RAILN_13 | R7 | PNR with 9 digits | Enter 123456789 | 123456789 | Invalid PNR error | Medium |
| TC_RAILN_14 | R7 | PNR with letters | Enter 'ABC1234567' | ABC1234567 | Invalid PNR error | Medium |
| TC_RAILN_15 | R8 | Book 121 days in advance | Select today + 121 | Day 121 | Error 'Booking not open for this date' | Medium |
| TC_RAILN_16 | R9 | Book when sold out | Select class with no seats and WL closed | Sold out | 'Booking not available' message | Medium |

## 7. Requirement Traceability Matrix
| Req ID | Requirement | Test Cases |
|---|---|---|
| R1 | Registration & Login | TC_RAILN_01 |
| R2 | Train Search | TC_RAILN_02, TC_RAILN_03, TC_RAILN_04 |
| R3 | Booking | TC_RAILN_05, TC_RAILN_06, TC_RAILN_07, TC_RAILN_08 |
| R4 | Seat Allocation | - |
| R5 | Payment | TC_RAILN_09, TC_RAILN_10 |
| R6 | Cancellation & Refund | TC_RAILN_11, TC_RAILN_12 |
| R7 | PNR Status | TC_RAILN_13, TC_RAILN_14 |
| R8 | Advance Reservation | TC_RAILN_15 |
| R9 | Performance | TC_RAILN_16 |

## 8. Execution Template
| TC ID | Actual Result | Status (Pass/Fail) | Defect ID | Remarks |
|---|---|---|---|---|
| TC_RAILN_01 |  |  |  |  |
| TC_RAILN_02 |  |  |  |  |
| TC_RAILN_03 |  |  |  |  |

## 9. Conclusion
The requirements of the Railway Reservation System were analysed and **16 negative test scenarios** with corresponding test cases were designed, covering the requirements with invalid input, boundary violations, security and error handling.
