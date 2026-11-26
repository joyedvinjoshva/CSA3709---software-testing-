# Case Study: Negative Test Scenarios and Test Cases - E-Commerce Application

**Course:** CSA37 - Software Testing | **Programme:** Computer Science and Engineering | **Institute:** SIMATS Engineering

## 1. Aim
To identify and analyse the requirements of the **E-Commerce Application** and to prepare **negative** test scenarios and test cases for the application.

## 2. System Overview
An online shopping platform where customers search and browse products, manage cart/wishlist, place orders, pay online and track delivery, while admins manage catalogue and orders.

**Actors:** Customer, Seller/Admin, Payment Gateway

## 3. Requirement Analysis
| Req ID | Requirement | Description |
|---|---|---|
| R1 | Registration & Login | Customer registers (name, email, phone, password) and logs in. |
| R2 | Search & Filter | Search by keyword; filter by category, price, rating; sort. |
| R3 | Product Details | Show images, price, stock status, reviews. |
| R4 | Shopping Cart | Add, remove, change quantity; totals update; cart persists after login. |
| R5 | Checkout & Address | Enter/choose address; apply coupon; view order summary. |
| R6 | Payment | Card, UPI, net banking, COD; failed payment must not create a paid order. |
| R7 | Order Tracking & Cancellation | View status; cancel before shipping. |
| R8 | Returns & Refund | Return within 7 days of delivery; refund to original source. |
| R9 | Performance & Security | Pages load < 3 s; HTTPS; card data never stored in plain text. |

**Analysis notes:** every requirement is testable, uniquely identified and traceable to at least one test scenario. Where limits, time-outs or messages are not given, the values stated in the descriptions are assumed.

**Negative tests** use *invalid, unexpected or boundary-violating* input or sequences to check that the system rejects them gracefully, with proper messages, without crashing, corrupting data or exposing security holes.

## 4. Test Design Techniques Used
Equivalence partitioning, boundary value analysis, state-transition testing and error guessing.

## 5. Test Scenarios
| Scenario ID | Requirement | Test Scenario |
|---|---|---|
| TS_ECOMN_01 | R1 | Register with existing email |
| TS_ECOMN_02 | R1 | Register with invalid email |
| TS_ECOMN_03 | R1 | Register with weak password |
| TS_ECOMN_04 | R1 | Login with wrong password |
| TS_ECOMN_05 | R1 | Login with blank fields |
| TS_ECOMN_06 | R2 | Search non-existing product |
| TS_ECOMN_07 | R2 | Search with script characters |
| TS_ECOMN_08 | R4 | Quantity zero/negative in cart |
| TS_ECOMN_09 | R4 | Quantity above available stock |
| TS_ECOMN_10 | R4 | Add out-of-stock item |
| TS_ECOMN_11 | R5 | Checkout with empty address |
| TS_ECOMN_12 | R5 | Invalid pin code |
| TS_ECOMN_13 | R5 | Expired/invalid coupon |
| TS_ECOMN_14 | R6 | Payment with expired card |
| TS_ECOMN_15 | R6 | Wrong CVV |
| TS_ECOMN_16 | R6 | Back button after payment |
| TS_ECOMN_17 | R7 | Cancel after shipped |
| TS_ECOMN_18 | R8 | Return after 7-day window |

## 6. Test Cases
| TC ID | Req | Scenario | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|
| TC_ECOMN_01 | R1 | Register with existing email | Sign up with registered email | Existing email | Error 'Email already registered' | High |
| TC_ECOMN_02 | R1 | Register with invalid email | Enter 'abc.com' | abc.com | Validation error | High |
| TC_ECOMN_03 | R1 | Register with weak password | Password '123' | 123 | Password policy error | High |
| TC_ECOMN_04 | R1 | Login with wrong password | Valid email, wrong password | wrong | Error 'Invalid credentials' | High |
| TC_ECOMN_05 | R1 | Login with blank fields | Click Login with blank inputs | (blank) | Mandatory field messages | Medium |
| TC_ECOMN_06 | R2 | Search non-existing product | Search 'xyzabc123' | xyzabc123 | 'No results found' | Medium |
| TC_ECOMN_07 | R2 | Search with script characters | Search '<script>alert(1)</script>' | XSS string | Input escaped; no script executes | Medium |
| TC_ECOMN_08 | R4 | Quantity zero/negative in cart | Set quantity 0 / -1 | 0, -1 | Rejected or item removed; no negative total | Medium |
| TC_ECOMN_09 | R4 | Quantity above available stock | Set quantity 999, stock 5 | 999 | Error 'Only 5 items available' | Medium |
| TC_ECOMN_10 | R4 | Add out-of-stock item | Click Add on out-of-stock product | Stock 0 | Add disabled / 'Out of stock' | Medium |
| TC_ECOMN_11 | R5 | Checkout with empty address | Leave address blank; Continue | (blank) | Mandatory address validation | Medium |
| TC_ECOMN_12 | R5 | Invalid pin code | Enter pin '12' | 12 | Pin code validation error | Medium |
| TC_ECOMN_13 | R5 | Expired/invalid coupon | Apply 'OLD50' | OLD50 | Error 'Coupon invalid or expired'; total unchanged | Medium |
| TC_ECOMN_14 | R6 | Payment with expired card | Pay with expired card | Expiry 01/20 | Payment declined; order unpaid | Medium |
| TC_ECOMN_15 | R6 | Wrong CVV | Enter wrong CVV | CVV 000 | Payment failed message | Medium |
| TC_ECOMN_16 | R6 | Back button after payment | Press browser Back after success | - | No duplicate order/charge | Medium |
| TC_ECOMN_17 | R7 | Cancel after shipped | Try Cancel on shipped order | Status = Shipped | Cancel disabled / not allowed | Medium |
| TC_ECOMN_18 | R8 | Return after 7-day window | Request return after 10 days | Delivered 10 days ago | Return rejected with policy message | Medium |

## 7. Requirement Traceability Matrix
| Req ID | Requirement | Test Cases |
|---|---|---|
| R1 | Registration & Login | TC_ECOMN_01, TC_ECOMN_02, TC_ECOMN_03, TC_ECOMN_04, TC_ECOMN_05 |
| R2 | Search & Filter | TC_ECOMN_06, TC_ECOMN_07 |
| R3 | Product Details | - |
| R4 | Shopping Cart | TC_ECOMN_08, TC_ECOMN_09, TC_ECOMN_10 |
| R5 | Checkout & Address | TC_ECOMN_11, TC_ECOMN_12, TC_ECOMN_13 |
| R6 | Payment | TC_ECOMN_14, TC_ECOMN_15, TC_ECOMN_16 |
| R7 | Order Tracking & Cancellation | TC_ECOMN_17 |
| R8 | Returns & Refund | TC_ECOMN_18 |
| R9 | Performance & Security | - |

## 8. Execution Template
| TC ID | Actual Result | Status (Pass/Fail) | Defect ID | Remarks |
|---|---|---|---|---|
| TC_ECOMN_01 |  |  |  |  |
| TC_ECOMN_02 |  |  |  |  |
| TC_ECOMN_03 |  |  |  |  |

## 9. Conclusion
The requirements of the E-Commerce Application were analysed and **18 negative test scenarios** with corresponding test cases were designed, covering the requirements with invalid input, boundary violations, security and error handling.
