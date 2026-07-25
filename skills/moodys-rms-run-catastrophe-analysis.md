---
name: Run a catastrophe analysis and read the results
description: Submit a portfolio or account for catastrophe model execution on the Intelligent Risk Platform, poll the job to completion, then read EP metrics, ELT/PLT loss tables and summary statistics off the resulting analysis.
api: openapi/moodys-rms-risk-modeler-openapi.yml
generated: '2026-07-25'
method: generated
operations:
  - searchPortfoliosv2
  - getPortfoliov2
  - processPortfolioV2
  - processAggregatePortfoliov2
  - getWorkflowv1
  - getPortfolioAnalysesResultsV2
  - getAnalysesResultsv2
  - getEPMetricsByAnalysisv2
  - getEventLossTableResultsv2
  - getPeriodLossTableResultsv2
  - getStatisticsResultsv2
  - getAALMetricsv2
  - getMetrics
  - runRenameAnalysisv2
---

# Run a catastrophe analysis and read the results

Model execution on the Intelligent Risk Platform is asynchronous. You submit exposure, you get a
job, you poll it, and only then do result resources exist to read.

## Before you start

- Exposure must already be imported into an EDM **and geocoded**. If it is not, see the
  *Import and geocode exposure into an EDM* skill first — an ungeocoded account fails with
  `ACCT-004`.
- Carry the `datasource` query parameter (the EDM name) on every exposure call.
- Send the API key in the `Authorization` header. Regional hosts: `api-use1.rms.com` or
  `api-euw1.rms.com`.

## Steps

1. **Find the exposure.** `searchPortfoliosv2` to locate the portfolio, `getPortfoliov2` to
   confirm it. Use `getDefaultProfilesv2` on an aggregate portfolio to see the ALM profiles
   available to it.

2. **Submit the run.** `processPortfolioV2` analyzes a portfolio;
   `processAggregatePortfoliov2` analyzes an aggregate portfolio; `processAccount` is the
   account-level equivalent and is **deprecated** — use the portfolio path where you can.
   Send a fresh UUID in `x-rms-requestid`.

3. **Poll the job.** `getWorkflowv1` with the id returned by the submit call. Do not start
   reading results until the workflow is terminal. `cancelWorkflowv1` aborts a run.

4. **List the analyses produced.** `getPortfolioAnalysesResultsV2` returns the results attached
   to that portfolio; `getAnalysesResultsv2` searches results across the tenant with
   `q`/`filter`, `sort`, `limit` and `offset`.

5. **Read the loss metrics** against the analysis id:
   - `getEPMetricsByAnalysisv2` — exceedance-probability metrics. Pass `epType` to filter by EP
     metric type; pass `perspective` to select the financial perspective.
   - `getEventLossTableResultsv2` — the ELT.
   - `getPeriodLossTableResultsv2` — the PLT.
   - `getStatisticsResultsv2` — summary statistics.
   - `getAALMetricsv2` — location-level average annual loss.
   - `getMetrics` — the general metrics collection for an analysis.

6. **Post-process where needed.** `marginalImpactv2` measures the differential loss of adding
   accounts to an existing portfolio. `convertResultCurrencyv2` restates results in another
   currency. `runClimateChangev2` recalculates under a climate-change view.

7. **Label and tidy.** `runRenameAnalysisv2` renames a result; `deleteAnalysesv2` removes
   results you no longer need. Both are cheap compared to re-running the model.

## Rules

- **Everything expensive is a job.** Model runs, geohaz, import, export, accumulation and
  currency conversion all return an id you poll. Nothing streams and there are no webhooks —
  the platform publishes no event or AsyncAPI surface.
- **Idempotency.** `x-rms-requestid` with a client-generated UUID makes a `POST` safe to retry.
  A retried model submission without one can start a second expensive run.
- **Errors.** `{code, message, logId}` in `application/json`. `ANALYSIS-*`, `ENGINE-*` and
  `JOB-*` codes are the ones to expect here — see `errors/moodys-rms-error-codes.yml`.
- **Deprecations.** `getAnalysesResults`, `getPortfolioAnalysesResults`, `getAccountAnalysesResults`,
  `processPortfolio`, `processAccount`, `downloadResults`, `exportDatav1` and
  `getAggregateExposureListsv1` are all marked deprecated in the specification. Deprecated
  operations stay live for one year and announce themselves in a `Warning` header.
