# Home Credit LAP Qualification Agent - Test Cases

## 1. Overview

This document describes the test scenarios used to evaluate the Home Credit Loan Against Property (LAP) Qualification Agent built using Retell AI.

The objective is to verify that the voice agent correctly handles:

- Customer qualification and disqualification
- Loan amount limits
- Callback requests
- Existing-loan and balance-transfer cases
- Out-of-order responses
- Contradictory information

## 2. Test Environment

| Test Environment | Details |
| --- | --- |
| Platform | Retell AI |
| Agent | Home Credit LAP Qualification Agent |
| Product | Loan Against Property (LAP) |
| Maximum loan amount | ₹75 lakh |
| Eligible property types | Residential, Commercial, Industrial |
| Eligible ownership types | Sole and Joint |
| Eligible occupations | Salaried and Self-employed |
| Income requirement | Income must be received in or credited to a bank account |
| Valid loan tenure | 3-15 years |

## 3. Test Scenario Summary

| Test ID | Test Scenario | Expected Behavior | Actual Result | Status |
| --- | --- | --- | --- | --- |
| TC01 | Normal eligible customer | Collect all seven valid eligibility details and provide the senior expert callback handoff. | The agent completed the qualification flow and provided the callback handoff. | PASS |
| TC02 | Agricultural property | Politely disqualify the customer and end the call immediately. | The agent explained that agricultural property was not eligible and ended the call. | PASS |
| TC03 | Income received in cash | Disqualify the customer because income must be credited to a bank account. | The agent explained the income requirement and politely ended the call. | PASS |
| TC04 | Original documents unavailable | Disqualify the customer if only photocopies are available or original documents are unavailable. | The agent explained the original-document requirement and ended the call. | PASS |
| TC05 | Requests ₹1 crore and accepts ₹75 lakh | Explain the maximum offer amount, confirm acceptance, and continue qualification. | The agent explained the ₹75 lakh limit, continued after acceptance, and provided the senior expert callback handoff. | PASS |
| TC06 | Requests ₹1 crore and declines ₹75 lakh | Respect the customer’s decision and end the call without continuing qualification. | The agent respected the customer’s decision and ended the qualification process. | PASS |
| TC07 | Joint property ownership | Accept joint ownership and continue the eligibility check. | The agent accepted joint ownership and continued the qualification flow. | PASS |
| TC08 | Existing property loan or balance transfer | Stop the fresh-loan checklist and direct the customer to a loan-transfer specialist. | The agent stopped the qualification checklist and explained that a specialist would follow up. | PASS |
| TC09 | Customer is busy | Ask for a preferred callback time, confirm it, thank the customer, and end the call. | The agent collected and confirmed the callback time before ending the call. | PASS |
| TC10 | Invalid loan tenure | Explain the valid 3-15-year range and request a valid tenure. | The agent explained the valid tenure range and continued after the customer provided a valid tenure. | PASS |
| TC11 | Out-of-order answers | Store valid information provided out of order and ask only for the earliest unanswered item. | The agent retained previously provided details and continued with the unanswered checklist items. | PASS |
| TC12 | Contradictory information | Clarify conflicting answers and use the customer’s confirmed answer. | The agent clarified the conflicting information and applied the eligibility rules to the confirmed answer. | PASS |

## 4. Detailed Test Cases

### TC01 - Normal Eligible Customer

**Input scenario:**

- Property type: Residential
- Ownership: Sole
- Original documents: Available
- Desired loan amount: ₹40 lakh
- Occupation: Salaried
- Income mode: Credited to bank account
- Estimated property market value: ₹1.2 crore
- Desired tenure: 10 years

**Expected behavior:**

The agent should collect all seven valid eligibility details, confirm the preliminary eligibility outcome without promising final approval, and inform the customer that a senior loan expert will call with the exact interest rates and next steps.

**Result:** PASS

### TC02 - Agricultural Property

**Input scenario:**

The customer confirms that the property is agricultural land.

**Expected behavior:**

The agent should explain politely that agricultural property is not eligible for this offer and end the call without continuing the remaining checklist.

**Result:** PASS

### TC03 - Income Received in Cash

**Input scenario:**

The customer has an otherwise eligible property but receives salary or business income in cash.

**Expected behavior:**

The agent should explain that income must be received in or credited to a bank account, disqualify the customer, and end the call without asking the remaining checklist questions.

**Result:** PASS

