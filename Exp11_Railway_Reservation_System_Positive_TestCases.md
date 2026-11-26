# Case Study: Positive Test Scenarios and Test Cases - Railway Reservation System

**Course:** CSA37 - Software Testing | **Programme:** Computer Science and Engineering | **Institute:** SIMATS Engineering

## 1. Aim
To identify and analyse the requirements of the **Railway Reservation System** and to prepare **positive** test scenarios and test cases for the application.

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

**Positive tests** use *valid* input and expected usage to check that the system does what the requirement says (the 'happy path').

## 4. Test Design Techniques Used
Equivalence partitioning, boundary value analysis, state-transition testing and error guessing.

## 5. Test Scenarios
| Scenario ID | Requirement | Test Scenario |
|---|---|---|
| TS_RAILP_01 | R1 | Login with valid credentials |
| TS_RAILP_02 | R2 | Search trains between two stations |
| TS_RAILP_03 | R2 | Check availability for a class |
| TS_RAILP_04 | R3 | Book ticket for one passenger |
| TS_RAILP_05 | R3 | Book for 6 passengers |
| TS_RAILP_06 | R4 | Senior citizen quota |
| TS_RAILP_07 | R5 | Pay within time limit |
| TS_RAILP_08 | R6 | Cancel confirmed ticket |
| TS_RAILP_09 | R7 | Check PNR status |
| TS_RAILP_10 | R8 | Book on last allowed day |

## 6. Test Cases
| TC ID | Req | Scenario | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|
| TC_RAILP_01 | R1 | Login with valid credentials | Enter user ID and password | Valid | Home page in logged-in state | High |
| TC_RAILP_02 | R2 | Search trains between two stations | Enter source, destination, future date; Search | Chennai - Madurai, tomorrow | Trains with timings and fares listed | High |
| TC_RAILP_03 | R2 | Check availability for a class | Select train & class 3A | 3A | Availability / WL status displayed | High |
| TC_RAILP_04 | R3 | Book ticket for one passenger | Fill passenger details; Continue; Pay | Name, Age 30, M | Booking confirmed; PNR generated | High |
| TC_RAILP_05 | R3 | Book for 6 passengers | Add six valid passengers | 6 passengers | Booking confirmed for all six | Medium |
| TC_RAILP_06 | R4 | Senior citizen quota | Enter age 62 female | Age 62, F | Lower berth / concession applied as per rule | Medium |
| TC_RAILP_07 | R5 | Pay within time limit | Pay with valid card within 10 min | Valid card | Payment success; ticket sent by e-mail/SMS | Medium |
| TC_RAILP_08 | R6 | Cancel confirmed ticket | My Bookings > Cancel > Confirm | Confirmed PNR | Cancelled; refund shown per rule | Medium |
| TC_RAILP_09 | R7 | Check PNR status | Enter valid 10-digit PNR | 1234567890 | Booking and passenger status displayed | Medium |
| TC_RAILP_10 | R8 | Book on last allowed day | Select date = today + 120 | Day 120 | Booking allowed | Medium |

## 7. Requirement Traceability Matrix
| Req ID | Requirement | Test Cases |
|---|---|---|
| R1 | Registration & Login | TC_RAILP_01 |
| R2 | Train Search | TC_RAILP_02, TC_RAILP_03 |
| R3 | Booking | TC_RAILP_04, TC_RAILP_05 |
| R4 | Seat Allocation | TC_RAILP_06 |
| R5 | Payment | TC_RAILP_07 |
| R6 | Cancellation & Refund | TC_RAILP_08 |
| R7 | PNR Status | TC_RAILP_09 |
| R8 | Advance Reservation | TC_RAILP_10 |
| R9 | Performance | - |

## 8. Execution Template
| TC ID | Actual Result | Status (Pass/Fail) | Defect ID | Remarks |
|---|---|---|---|---|
| TC_RAILP_01 |  |  |  |  |
| TC_RAILP_02 |  |  |  |  |
| TC_RAILP_03 |  |  |  |  |

## 9. Conclusion
The requirements of the Railway Reservation System were analysed and **10 positive test scenarios** with corresponding test cases were designed, covering the requirements with valid flows.
