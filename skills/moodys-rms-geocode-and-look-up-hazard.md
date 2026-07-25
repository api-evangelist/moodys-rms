---
name: Geocode an address and look up peril hazard
description: Use the Location Intelligence API to resolve an address to coordinates with a stated resolution, then read per-peril hazard and risk attributes for that location — either one layer at a time or in a single composite call.
api: openapi/moodys-rms-location-intelligence-openapi.yaml
generated: '2026-07-25'
method: generated
operations:
  - composite
  - genericLookup
---

# Geocode an address and look up peril hazard

Location Intelligence answers two questions for a single location: *where exactly is it* and
*what perils threaten it*. It is the enrichment step that runs before exposure is modeled, and
it can also be called standalone for underwriting triage.

## Before you start

- API key in the `Authorization` header. Regional host `api-use1.rms.com` or `api-euw1.rms.com`,
  app path `/li`.
- This surface is **path-versioned by data vintage**, not by API version. A layer is addressed as
  `/{layer}/{version}` — for example `/geocode/22.0`, `/geocode/latest`, `/ac_eq_hazard/18.1`.
  Pin an explicit vintage when you need reproducible results; use `latest` when you want the
  current geocoding engine.

## Steps

1. **Decide one call or many.** `composite` (`POST /composite`) takes a location — address plus
   building characteristics — and returns geocode *and* the requested hazard layers in a single
   round trip. Prefer it for per-risk underwriting lookups.

2. **Or call layers individually.** `genericLookup` (`POST /{layer}/{version}`) is the single
   generic operation behind all 363 layer endpoints. Set `layer` to the peril or reference layer
   and `version` to the data vintage.

3. **Geocode.** Use the `geocode` layer. The response carries the resolved coordinates and a
   `rmsGeocodingResolutionCode` — the one place in this whole platform where ACORD appears, as
   the code mapped to the ACORD standard resolution scale. Treat resolution as a first-class
   result: a country-centroid match and a rooftop match are not the same risk.

4. **Look up hazard by peril.** Layers are named `<region>_<peril>_hazard` — for example
   `ac_eq_hazard` (Central America earthquake), `ah_eq_hazard` (South America earthquake),
   `au_eq_hazard` (Australia earthquake), and the windstorm equivalents. Each declares the
   tagged families `Earthquake Hazard Lookup`, `Windstorm Hazard Lookup` and `Risk Lookups`.

5. **Feed the result forward.** In a modeling flow, this data is what `geohazPortfoliov2` and
   `geohazAccountv2` in the Risk Modeler API apply in bulk. Use Location Intelligence directly
   for one-off or pre-import lookups; use geohaz jobs once the exposure is in an EDM.

## Rules

- **Only two operations carry an `operationId`.** 363 of 365 Location Intelligence operations
  declare none, so tooling cannot address them by id — address them by path. This is the single
  biggest contract-quality gap in the Moody's RMS surface.
- **Errors.** Every operation declares `400`, `401`, `404` and `500`. The body is the vendor
  `{code, message, logId}` envelope; `GEO_SERVICE-*` and `GE-*` codes are the ones to expect.
  See `errors/moodys-rms-error-codes.yml`.
- **Idempotency.** These lookups are `POST` but semantically read-only. Still send
  `x-rms-requestid` so a retried request is recognized as the same request.
- **Vintages are data, not versions.** `18.0`, `18.1`, `20.0`, `21.0`, `22.0`, `25.0` and
  `latest` are geocoding-engine and hazard-data releases. Changing vintage changes answers, so
  record the one you used alongside the result.
