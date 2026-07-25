---
name: Import and geocode exposure into an EDM
description: Upload an exposure file to the Intelligent Risk Platform, import it into an EDM database as a portfolio and accounts, then run geohazard enrichment so the exposure is ready to model.
api: openapi/moodys-rms-risk-modeler-openapi.yml
generated: '2026-07-25'
method: generated
operations:
  - searchEdms
  - getUrlForUpload
  - CreateUploadTask
  - createJob
  - getWorkflowv1
  - searchPortfoliosv2
  - createPortfoliov2
  - managePortfolioAccountsv2
  - geohazPortfoliov2
  - validateAccountv2
---

# Import and geocode exposure into an EDM

Exposure has to be inside an EDM (Exposure Data Module) database and geocoded before any
catastrophe model will run against it. This skill covers that path end to end.

## Before you start

- Get the host and API key from your tenant administrator. Hosts are regional:
  `api-use1.rms.com` (Americas) or `api-euw1.rms.com` (Europe). There is no self-serve signup
  and no sandbox — an unauthenticated call returns `401`.
- Send the key in the `Authorization` header on every request, with no bearer prefix.
- Almost every Risk Modeler operation takes a `datasource` query parameter naming the EDM you
  are working in. Resolve it first and carry it through.
- Every `POST` here is a job. Submit, take the id from the response, then poll. Do not assume
  a `202 Accepted` means the work finished.

## Steps

1. **Pick the EDM.** Call `searchEdms` to list the exposure databases the key can reach, and
   choose the one you will pass as `datasource` for the rest of the flow.

2. **Get an upload location.** Call `getUrlForUpload` to obtain the storage bucket URL and
   upload id for the file transfer.

3. **Upload the EDM file.** Call `CreateUploadTask` with that upload id. (Use
   `CreateUploadTaskForRdm` instead when you are loading analysis results rather than exposure.)

4. **Start the import.** Call `createJob` to import exposures from the uploaded file. Send an
   `x-rms-requestid` header holding a UUID you generate — `POST` is not idempotent by default,
   and this key makes the retry safe if the response never arrives.

5. **Poll to completion.** Call `getWorkflowv1` with the returned id until the workflow reports
   a terminal state. `getWorkflowsv1` lists in-flight work; `cancelWorkflowv1` aborts it.

6. **Confirm or create the portfolio.** Call `searchPortfoliosv2` to find the imported
   portfolio, or `createPortfoliov2` to create one, then `managePortfolioAccountsv2` to attach
   accounts to it.

7. **Validate before you spend model time.** Call `validateAccountv2` on the accounts you care
   about. Unvalidated or ungeocoded exposure is the most common cause of a failed analysis —
   the error catalog returns `ACCT-004` ("No geocoded locations exist in account ...") for
   exactly this.

8. **Geocode and enrich.** Call `geohazPortfoliov2` to run geohazard enrichment over the whole
   portfolio (or `geohazAccountv2` for a single account). This is another job — poll it with
   `getWorkflowv1`.

## Rules

- **Idempotency.** Put a fresh UUID in `x-rms-requestid` on every `POST` and `PATCH`. Reuse the
  *same* key when retrying an unacknowledged request. Generate a *new* key after a `400`, once
  you have corrected the body. A `409 Conflict` means the original request is still processing —
  wait and retry rather than resubmitting.
- **Errors.** The body is `{code, message, logId}`, not RFC 9457 problem+json. Match on `code`
  (for example `ACCT-002` for a permissions problem), and quote `logId` in any support ticket.
  See `errors/moodys-rms-error-codes.yml`.
- **Paging.** List operations take `limit` and `offset`, plus `q`/`filter` and `sort`.
- **Versions.** Prefer the `v2` operations. `v1` equivalents such as `processPortfolio` are
  marked deprecated in the specification and are supported for one year after deprecation.
