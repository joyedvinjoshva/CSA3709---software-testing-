# Case Study: Negative Test Scenarios and Test Cases - Food Delivery Application

**Course:** CSA37 - Software Testing | **Programme:** Computer Science and Engineering | **Institute:** SIMATS Engineering

## 1. Aim
To identify and analyse the requirements of the **Food Delivery Application** and to prepare **negative** test scenarios and test cases for the application.

## 2. System Overview
A mobile/web application where users discover restaurants, order food, pay online and track delivery in real time; restaurants accept orders and delivery partners fulfil them.

**Actors:** Customer, Restaurant, Delivery Partner, Admin

## 3. Requirement Analysis
| Req ID | Requirement | Description |
|---|---|---|
| R1 | Sign-up/Login (OTP) | Register/login using mobile number + OTP or email/password. |
| R2 | Location & Search | Detect/enter location; search restaurants/dishes; filters (veg, rating, time). |
| R3 | Menu & Cart | View menu, customise items, add to cart; cart holds items of one restaurant. |
| R4 | Offers & Coupons | Apply valid coupons; discount subject to minimum order value. |
| R5 | Payment | UPI, cards, wallet, COD; failed payment retried safely. |
| R6 | Order Tracking | Live status placed > preparing > picked up > delivered, with ETA. |
| R7 | Cancellation & Refund | Cancel before restaurant accepts; refund to source. |
| R8 | Ratings & Reviews | Rate restaurant and delivery after delivery. |
| R9 | Non-functional | Serviceability check, response < 3 s, secure payments. |

**Analysis notes:** every requirement is testable, uniquely identified and traceable to at least one test scenario. Where limits, time-outs or messages are not given, the values stated in the descriptions are assumed.

**Negative tests** use *invalid, unexpected or boundary-violating* input or sequences to check that the system rejects them gracefully, with proper messages, without crashing, corrupting data or exposing security holes.

## 4. Test Design Techniques Used
Equivalence partitioning, boundary value analysis, state-transition testing and error guessing.

## 5. Test Scenarios
| Scenario ID | Requirement | Test Scenario |
|---|---|---|
| TS_FOODN_01 | R1 | Wrong OTP |
| TS_FOODN_02 | R1 | Expired OTP |
| TS_FOODN_03 | R1 | Invalid mobile number |
| TS_FOODN_04 | R2 | Location outside service area |
| TS_FOODN_05 | R2 | Search nonsense text |
| TS_FOODN_06 | R3 | Items from two restaurants |
| TS_FOODN_07 | R3 | Order from closed restaurant |
| TS_FOODN_08 | R3 | Quantity beyond limit |
| TS_FOODN_09 | R4 | Coupon below minimum order |
| TS_FOODN_10 | R4 | Expired coupon |
| TS_FOODN_11 | R5 | Payment failure |
| TS_FOODN_12 | R5 | Network drop during payment |
| TS_FOODN_13 | R5 | COD above COD limit |
| TS_FOODN_14 | R7 | Cancel after food prepared |
| TS_FOODN_15 | R6 | Track a delivered order |
| TS_FOODN_16 | R8 | Submit review without rating |

## 6. Test Cases
| TC ID | Req | Scenario | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|
| TC_FOODN_01 | R1 | Wrong OTP | Enter incorrect OTP | 000000 | Error 'Invalid OTP'; no login | High |
| TC_FOODN_02 | R1 | Expired OTP | Enter OTP after validity | OTP after 10 min | Error 'OTP expired'; resend option | High |
| TC_FOODN_03 | R1 | Invalid mobile number | Enter 5-digit number | 12345 | Validation error | High |
| TC_FOODN_04 | R2 | Location outside service area | Enter unserviceable address | Remote pin code | 'Not serviceable' message | High |
| TC_FOODN_05 | R2 | Search nonsense text | Search '@@@###' | @@@### | 'No results'; no crash | Medium |
| TC_FOODN_06 | R3 | Items from two restaurants | Add item from restaurant B while A's items in cart | Two restaurants | Prompt to clear/replace cart | Medium |
| TC_FOODN_07 | R3 | Order from closed restaurant | Open closed restaurant and order | Closed | Ordering disabled with notice | Medium |
| TC_FOODN_08 | R3 | Quantity beyond limit | Set quantity 100 | 100 | Limit message shown | Medium |
| TC_FOODN_09 | R4 | Coupon below minimum order | Apply coupon with small order | Cart Rs.100 vs min Rs.300 | Error stating minimum order value | Medium |
| TC_FOODN_10 | R4 | Expired coupon | Apply expired coupon | OLD20 | Coupon invalid message | Medium |
| TC_FOODN_11 | R5 | Payment failure | Invalid UPI/declined card | Wrong UPI id | Payment failed; order not placed; retry option | Medium |
| TC_FOODN_12 | R5 | Network drop during payment | Disconnect after paying | - | No duplicate charge; status reconciled | Medium |
| TC_FOODN_13 | R5 | COD above COD limit | Choose COD for large order | Rs.10000 | COD disabled message | Medium |
| TC_FOODN_14 | R7 | Cancel after food prepared | Cancel when Preparing/Picked up | - | Cancellation denied/partial per policy | Medium |
| TC_FOODN_15 | R6 | Track a delivered order | Open live tracking of delivered order | - | Shows 'Delivered'; no live map | Medium |
| TC_FOODN_16 | R8 | Submit review without rating | Submit without rating | - | Rating mandatory validation | Medium |

## 7. Requirement Traceability Matrix
| Req ID | Requirement | Test Cases |
|---|---|---|
| R1 | Sign-up/Login (OTP) | TC_FOODN_01, TC_FOODN_02, TC_FOODN_03 |
| R2 | Location & Search | TC_FOODN_04, TC_FOODN_05 |
| R3 | Menu & Cart | TC_FOODN_06, TC_FOODN_07, TC_FOODN_08 |
| R4 | Offers & Coupons | TC_FOODN_09, TC_FOODN_10 |
| R5 | Payment | TC_FOODN_11, TC_FOODN_12, TC_FOODN_13 |
| R6 | Order Tracking | TC_FOODN_15 |
| R7 | Cancellation & Refund | TC_FOODN_14 |
| R8 | Ratings & Reviews | TC_FOODN_16 |
| R9 | Non-functional | - |

## 8. Execution Template
| TC ID | Actual Result | Status (Pass/Fail) | Defect ID | Remarks |
|---|---|---|---|---|
| TC_FOODN_01 |  |  |  |  |
| TC_FOODN_02 |  |  |  |  |
| TC_FOODN_03 |  |  |  |  |

## 9. Conclusion
The requirements of the Food Delivery Application were analysed and **16 negative test scenarios** with corresponding test cases were designed, covering the requirements with invalid input, boundary violations, security and error handling.
