---
name: indirect-tax-compliance-reports
description: List ONESOURCE Indirect Tax Compliance reports, read a report's metadata, and pull its data, polling the cached operation for large results.
api: thomson-reuters:onesource-indirect-tax-compliance-reports-api
operations:
  - Reports_GetReports
  - Reports_GetReportMetdata
  - Reports_GetData
  - Reports_GetOperationStatusFromCache
  - Reports_GetDataFromCache
---
1. `Reports_GetReports` to list the reports available to the integration.
2. `Reports_GetReportMetdata` for the chosen report to learn its parameters and columns.
3. `Reports_GetData` to run it. For long-running results, poll `Reports_GetOperationStatusFromCache`, then read rows with `Reports_GetDataFromCache`.

Rules: the default rate limit is 100 requests per minute per integration and excess calls return HTTP 429 — back off before polling again. Requests carry a bearer token from the ONESOURCE Authorization API. No idempotency key exists; these are reads.
