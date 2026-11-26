# Experiment 1: Identification and Documentation of Software Defects in an ATM System Specification

**Course:** CSA37 - Software Testing | **Institute:** SIMATS Engineering

## 1. Aim
To select a system (ATM), thoroughly examine its system specification, and identify and document the software (specification/requirement) defects present.

## 2. System Selected
Automated Teller Machine (ATM) - a self-service banking terminal for cash withdrawal, balance enquiry, mini-statement and PIN change.

## 3. System Specification Examined
| ID | Specification statement |
|---|---|
| S1 | The user inserts a card and enters a 4-digit PIN. After 3 wrong attempts the card is retained. |
| S2 | The user can withdraw cash in multiples of 100. Minimum Rs.100, maximum Rs.20,000 per transaction. |
| S3 | Daily withdrawal limit is Rs.40,000 per card. |
| S4 | The ATM shall display the balance and print a mini-statement on request. |
| S5 | The ATM shall dispense cash only if the account balance is sufficient. |
| S6 | If the user does not respond for a reasonable time, the session ends. |
| S7 | The receipt is printed after each transaction. |
| S8 | The system should be fast and user friendly. |
| S9 | The user can change the PIN. The new PIN must be different from the old PIN. |
| S10 | The ATM shall handle hardware failures appropriately. |

## 4. Review Technique
A static technique (requirement walkthrough / inspection). Each statement was checked for **ambiguity, incompleteness, contradiction, omission, testability and consistency**.

## 5. Defects Identified
| Defect ID | Spec ref | Defect type | Description | Severity | Suggested fix |
|---|---|---|---|---|---|
| D01 | S6 | Ambiguity | 'Reasonable time' is not quantified, so the time-out cannot be tested. | Medium | Specify e.g. 30 s idle time-out with a 10 s warning. |
| D02 | S8 | Non-testable requirement | 'Fast' and 'user friendly' have no measurable criteria. | Medium | State response time (e.g. < 3 s per screen) and usability criteria. |
| D03 | S10 | Incompleteness | 'Appropriately' does not say what happens on card jam, cash jam, printer out of paper or power loss. | High | List each failure and required behaviour (rollback, log, message). |
| D04 | S1 | Omission | No description of unblocking a retained card, nor whether the PIN-attempt counter resets after a correct entry. | Medium | Define counter reset and card recovery. |
| D05 | S2 / S3 | Incompleteness | Behaviour is unspecified when the request exceeds the remaining daily limit (e.g. Rs.5,000 left, user asks Rs.10,000). | High | Specify the error message and whether partial withdrawal is allowed. |
| D06 | S2 | Incompleteness | Note availability not covered: what if the ATM lacks the notes/cash for the requested amount? | High | Add denomination rules and 'cash not available' handling. |
| D07 | S5 | Omission | Does the balance check include minimum balance, holds and uncleared cheques? | High | Define available vs ledger balance and minimum balance rule. |
| D08 | S7 | Omission | Receipt printing failure or paper-out: should the transaction proceed? Is a receipt optional? | Low | Allow 'no receipt'; define behaviour on printer failure. |
| D09 | S9 | Incompleteness | PIN policy missing: no rule against trivial PINs (0000, 1234) or confirming the new PIN. | Medium | Add PIN complexity and double-entry confirmation. |
| D10 | S4 | Omission | Number of transactions and format of the mini-statement are not given. | Low | Specify last 5/10 transactions with date, type, amount, balance. |
| D11 | General | Omission | No security requirement: skimming protection, PIN encryption, session clearing, audit log. | High | Add security and audit requirements. |
| D12 | General | Omission | Other-bank card handling, transaction fees and free-transaction count are not mentioned. | Medium | Define fees and display of charges. |
| D13 | S2 | Boundary ambiguity | Whether Rs.20,000 itself is allowed (<= or <) is unclear. | Low | State inclusive limits. |

## 6. Defect Summary
| Defect type | Count |
|---|---|
| Ambiguity | 1 |
| Boundary ambiguity | 1 |
| Incompleteness | 4 |
| Non-testable requirement | 1 |
| Omission | 6 |

| Severity | Count |
|---|---|
| High | 5 |
| Low | 3 |
| Medium | 5 |

## 7. Defect Life Cycle
New -> Assigned -> Open -> Fixed -> Retest -> Verified -> Closed (or Reopened / Rejected / Deferred).

## 8. Sample Defect Report
| Field | Value |
|---|---|
| Defect ID | D05 |
| Summary | Behaviour undefined when requested amount exceeds remaining daily limit |
| Module | Cash withdrawal |
| Severity / Priority | High / High |
| Steps to reproduce | Withdraw Rs.35,000 earlier in the day; request Rs.10,000 |
| Expected | Clear message: 'Daily limit exceeded; you can withdraw up to Rs.5,000' |
| Actual | Not defined in specification |
| Status | New |

## 9. Conclusion
13 specification defects were identified in the ATM specification, mostly ambiguity, omissions and incompleteness. Fixing them before development is cheapest, because defects found in requirements cost far less than those found later.
