# Moody's RMS (moodys-rms)

Moody's RMS is the catastrophe risk modeling and risk-data business of Moody's Corporation, headquartered in Newark, California in its home market of the United States and serving property and casualty insurers, reinsurers, brokers, and capital-market participants worldwide. Founded at Stanford in 1988 as Risk Management Solutions and acquired by Moody's in 2021, the company sells peril models and the exposure data infrastructure that carriers use to price, accumulate, and transfer catastrophe risk. Its products run on the cloud-native Intelligent Risk Platform, which fronts Risk Modeler, ExposureIQ, UnderwriteIQ, TreatyIQ, and Risk Data Exchange.

Unlike most of the US insurance sector — which has no federal regulator, no open-insurance mandate, and almost no public API surface — Moody's RMS is genuinely API-forward. It operates a public, self-serve developer portal at [developer.rms.com](https://developer.rms.com/), publishes downloadable OpenAPI 3.0 definitions and public Postman collections from its own [rms-developers](https://github.com/RMS/rms-developers) GitHub repository, and exposes live REST hosts at `api-use1.rms.com` and `api-euw1.rms.com`. Documentation is readable without a login, but the APIs themselves are tenant-scoped: keys are issued only to licensed Intelligent Risk Platform tenants, so there is no self-serve signup and no sandbox.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/moodys-rms/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/moodys-rms/refs/heads/main/apis.yml)

## Tags

- Insurance
- United States
- Property and Casualty
- Reinsurance
- Risk Data
- Catastrophe Modeling
- Underwriting
- Climate Risk
- Geocoding
- Analytics

## Timestamps

- **Created:** 2026-07-25
- **Modified:** 2026-07-25

## APIs

### Moody's RMS Platform APIs

A collection of REST APIs that let Intelligent Risk Platform tenants automate portfolio management, underwriting, and risk-transfer workflows across Risk Modeler, UnderwriteIQ, TreatyIQ, ExposureIQ, and Risk Data Exchange. The public reference is segmented into roughly two dozen families including Import, Export, Batch, Model, Accumulation, Rollup, Grouping, Geohaz, Bulk Geohazard, Enrich Exposure, Currency Conversion, Auto Select, Clone, Copy, ESG Data, Exchange Data, Reference Data, Risk Data, Admin Data, Tenant Data, Security, STEP, and Variation. No downloadable OpenAPI definition was published for this family at the time of review.

- **Human URL:** [https://developer.rms.com/platform](https://developer.rms.com/platform)

#### Properties

- [Documentation](https://developer.rms.com/platform/docs)
- [API Reference](https://developer.rms.com/platform/reference)
- [Postman Workspace](https://www.postman.com/rms-developers/rms-developers/overview)

### Moody's RMS Risk Modeler API

The Risk Modeler 2.0 public API — the legacy catastrophe-modeling and underwriting surface of the Intelligent Risk Platform, superseded by the Platform APIs but still documented and specified. The harvested OpenAPI 3.0.1 definition carries 280 paths covering exposure and EDM/RDM management, account and portfolio data, model profiles, analysis runs, results and metrics, imports and exports, geohazard lookups, and job orchestration.

- **Human URL:** [https://developer.rms.com/risk-modeler](https://developer.rms.com/risk-modeler)
- **Base URL:** `https://api-use1.rms.com/riskmodeler`

#### Properties

- [Documentation](https://developer.rms.com/risk-modeler)
- [API Reference](https://developer.rms.com/risk-modeler/reference)
- [OpenAPI](openapi/moodys-rms-risk-modeler-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](https://github.com/RMS/rms-developers/blob/master/.assets/rm/rm2-postman.zip)

### Moody's RMS Data Bridge API

Administers database connections and moves exposure and results data into and out of the Intelligent Risk Platform. The harvested OpenAPI 3.0.1 definition carries 21 paths covering database and server management, EDM/RDM database creation and deletion, upload and download of exposure databases, and the job status endpoints that track those transfers.

- **Human URL:** [https://developer.rms.com/databridge](https://developer.rms.com/databridge)
- **Base URL:** `https://api-use1.rms.com/databridge`

#### Properties

- [Documentation](https://developer.rms.com/databridge)
- [API Reference](https://developer.rms.com/databridge/reference)
- [OpenAPI](openapi/moodys-rms-data-bridge-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### Moody's RMS Location Intelligence API

Address geocoding and per-location peril and hazard risk lookups used to enrich exposure before modeling. The harvested OpenAPI 3.0.1 definition carries 366 paths under three declared tags — Geocoding, Composite, and Risk Lookups — returning geocode resolution (including a code mapped to the ACORD standard resolution scale), hazard scores, and peril-specific risk attributes by location.

- **Human URL:** [https://developer.rms.com/location-intelligence](https://developer.rms.com/location-intelligence)
- **Base URL:** `https://api-use1.rms.com/li`

#### Properties

- [Documentation](https://developer.rms.com/location-intelligence)
- [API Reference](https://developer.rms.com/location-intelligence/reference)
- [OpenAPI](openapi/moodys-rms-location-intelligence-openapi.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](https://github.com/RMS/rms-developers/blob/master/.assets/li/li-postman.json.zip)

### Moody's RMS Climate On Demand API

Physical climate risk data delivered as an API so financial-services organizations can build climate applications on the Intelligent Risk Platform. The public developer page documents four product surfaces — CoD Real Assets Stn, CoD Real Assets Pro, CoD Corporates, and CoD Spatial Areas — and offers a public Postman collection. No downloadable OpenAPI definition was found for this family at the time of review.

- **Human URL:** [https://developer.rms.com/climate-on-demand](https://developer.rms.com/climate-on-demand)

#### Properties

- [Documentation](https://developer.rms.com/climate-on-demand)
- [Postman Collection](https://www.postman.com/rms-developers/workspace/cod/collection/21620294-578a748b-78a6-4a3a-b4b3-5c5380b7848e)

## API Posture

- **Developer portal:** [https://developer.rms.com/](https://developer.rms.com/) — HTTP 200, a real self-serve ReadMe documentation hub, publicly readable with no login wall.
- **Specifications harvested:** 3 OpenAPI 3.0.1 documents, 667 paths total, taken verbatim from the vendor's own [rms-developers](https://github.com/RMS/rms-developers) repository on 2026-07-25.
- **Authentication:** API key in the `Authorization` header (`RMS_Auth`), issued to licensed Intelligent Risk Platform tenants. No OAuth2, no mTLS, no OpenID discovery document.
- **ACORD posture:** No ACORD transactional surface. Exchange runs on the company's own cat-risk stack — EDM/RDM databases, the Risk Data Open Standard (RDOS), and interoperability with CEDE and OED. ACORD appears exactly once across all harvested specs, as a geocode-resolution code mapping in the Location Intelligence API.
- **Quote / bind / issue / FNOL:** None exposed. This is risk-data and catastrophe analytics, consumed by carrier and reinsurer analytics teams, not a policy-transaction surface.
- **Webhooks / events:** None. Long-running work uses a polling job model.
- **Home market:** United States.

## Common Properties

- [Website](https://www.moodys.com/web/en/us/who-we-serve/insurance.html)
- [Documentation](https://developer.rms.com/)
- [Developer Portal](https://developer.rms.com/)
- [GitHub Organization](https://github.com/RMS)
- [Postman Workspace](https://www.postman.com/rms-developers/rms-developers/overview)
- [API Reference](https://developer.rms.com/platform/reference)

## Maintainers

- Kin Lane — kin@apievangelist.com
