# Home Credit LAP Qualification Agent - Audio Transcripts

## 1. Purpose

This document contains the available Retell AI call summaries and transcripts used as evidence for the Home Credit Loan Against Property (LAP) Qualification Agent.

The transcripts are presented as recorded. Minor grammatical errors or unusual phrases in customer speech may be transcription artifacts from automatic speech recognition.

## 2. Test Coverage

| Test case | Scenario | Outcome |
| --- | --- | --- |
| Test Case 1 | Normal eligible customer | Completed all seven eligibility checks and received a senior expert handoff |
| Test Case 2 | Agricultural property | Disqualified immediately |
| Test Case 3 | Cash income | Disqualified immediately |
| Test Case 4 | Original documents unavailable | Disqualified immediately |
| Test Case 5 | Loan request above ₹75 lakh, customer accepts ₹75 lakh | Completed qualification and received a senior expert handoff |

---

## Test Case 1 - Normal Eligible Customer

### Call Metadata

| Field | Details |
| --- | --- |
| Date and time | 10/10/2026, 12:06 IST |
| Agent | Home Credit LAP Qualification Agent |
| Agent ID | `agent_29ddd5...aa2` |
| Version | 1 |
| Call ID | `call_d1da1f094879e31a93f...454` |
| Duration | 1 minute 36 seconds |
| Cost | $0.237 |
| LLM tokens | 2098.12 |
| Call status | Ended |
| Call result | Successful |
| User sentiment | Positive |
| Disconnection reason | Agent hangup |
| End-to-end latency | 1151 ms |

### Conversation Analysis

Rahul Sharma confirmed interest in a loan against residential property and provided the required eligibility details:

- Property type: Residential
- Ownership: Sole
- Original documents: Available
- Occupation: Salaried
- Income mode: Credited to bank account
- Estimated property value: Approximately ₹1.2 crore
- Requested loan amount: ₹40 lakh
- Preferred tenure: 10 years

The agent stated that a senior loan expert would call with exact rates and next steps.

### Transcript

**Agent - 0:00**

Hello, may I speak with Rahul Sharma?

**Customer - 0:04**

S this is round show only.

**Agent - 0:08**

Sorry, could you please confirm - am I speaking with Rahul Sharma?

**Customer - 0:12**

Yes. This is Rahul Sharma.

**Agent - 0:15**

Hi Rahul, I’m Priya from Home Credit. As a valued customer, you have a pre-approved Loan Against Property offer of up to ₹75 lakh. I just have a few quick questions to see if it suits you.

**Customer - 0:26**

Two, go ahead.

**Agent - 0:29**

Thank you. What type of property is it - residential, commercial, or industrial?

**Customer - 0:35**

Then a residential property.

**Agent - 0:38**

Is the property solely owned by you or jointly owned?

**Customer - 0:42**

As it is fully owned by me.

**Agent - 0:45**

Do you have the original property documents available for verification?

**Customer - 0:49**

As I have all the required original documents.

**Agent - 0:55**

What loan amount are you looking for?

**Customer - 0:58**

Forty lakh rupees.

**Agent - 1:01**

Thank you. Are you salaried or self-employed, and is your income credited to your bank account?

**Customer - 1:08**

And salary and a salary is credited directly to my bank account only.

**Agent - 1:13**

What is the approximate current market value of the property?

**Customer - 1:17**

Around one point two crore rupees.

**Agent - 1:20**

And what loan tenure would you prefer, between 3 and 15 years?

**Customer - 1:25**

Ten years.

**Agent - 1:28**

Thank you, Rahul. I have the details. A senior loan expert will call you shortly with the exact interest rates and next steps.

### Tool Action

At 1:36, the agent called `end_call`.

---

## Test Case 2 - Agricultural Property

### Conversation Analysis

Priya from Home Credit spoke with Rahul Sharma about a pre-approved Loan Against Property offer of up to ₹75 lakh. Rahul stated that the property was agricultural land. The agent informed him that agricultural property was not eligible for this offer and ended the call.

### Transcript

**Agent - 0:00**

Hello, may I speak with Rahul Sharma?

**Customer - 0:04**

As I’m Rahul Sharma.

**Agent - 0:06**

Hello Rahul, I’m Priya from Home Credit. As a valued customer, you have a pre-approved Loan Against Property offer of up to ₹75 lakh. I just have a few quick questions to see if it suits you.

Is the property residential, commercial, industrial, or agricultural?

**Customer - 0:22**

Is in agricultural land.

**Agent - 0:27**

Thank you for your time, Rahul. Agricultural property does not meet the criteria for this specific offer at this time.

### Tool Action

At 0:33, the agent called `end_call`.

---

## Test Case 3 - Income Received in Cash

### Conversation Analysis

Priya from Home Credit screened Rahul Sharma for a pre-approved Loan Against Property offer. Rahul had a solely owned residential property with original documents and requested ₹40 lakh. He was deemed ineligible because his salary was received in cash rather than credited to a bank account.

### Transcript

**Agent - 0:00**

Hello, may I speak with Rahul Sharma?

**Customer - 0:03**

As it is Raujuma.

**Agent - 0:08**

Could I please confirm if I’m speaking with Rahul Sharma?

**Customer - 0:12**

Yes. I am Rahul Sharma.

**Agent - 0:14**

Hi Rahul, I’m Priya from Home Credit. As a valued customer, you have a pre-approved Loan Against Property offer of up to ₹75 lakh. I just need a few quick details to see if it suits you.

**Customer - 0:26**

Okay.

**Customer - 0:27**

So go ahead.

**Agent - 0:29**

Thank you. What type of property is it - residential, commercial, or industrial?

**Customer - 0:34**

The residential.

**Agent - 0:36**

Is the property solely owned by you or jointly owned?

