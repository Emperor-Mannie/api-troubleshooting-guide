# Postman Exercise: Investigating a Failed Payment API Request

## 1. Objective

This exercise demonstrates a structured approach to investigating payment API failures using Postman.

The scenarios are simulated and use fictional payment data. They are designed to demonstrate practical API troubleshooting and customer support skills.

## 2. Scenario

A customer reports that a payment request was submitted through an application, but the payment was not completed.

The support team needs to investigate the request, identify possible causes and determine whether the issue requires escalation.

## 3. Sample API Request

**Method:** POST

**Example endpoint:** `https://postman-echo.com/post`

**Headers:**

```http
Content-Type: application/json
```

**Request body:**

```json
{
  "customer_id": "CUS-10001",
  "invoice_id": "INV-2026-001",
  "amount": 25000,
  "currency": "NGN",
  "payment_reference": "PAY-10001"
}
```

Note: Postman Echo is used to demonstrate request inspection. It does not process actual payments.

## 4. Investigation Procedure

### Step 1: Validate the request

- Confirm that the HTTP method is correct.
- Confirm that the endpoint is correct.
- Check that the required headers are present.
- Validate the JSON structure.
- Confirm that mandatory fields are included.
- Check that the amount and currency use the expected format.

### Step 2: Submit the request

Send the request through Postman and inspect the response.

Review:
- HTTP status code.
- Response body.
- Response headers.
- Response time.
- Any returned error message.

### Step 3: Interpret possible responses

| Status code | Meaning | Support investigation |
|---|---|---|
| 200 | Successful request | Confirm the response contains the expected data |
| 400 | Bad request | Inspect request structure and parameters |
| 401 | Unauthorised | Check authentication and token validity |
| 403 | Forbidden | Check permissions and access restrictions |
| 404 | Not found | Verify the endpoint or resource identifier |
| 422 | Unprocessable entity | Inspect field validation and business rules |
| 500 | Internal server error | Gather evidence and escalate for backend investigation |

A successful HTTP response does not necessarily prove that a payment has settled. Confirm the actual transaction status through the appropriate payment system.

## 5. Simulated Investigation Cases

### Case A: Invalid request data

**Customer complaint:** Payment request rejected.

**Possible finding:** A required field is missing or the amount is supplied in an invalid format.

**Investigation:**
- Inspect the JSON body.
- Compare the submitted fields with the API documentation.
- Validate the amount and currency.
- Correct the request only after confirming the expected format.

**Outcome:** Identify and document the invalid field.

### Case B: Authentication failure

**Customer complaint:** API request returns an authorisation error.

**Possible finding:** The authentication token is missing, expired or invalid.

**Investigation:**
- Inspect the request headers.
- Confirm the expected authentication method.
- Check token validity through an authorised process.
- Never request or expose a customer's secret key or password.

**Outcome:** Identify whether authentication is responsible and escalate if required.

### Case C: Server-side failure

**Customer complaint:** Payment request returns an internal server error.

**Possible finding:** The request reaches the service, but the backend encounters an error.

**Investigation:**
- Record the request timestamp.
- Capture the HTTP status code.
- Record the endpoint and request method.
- Preserve the response body, excluding sensitive information.
- Check whether the issue is reproducible.
- Escalate with the available evidence.

**Outcome:** Provide Engineering with enough information to investigate.

## 6. Technical Escalation Template

**Issue:** Payment API request failure

**Environment:** Test environment

**Endpoint:** [Insert endpoint]

**HTTP Method:** POST

**Timestamp:** [Insert timestamp]

**Status Code:** [Insert status code]

**Expected Behaviour:** Payment request should be accepted and return the expected response.

**Actual Behaviour:** [Describe the observed response]

**Investigation Performed:**
- Request method and endpoint verified.
- Request headers inspected.
- JSON payload validated.
- Response code and body reviewed.
- Issue reproduction attempted.

**Evidence:** Sanitised request and response samples.

**Support Assessment:** [Document findings and possible cause without presenting an unverified hypothesis as confirmed.]

**Action Required:** Further technical investigation where necessary.

## 7. Key Support Principles

- Reproduce reported issues before concluding.
- Validate inputs before escalating.
- Distinguish HTTP request success from actual payment settlement.
- Protect authentication credentials and customer information.
- Provide clear evidence when escalating.
- Keep customers informed using accurate, non-technical explanations where appropriate.
- Document findings and resolution steps.

## 8. Disclaimer

This is a simulated technical support exercise created for professional learning and portfolio demonstration. It does not represent an actual payment incident or a production payment integration.
