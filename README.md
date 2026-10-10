# Home Credit LAP Qualification Agent

## 1. Project Overview

This project defines an AI voice agent for Home Credit that contacts existing customers about a pre-approved Loan Against Property (LAP) offer of up to **₹75 lakh**.

The agent performs a **preliminary eligibility check** and passes complete, valid leads to a senior loan expert. It does not make final loan decisions, promise approval, or provide unsupported product details.

## 2. Objectives

The agent is designed to:

1. Verify that the intended customer is on the call.
2. Respect privacy and avoid sharing offer details with anyone else.
3. Identify when the customer is busy and arrange a callback.
4. Present the LAP offer naturally and conversationally.
5. Detect existing-loan, balance-transfer, and EMI-reduction requests.
6. Collect seven eligibility items while remembering information given out of order.
7. Apply the eligibility rules consistently.
8. End the call immediately when a confirmed disqualifying condition is found.
9. Hand valid, complete cases to a senior loan expert.

## 3. Conversation Flow

| Step | Agent behavior |
| --- | --- |
| 1. Greeting | Ask for the customer and verify their identity. |
| 2. Availability | If the customer is busy, capture a callback time and end the call. |
| 3. Offer | Explain the special LAP offer of up to ₹75 lakh. |
| 4. Transfer check | Detect an existing property loan, balance transfer, or EMI-reduction request. |
| 5. Eligibility | Collect the seven checklist items and validate each answer. |
| 6. Decision | Disqualify immediately when a mandatory rule fails. |
| 7. Handoff | After all valid items are captured, arrange a senior loan expert callback. |

## 4. Eligibility Checklist

The agent collects these items in order. Customers may provide several answers together or answer out of order; those facts are stored and the agent asks only for the earliest unanswered item.

| No. | Checklist item | Required information |
| --- | --- | --- |
| 1 | Property type | Residential, commercial, or industrial |
| 2 | Ownership | Sole or joint |
| 3 | Original documents | Original property documents available for verification |
| 4 | Desired loan amount | Amount up to ₹75 lakh, or acceptance of ₹75 lakh when a higher amount is requested |
| 5 | Occupation and income mode | Salaried or self-employed, with income credited to a bank account |
| 6 | Market value | Customer’s approximate property value |
| 7 | Desired tenure | Between 3 and 15 years, inclusive |

## 5. Eligibility Rules

| Category | Eligible | Disqualifying or alternate behavior |
| --- | --- | --- |
| Property type | Residential, commercial, industrial | Agricultural property: politely disqualify and end the call |
| Ownership | Sole or joint | Ambiguous ownership: clarify before recording a value |
| Documents | Original documents available for verification | Only photocopies or no originals: disqualify and end the call |
| Loan amount | Up to ₹75 lakh | For more than ₹75 lakh, explain the limit and ask whether the customer accepts ₹75 lakh; end if they decline |
| Occupation | Salaried or self-employed | Any other occupation requires clarification |
| Income mode | Income credited to a bank account | Cash income: disqualify; undefined modes such as cheque require clarification |
| Market value | Any approximate customer estimate | No minimum value is applied |
| Tenure | 3 to 15 years | Explain the valid range for an invalid answer; repeated refusal or invalid answers lead to disqualification |

## 6. State and Decision Handling

The prompt instructs the agent to maintain internal state for each checklist item. A value may be unknown, captured, clarification-pending, or ineligible.

After every customer response, the agent follows this sequence:

1. If the customer asks the agent to wait, output exactly `NO_RESPONSE_NEEDED`.
2. Check for an existing-loan or EMI-reduction transfer case.
3. Handle a busy-customer callback request.
4. Extract every eligibility fact from the response.
5. Store all valid facts, including facts provided out of order.
6. Resolve contradictions instead of silently overwriting them.
7. Apply immediate disqualification rules.
8. Ask only the earliest unanswered checklist item.

This prevents repeated questions and supports natural customer responses such as:

> “It is a residential house, jointly owned, and worth around ₹80 lakh.”

The agent stores all three facts and continues with the first missing item.

## 7. Special Conversation Paths

### Busy customer

The agent does not continue the offer or eligibility questions. It asks for a convenient callback time, confirms the time, thanks the customer, and calls `end_call`.

### Existing loan or EMI reduction

The agent stops the fresh-loan checklist, explains that a loan-transfer specialist will contact the customer, thanks them, and calls `end_call`. The customer is not labeled qualified or disqualified.

### Diversions and product questions

The agent answers briefly using only `additional_context_from_rag`. It does not invent interest rates, fees, charges, guarantees, or other product details. When exact information is unavailable, it says that the senior loan expert will provide it after the preliminary check, then returns to the earliest unanswered item.

### Contradictions and corrections

The agent asks the customer to confirm which answer is correct. The confirmed answer replaces the earlier value. If the confirmed answer is ineligible, the agent disqualifies the customer immediately.

## 8. Handoff Conditions

The senior loan expert handoff occurs only when:

- All seven checklist items have valid answers.
- No disqualifying condition exists.
- The case is not an existing-loan, balance-transfer, or EMI-reduction case.
- No clarification is pending.

At handoff, the agent confirms that the preliminary details are complete and says that a senior loan expert will call with the exact interest rates and next steps. The agent does not claim final approval.

## 9. Language and Agent Identity

The system prompt supports dynamic values for:

| Variable | Purpose |
| --- | --- |
| `{{agent_name}}` | Agent identity |
| `{{company_name}}` | Company identity |
| `{{customer_name}}` | Intended customer |
| `{{agent_gender}}` | Consistent gender and gendered grammar where applicable |
| `{{current_day}}`, `{{current_date}}`, `{{current_time}}` | Current call context |
| `{{language_to_speak}}` | English or Hindi call language |
| `{{additional_context_from_rag}}` | Approved product knowledge |

The agent stays in the configured language unless the customer explicitly asks for the other supported language. It keeps responses short, courteous, and conversational.

## 10. Repository Contents

| File | Purpose |
| --- | --- |
| [system_prompt.md](system_prompt.md) | Complete Retell AI system prompt with call flow, state rules, eligibility logic, diversions, and handoff behavior |
| [test_cases.md](test_cases.md) | 12 test scenarios with inputs, expected behavior, actual results, and evidence filenames |
| [README.md](README.md) | Project overview, implementation approach, business rules, and submission guide |

## 11. Test Coverage

The test suite contains 12 documented scenarios covering:

- Normal eligible customer
- Agricultural property
- Cash income
- Unavailable original documents
- Loan amount above ₹75 lakh with acceptance or decline
- Joint ownership
- Existing loan or balance transfer
- Busy customer callback
- Invalid tenure
- Out-of-order answers
- Contradictory information

### Test status

| Metric | Result |
| --- | --- |
| Total test cases | 12 |
| Passed | 12 |
| Failed | 0 |
| Pass rate | 100% |

The detailed test results are available in [test_cases.md](test_cases.md). Recordings and matching transcripts should be retained for each test case when the calls are executed in Retell AI.

## 12. Submission Deliverables

1. Complete system prompt
2. Voice-agent implementation in Retell AI or a similar platform
3. Test call recordings
4. Matching call transcripts and logs
5. Test results and supporting documentation

## 13. Design Principles

- **Stateful:** remember valid facts provided naturally or out of order.
- **Sequential:** ask the earliest unanswered checklist item.
- **Accurate:** apply only the stated eligibility rules.
- **Privacy-conscious:** disclose offer information only after customer verification.
- **Conversational:** use short, courteous turns instead of a rigid questionnaire.
- **Conservative:** never invent product information or promise approval.
- **Disciplined:** stop immediately for disqualification and transfer cases.
- **Human-assisted:** send complete preliminary cases to a senior loan expert for final details and decisions.