### TC04 - Original Documents Unavailable

**Input scenario:**

The customer confirms that only photocopies of the property documents are available.

**Expected behavior:**

The agent should explain that original property documents are required for verification, disqualify the customer, and end the call.

**Result:** PASS

### TC05 - Loan Amount Above the Offer Limit, Customer Accepts

**Input scenario:**

The customer requests ₹1 crore and agrees to continue with the maximum offer amount of ₹75 lakh. The remaining eligibility details are valid.

**Expected behavior:**

The agent should explain the maximum offer amount, ask whether the customer wants to continue with ₹75 lakh, record ₹75 lakh after acceptance, complete the checklist, and provide the senior expert callback handoff.

**Result:** PASS

### TC06 - Loan Amount Above the Offer Limit, Customer Declines

**Input scenario:**

The customer requests ₹1 crore but declines to continue with ₹75 lakh.

**Expected behavior:**

The agent should acknowledge the customer’s decision, politely end the qualification process, and not continue asking eligibility questions.

**Result:** PASS

### TC07 - Joint Property Ownership

**Input scenario:**

The customer confirms that the property is jointly owned and provides valid answers to the remaining eligibility questions.

**Expected behavior:**

The agent should accept joint ownership as eligible and continue collecting the remaining checklist details.

**Result:** PASS

### TC08 - Existing Property Loan or Balance Transfer

**Input scenario:**

The customer mentions an existing property loan, requests a balance transfer, or wants to reduce their current EMI.

**Expected behavior:**

The agent should stop the fresh-loan checklist, explain that a loan-transfer specialist will follow up, and end the call without classifying the customer as qualified or disqualified.

**Result:** PASS

### TC09 - Busy Customer and Callback Request

**Input scenario:**

The customer says they are busy and asks the agent to call later.

**Expected behavior:**

The agent should ask for a convenient callback time, repeat the time for confirmation, thank the customer, and end the call without continuing the offer or eligibility questions.

**Result:** PASS

### TC10 - Invalid Loan Tenure

**Input scenario:**

The customer initially requests a tenure outside the allowed range, such as 20 years, and then selects a valid tenure of 15 years.

**Expected behavior:**

The agent should explain that the available tenure is between 3 and 15 years, request a valid tenure, and continue the checklist once the customer provides a valid value.

**Result:** PASS

### TC11 - Out-of-Order Answers

**Input scenario:**

The customer provides several details in one response, such as the desired loan amount, property market value, and occupation, before answering the property type and ownership questions.

**Expected behavior:**

The agent should extract and store all valid details, avoid asking questions whose answers are already known, and ask only the earliest unanswered checklist item.

**Result:** PASS

### TC12 - Contradictory Information

**Input scenario:**

The customer gives conflicting answers about the property type and then confirms which answer is correct.

**Expected behavior:**

The agent should identify the contradiction, ask the customer to clarify, store the confirmed answer, and apply the appropriate eligibility rule. If the confirmed property type is agricultural, the agent should disqualify the customer immediately.

**Result:** PASS

## 5. Test Summary

- Total test cases: 12
- Passed: 12
- Failed: 0
- Pass rate: 100%

All 12 planned test scenarios were tested to evaluate the agent’s behavior against the Home Credit LAP qualification requirements.

The tests cover the main qualification rules, immediate disqualification conditions, callback handling, transfer cases, out-of-order answers, and contradiction handling.

## 6. Test Evidence

Call recordings and corresponding transcripts should be retained for the executed test cases.

Recommended evidence filenames:

- `TC01_normal_eligible_customer`
- `TC02_agricultural_property`
- `TC03_cash_income`
- `TC04_original_documents_unavailable`
- `TC05_loan_limit_accepted`
- `TC06_loan_limit_declined`
- `TC07_joint_ownership`
- `TC08_loan_transfer`
- `TC09_callback_request`
- `TC10_invalid_tenure`
- `TC11_out_of_order_answers`
- `TC12_contradictory_information`

Each recording should have a matching transcript so that reviewers can compare the agent’s actual responses with the expected behavior.

## 7. Conclusion

The test suite evaluates whether the Home Credit LAP Qualification Agent follows the specified qualification process, applies the eligibility rules, handles exceptions appropriately, and provides the correct next step for each customer.

The agent is designed to perform preliminary qualification only. Final loan decisions and exact interest rates are handled by a senior loan expert.
