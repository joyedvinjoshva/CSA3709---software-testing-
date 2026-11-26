# Case Study: Positive Test Scenarios and Test Cases - Food Delivery Application

**Course:** CSA37 - Software Testing | **Programme:** Computer Science and Engineering | **Institute:** SIMATS Engineering

## 1. Aim
To identify and analyse the requirements of the **Food Delivery Application** and to prepare **positive** test scenarios and test cases for the application.

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

**Positive tests** use *valid* input and expected usage to check that the system does what the requirement says (the 'happy path').

## 4. Test Design Techniques Used
Equivalence partitioning, boundary value analysis, state-transition testing and error guessing.

## 5. Test Scenarios
| Scenario ID | Requirement | Test Scenario |
|---|---|---|
| TS_FOODP_01 | R1 | Login with valid mobile + OTP |
| TS_FOODP_02 | R2 | Set delivery location |
| TS_FOODP_03 | R2 | Search restaurant by name |
| TS_FOODP_04 | R2 | Apply veg filter |
| TS_FOODP_05 | R3 | Add dish to cart |
| TS_FOODP_06 | R3 | Customise dish |
| TS_FOODP_07 | R4 | Apply valid coupon |
| TS_FOODP_08 | R5 | Pay using UPI |
| TS_FOODP_09 | R5 | Cash on delivery |
| TS_FOODP_10 | R6 | Track order live |
| TS_FOODP_11 | R7 | Cancel before acceptance |
| TS_FOODP_12 | R8 | Rate delivered order |

## 6. Test Cases
| TC ID | Req | Scenario | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|
| TC_FOODP_01 | R1 | Login with valid mobile + OTP | Enter mobile; receive OTP; enter OTP | Valid number, correct OTP | Logged in; home screen shown | High |
| TC_FOODP_02 | R2 | Set delivery location | Allow GPS / type address | Valid address | Nearby restaurants listed | High |
| TC_FOODP_03 | R2 | Search restaurant by name | Type 'Pizza' | pizza | Matching restaurants/dishes shown | High |
| TC_FOODP_04 | R2 | Apply veg filter | Toggle Veg only | - | Only vegetarian items shown | High |
| TC_FOODP_05 | R3 | Add dish to cart | Open menu; add dish | Qty 1 | Cart shows item and price | Medium |
| TC_FOODP_06 | R3 | Customise dish | Select size and extra topping | Large + cheese | Price updates with add-ons | Medium |
| TC_FOODP_07 | R4 | Apply valid coupon | Enter coupon at cart | WELCOME50, order above minimum | Discount applied | Medium |
| TC_FOODP_08 | R5 | Pay using UPI | Select UPI; approve | Valid UPI id | Payment success; order placed | Medium |
| TC_FOODP_09 | R5 | Cash on delivery | Choose COD; Place order | - | Order placed with COD tag | Medium |
| TC_FOODP_10 | R6 | Track order live | Open Track Order | Active order | Status updates and ETA displayed | Medium |
| TC_FOODP_11 | R7 | Cancel before acceptance | Cancel within allowed time | Status = Placed | Cancelled; refund initiated | Medium |
| TC_FOODP_12 | R8 | Rate delivered order | Give 5 stars + comment | 5, 'Tasty' | Rating saved and shown | Medium |

## 7. Requirement Traceability Matrix
| Req ID | Requirement | Test Cases |
|---|---|---|
| R1 | Sign-up/Login (OTP) | TC_FOODP_01 |
| R2 | Location & Search | TC_FOODP_02, TC_FOODP_03, TC_FOODP_04 |
| R3 | Menu & Cart | TC_FOODP_05, TC_FOODP_06 |
| R4 | Offers & Coupons | TC_FOODP_07 |
| R5 | Payment | TC_FOODP_08, TC_FOODP_09 |
| R6 | Order Tracking | TC_FOODP_10 |
| R7 | Cancellation & Refund | TC_FOODP_11 |
| R8 | Ratings & Reviews | TC_FOODP_12 |
| R9 | Non-functional | - |

## 8. Execution Template
| TC ID | Actual Result | Status (Pass/Fail) | Defect ID | Remarks |
|---|---|---|---|---|
| TC_FOODP_01 |  |  |  |  |
| TC_FOODP_02 |  |  |  |  |
| TC_FOODP_03 |  |  |  |  |

## 9. Conclusion
The requirements of the Food Delivery Application were analysed and **12 positive test scenarios** with corresponding test cases were designed, covering the requirements with valid flows.
