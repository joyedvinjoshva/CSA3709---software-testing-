# Case Study: Positive Test Scenarios and Test Cases - E-Commerce Application

**Course:** CSA37 - Software Testing | **Programme:** Computer Science and Engineering | **Institute:** SIMATS Engineering

## 1. Aim
To identify and analyse the requirements of the **E-Commerce Application** and to prepare **positive** test scenarios and test cases for the application.

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

**Positive tests** use *valid* input and expected usage to check that the system does what the requirement says (the 'happy path').

## 4. Test Design Techniques Used
Equivalence partitioning, boundary value analysis, state-transition testing and error guessing.

## 5. Test Scenarios
| Scenario ID | Requirement | Test Scenario |
|---|---|---|
| TS_ECOMP_01 | R1 | Register with valid details |
| TS_ECOMP_02 | R1 | Login with valid credentials |
| TS_ECOMP_03 | R2 | Search existing product |
| TS_ECOMP_04 | R2 | Filter by price range |
| TS_ECOMP_05 | R2 | Sort by price low to high |
| TS_ECOMP_06 | R3 | Open product details |
| TS_ECOMP_07 | R4 | Add item to cart |
| TS_ECOMP_08 | R4 | Increase quantity in cart |
| TS_ECOMP_09 | R4 | Remove item from cart |
| TS_ECOMP_10 | R5 | Apply valid coupon |
| TS_ECOMP_11 | R6 | Pay with valid card |
| TS_ECOMP_12 | R6 | Cash on delivery order |
| TS_ECOMP_13 | R7 | Track an order |
| TS_ECOMP_14 | R7 | Cancel order before shipping |
| TS_ECOMP_15 | R8 | Return within 7 days |

## 6. Test Cases
| TC ID | Req | Scenario | Test Steps | Test Data | Expected Result | Priority |
|---|---|---|---|---|---|---|
| TC_ECOMP_01 | R1 | Register with valid details | Open Sign-up; fill valid data; Submit | Name, valid email, 10-digit phone, Pass@1234 | Account created; confirmation shown | High |
| TC_ECOMP_02 | R1 | Login with valid credentials | Enter registered email/password; Login | Valid user | Home page with user's name | High |
| TC_ECOMP_03 | R2 | Search existing product | Type 'laptop'; press Enter | Keyword: laptop | Relevant laptops listed | High |
| TC_ECOMP_04 | R2 | Filter by price range | Apply price 10000-30000 | Range | Only products within range shown | High |
| TC_ECOMP_05 | R2 | Sort by price low to high | Select sort option | Price asc | Results ascending | Medium |
| TC_ECOMP_06 | R3 | Open product details | Click on a product | In-stock product | Details, images, price, 'In stock' displayed | Medium |
| TC_ECOMP_07 | R4 | Add item to cart | Click Add to Cart | Qty 1 | Cart count = 1; item shown | Medium |
| TC_ECOMP_08 | R4 | Increase quantity in cart | Change qty 1 -> 3 | Qty 3 | Line and grand totals recalculated | Medium |
| TC_ECOMP_09 | R4 | Remove item from cart | Click Remove | - | Item removed; totals updated | Medium |
| TC_ECOMP_10 | R5 | Apply valid coupon | Enter valid coupon at checkout | SAVE10 | Discount applied | Medium |
| TC_ECOMP_11 | R6 | Pay with valid card | Select card; enter valid details; Pay | Test card 4111 1111 1111 1111 | Payment success; order number generated | Medium |
| TC_ECOMP_12 | R6 | Cash on delivery order | Select COD; Place order | COD-eligible pin code | Order placed 'Confirmed' | Medium |
| TC_ECOMP_13 | R7 | Track an order | My Orders > Track | Existing order | Current status and expected delivery shown | Medium |
| TC_ECOMP_14 | R7 | Cancel order before shipping | Open order; Cancel; confirm | Status = Confirmed | Order cancelled; refund initiated | Medium |
| TC_ECOMP_15 | R8 | Return within 7 days | Open delivered order; Return; select reason | Delivered 2 days ago | Return accepted; pickup scheduled | Medium |

## 7. Requirement Traceability Matrix
| Req ID | Requirement | Test Cases |
|---|---|---|
| R1 | Registration & Login | TC_ECOMP_01, TC_ECOMP_02 |
| R2 | Search & Filter | TC_ECOMP_03, TC_ECOMP_04, TC_ECOMP_05 |
| R3 | Product Details | TC_ECOMP_06 |
| R4 | Shopping Cart | TC_ECOMP_07, TC_ECOMP_08, TC_ECOMP_09 |
| R5 | Checkout & Address | TC_ECOMP_10 |
| R6 | Payment | TC_ECOMP_11, TC_ECOMP_12 |
| R7 | Order Tracking & Cancellation | TC_ECOMP_13, TC_ECOMP_14 |
| R8 | Returns & Refund | TC_ECOMP_15 |
| R9 | Performance & Security | - |

## 8. Execution Template
| TC ID | Actual Result | Status (Pass/Fail) | Defect ID | Remarks |
|---|---|---|---|---|
| TC_ECOMP_01 |  |  |  |  |
| TC_ECOMP_02 |  |  |  |  |
| TC_ECOMP_03 |  |  |  |  |

## 9. Conclusion
The requirements of the E-Commerce Application were analysed and **15 positive test scenarios** with corresponding test cases were designed, covering the requirements with valid flows.
