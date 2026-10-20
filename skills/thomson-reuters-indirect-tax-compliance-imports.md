---
name: indirect-tax-compliance-imports
description: Upload and process a data import into ONESOURCE Indirect Tax Compliance, track its status, and rerun or delete it.
api: thomson-reuters:onesource-indirect-tax-compliance-imports-api
operations:
  - IndirectTaxImports_imports
  - IndirectTaxImports_uploadData
  - IndirectTaxImports_ImportData
  - IndirectTaxImports_FetchUploadStatus
  - IndirectTaxImports_ProcessImport
  - IndirectTaxImports_FetchStatus
  - IndirectTaxImports_ImportRerun
  - IndirectTaxImports_DeleteImportData
---
1. `IndirectTaxImports_imports` to list supported imports.
2. `IndirectTaxImports_uploadData` (or `IndirectTaxImports_ImportData`) to send the file; poll `IndirectTaxImports_FetchUploadStatus`.
3. `IndirectTaxImports_ProcessImport`, then poll `IndirectTaxImports_FetchStatus` until it completes.
4. On failure use `IndirectTaxImports_ImportRerun`; to back out, `IndirectTaxImports_DeleteImportData`.

Rules: no idempotency key is documented, so check status before re-submitting an upload to avoid duplicates. Retry HTTP 429 with exponential backoff.