**Customer - 0:41**

Totally owned by me.

**Agent - 0:43**

Do you have the original property documents available for verification?

**Customer - 0:47**

Yes. Yes.

**Agent - 0:49**

What loan amount are you looking for?

**Customer - 0:52**

Oh, forty lakh rupees.

**Agent - 0:54**

Thank you. Are you salaried or self-employed, and is your income credited to your bank account?

**Customer - 1:00**

I'm sorry, but I receive my salary in cash.

**Agent - 1:05**

I understand. Since income for this offer needs to be credited to a bank account, you don’t meet the criteria at this time. Thank you for your time.

### Tool Action

At 1:13, the agent called `end_call`.

---

## Test Case 4 - Original Documents Unavailable

### Conversation Analysis

The agent verified Rahul Sharma’s identity and discussed a pre-approved Loan Against Property offer of up to ₹75 lakh. Rahul stated that he solely owned a residential property but did not have the original property documents. The agent explained that he did not meet the eligibility criteria and ended the call.

### Transcript

**Agent - 0:00**

Hello, may I speak with Rahul Sharma?

**Customer - 0:03**

As I am Dalul Sharma.

**Agent - 0:08**

Sorry, I’m calling Rahul Sharma from Home Credit about an existing-customer offer. Is Rahul available to speak?

**Customer - 0:15**

Yes, I am Rahul Sharma.

**Agent - 0:18**

Thank you, Rahul. I’m Priya from Home Credit. As a valued customer, you have a pre-approved Loan Against Property offer of up to ₹75 lakh. I just need a few quick details to see if it suits you.

What type of property do you have - residential, commercial, or industrial?

**Customer - 0:35**

Residential property.

**Agent - 0:38**

Is the property solely owned by you or jointly owned?

**Customer - 0:42**

It's solely owned by me.

**Agent - 0:45**

Do you have the original property documents available for verification?

**Customer - 0:49**

No. I only have the photographs and very clear copies of them.

**Agent - 0:59**

I understand, but original property documents are required for this specific offer. You do not meet the criteria at this time. Thank you for your time.

### Tool Action

At 1:07, the agent called `end_call`.

---

## Test Case 5 - Loan Amount Above the Offer Limit, Customer Accepts

### Conversation Analysis

Rahul Sharma confirmed interest in a Loan Against Property for a residential, solely owned property with original documents available. He initially requested ₹1 crore, accepted the maximum offer amount of ₹75 lakh, and then confirmed that he was salaried with income credited to his bank account. He stated that the property value was approximately ₹1.2 crore and preferred a 10-year tenure. The agent said that a loan expert would follow up.

### Transcript

**Agent - 0:00**

Hello, may I speak with Rahul Sharma?

**Customer - 0:03**

As this is Raul Sharma.

**Agent - 0:08**

Hi Rahul, this is Priya from Home Credit. As a valued customer, you have a pre-approved Loan Against Property offer of up to ₹75 lakh. I just need a few quick details to see if it suits you.

**Customer - 0:21**

Sure. Go ahead.

**Agent - 0:22**

Thank you. What type of property is it - residential, commercial, or industrial?

**Customer - 0:28**

It is residential.

**Agent - 0:30**

Thanks. Is the property solely owned or jointly owned?

**Customer - 0:35**

(Unintelligible audio.)

**Agent - 0:36**

Could you confirm whether it is solely owned or jointly owned?

**Customer - 0:41**

Totally honored by me.

**Agent - 0:44**

Sorry, I didn’t catch that. Is the property solely owned by you, or jointly owned with someone else?

**Customer - 0:50**

Totally honored.

**Agent - 0:53**

Just to confirm, is the property solely owned or jointly owned?

**Customer - 0:59**

Solely owned.

**Agent - 1:01**

Thank you. Are the original property documents available for verification?

**Customer - 1:07**

Yes. I do have all the required original property documents.

**Agent - 1:12**

Great. How much loan amount are you looking for?

**Customer - 1:15**

I need one crore rupees.

**Agent - 1:18**

Could you confirm the loan amount in rupees or lakhs?

**Customer - 1:23**

Hundred lakhs.

**Agent - 1:25**

The maximum available under this offer is ₹75 lakh. Would you like to continue with ₹75 lakh?

**Customer - 1:32**

Oh, is it? Okay. Yes. Seventy-five lakh is fine.

**Customer - 1:35**

Let's continue.

**Agent - 1:36**

Thanks. Are you salaried or self-employed, and is your income credited to your bank account?

**Customer - 1:43**

Salary, my salary is credited to my bank account only.

**Agent - 1:47**

Thank you. What is the approximate current market value of the property?

**Customer - 1:53**

Approximately, one point two crore rupees.

**Agent - 1:55**

Thank you. What loan tenure would you prefer, between 3 and 15 years?

**Customer - 2:01**

Ten years.

**Agent - 2:04**

Thank you, Rahul. I have the details. A senior loan expert will call you back shortly with the exact interest rates and next steps. Have a good day.

### Tool Action

At 2:13, the agent called `end_call`.

---

## 3. Evidence Summary

| Test case | Key behavior demonstrated | Tool action |
| --- | --- | --- |
| Test Case 1 | Complete valid qualification and senior expert handoff | `end_call` |
| Test Case 2 | Immediate agricultural-property disqualification | `end_call` |
| Test Case 3 | Immediate cash-income disqualification | `end_call` |
| Test Case 4 | Immediate disqualification when originals are unavailable | `end_call` |
| Test Case 5 | Correctly caps ₹1 crore request at ₹75 lakh after customer acceptance | `end_call` |

These transcripts support the outcomes recorded in [test_cases.md](test_cases.md). The agent prompt used for these calls is available in [system_prompt.md](system_prompt.md).

