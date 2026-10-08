# CBU TAAS ReAct Diagnostic Agent - Lab 1

- **Name:** Lakshmi Narayanan S
- **Track:** Agentic AI
- **Lab Name:** Lab 1 — ReAct Agent for QA Diagnostics

---

## What It Does
An autonomous ReAct (Reasoning + Acting) diagnostic agent designed to triage simulated telecom test automation failures in CBU TAAS. It executes a step-by-step diagnostic cycle:
1. Calls mock test log telemetry (`get_test_logs`) to detect failure points.
2. Identifies timeout symptoms and inspects backend service telemetry (`check_endpoint_status`).
3. Diagnoses upstream microservice outages (HTTP 503 / connection pool exhaustion) and outputs an actionable remediation report.

---

## Tools Used
- `google-genai` SDK (`gemini-3.8-flash`)
- `get_test_logs()`: Retrieves test suite execution logs and HTTP timeout traces.
- `check_endpoint_status()`: Inspects service availability, latency, and database connection pool health.

---

## How to Run
1. Open `/src/CBU_TAAS_ReAct_Diagnostic_Agent.ipynb` in Google Colab.
2. Add your Gemini API key in Colab Secrets as `GEMINI_API_KEY` with Notebook access enabled.
3. Run all cells sequentially.

---

## Observations & Output Trace
The agent autonomously reasoned through tool execution:
- Located the HTTP 504 timeout on `/api/v1/billing/charge`.
- Queried the service endpoint and confirmed database pool saturation as the true root cause.
- Produced the complete diagnostic report with targeted database recovery actions.

![Console Trace](screenshots/screenshot.png)
