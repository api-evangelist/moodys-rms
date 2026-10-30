# Moody's RMS

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Moody's RMS is the catastrophe risk modeling and risk-data business of Moody's Corporation, headquartered in Newark, California in its home market of the United States and serving property and casualty insurers, reinsurers, brokers, and capital-market participants worldwide. Founded at Stanford in 1988 as Risk Management Solutions and acquired by Moody's in 2021, the company sells peril models (hurricane, earthquake, flood, wildfire, severe convective storm, terror, cyber, pandemic) and the exposure data infrastructure that carriers use to price, accumulate, and transfer catastrophe risk. Its products run on the cloud-native Intelligent Risk Platform, which fronts Risk Modeler, ExposureIQ, UnderwriteIQ, TreatyIQ, and Risk Data Exchange. Unlike most of the US insurance sector, Moody's RMS is genuinely API-forward: it operates a public, self-serve ReadMe developer portal at developer.rms.com covering Platform APIs, Risk Modeler, Data Bridge, Location Intelligence, and Climate On Demand, publishes downloadable OpenAPI 3.0 definitions and public Postman collections from its own rms-developers GitHub repository, and exposes live REST hosts at api-use1.rms.com and api-euw1.rms.com. Reference documentation is readable without a login, but the APIs themselves are tenant-scoped: keys are issued only to licensed Intelligent Risk Platform tenants, so there is no self-serve signup and no sandbox. Its data-standards posture is cat-risk rather than ACORD — the exchange formats are the RMS EDM/RDM databases, the Risk Data Open Standard (RDOS), and interoperability with CEDE and OED; ACORD appears only as a geocoding-resolution code mapping inside the Location Intelligence API. These are risk-data and analytics APIs, not policy APIs: no quote, bind, issue, or FNOL surface is published.

**Areas:** Insurance · United States · Property and Casualty · Reinsurance · Risk Data · Catastrophe Modeling · Underwriting · Climate Risk · Geocoding · Analytics

## Moody's RMS on APIs.io

Everything profiled for Moody's RMS is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/moodys-rms/](https://apis.io/providers/moodys-rms/)** — or go straight to one of the APIs or properties below.

### APIs (50)

- [Moody's RMS Platform APIs](https://apis.io/apis/moodys-rms/platform-apis/) — A collection of REST APIs that let Intelligent Risk Platform tenants automate portfolio management, underwriting, and risk-transfer workflows across Risk…
- [Moody's RMS Climate On Demand API](https://apis.io/apis/moodys-rms/climate-on-demand-api/) — Physical climate risk data delivered as an API so financial-services organizations can build climate applications on the Intelligent Risk Platform. The…
- [Moody's RMS Platform MCP Server](https://apis.io/apis/moodys-rms/platform-mcp-server/) — A hosted Model Context Protocol server, irp-integration-mcp, released with Intelligent Risk Platform version 2026.07.c on 2026-06-30. It transforms the…
- [Moody's RMS Account V1 API](https://apis.io/apis/moodys-rms/moodys-rms-accountv1-api/) — The AccountV1 API from Moody's RMS — 21 operation(s) for accountv1.
- [Moody's RMS Aggregate PortfolioV1 API](https://apis.io/apis/moodys-rms/moodys-rms-aggregate-portfoliov1-api/) — The Aggregate PortfolioV1 API from Moody's RMS — 12 operation(s) for aggregate portfoliov1.
- [Moody's RMS Aggregate PortfolioV2 API](https://apis.io/apis/moodys-rms/moodys-rms-aggregate-portfoliov2-api/) — The Aggregate PortfolioV2 API from Moody's RMS — 12 operation(s) for aggregate portfoliov2.
- [Moody's RMS Analysis GroupsV1 API](https://apis.io/apis/moodys-rms/moodys-rms-analysis-groupsv1-api/) — The Analysis GroupsV1 API from Moody's RMS — 4 operation(s) for analysis groupsv1.
- [Moody's RMS Analysis GroupsV2 API](https://apis.io/apis/moodys-rms/moodys-rms-analysis-groupsv2-api/) — The Analysis GroupsV2 API from Moody's RMS — 4 operation(s) for analysis groupsv2.
- [Moody's RMS Branch V1 API](https://apis.io/apis/moodys-rms/moodys-rms-branchv1-api/) — The BranchV1 API from Moody's RMS — 2 operation(s) for branchv1.
- [Moody's RMS Cedant V1 API](https://apis.io/apis/moodys-rms/moodys-rms-cedantv1-api/) — The CedantV1 API from Moody's RMS — 2 operation(s) for cedantv1.
- [Moody's RMS Client IP API](https://apis.io/apis/moodys-rms/moodys-rms-client-ip-api/) — The Client IP API from Moody's RMS — 1 operation(s) for client ip.
- [Moody's RMS Cluster API](https://apis.io/apis/moodys-rms/moodys-rms-cluster-api/) — The Cluster API from Moody's RMS — 5 operation(s) for cluster.
- [Moody's RMS Composite API](https://apis.io/apis/moodys-rms/moodys-rms-composite-api/) — Returns multiple layers for an address, including chaining the output of one layer into the input for another
- [Moody's RMS Databases API](https://apis.io/apis/moodys-rms/moodys-rms-databases-api/) — The Databases API from Moody's RMS — 5 operation(s) for databases.
- [Moody's RMS Datasources V1 API](https://apis.io/apis/moodys-rms/moodys-rms-datasourcesv1-api/) — The DatasourcesV1 API from Moody's RMS — 3 operation(s) for datasourcesv1.
- [Moody's RMS Datasources V2 API](https://apis.io/apis/moodys-rms/moodys-rms-datasourcesv2-api/) — The DatasourcesV2 API from Moody's RMS — 3 operation(s) for datasourcesv2.
- [Moody's RMS Datastore V1 API](https://apis.io/apis/moodys-rms/moodys-rms-datastorev1-api/) — The DatastoreV1 API from Moody's RMS — 3 operation(s) for datastorev1.
- [Moody's RMS Datastore V2 API](https://apis.io/apis/moodys-rms/moodys-rms-datastorev2-api/) — The DatastoreV2 API from Moody's RMS — 3 operation(s) for datastorev2.
- [Moody's RMS Domains V1 API](https://apis.io/apis/moodys-rms/moodys-rms-domainsv1-api/) — The DomainsV1 API from Moody's RMS — 8 operation(s) for domainsv1.
- [Moody's RMS Earthquake Hazard Lookup API](https://apis.io/apis/moodys-rms/moodys-rms-earthquake-hazard-lookup-api/) — The Earthquake Hazard Lookup API from Moody's RMS — 40 operation(s) for earthquake hazard lookup.
- [Moody's RMS Exports V1 API](https://apis.io/apis/moodys-rms/moodys-rms-exportsv1-api/) — The ExportsV1 API from Moody's RMS — 2 operation(s) for exportsv1.
- [Moody's RMS Exports V2 API](https://apis.io/apis/moodys-rms/moodys-rms-exportsv2-api/) — The ExportsV2 API from Moody's RMS — 1 operation(s) for exportsv2.
- [Moody's RMS Exposure BatchV3 API](https://apis.io/apis/moodys-rms/moodys-rms-exposure-batchv3-api/) — The Exposure BatchV3 API from Moody's RMS — 1 operation(s) for exposure batchv3.
- [Moody's RMS Exposure SetsV1 API](https://apis.io/apis/moodys-rms/moodys-rms-exposure-setsv1-api/) — The Exposure SetsV1 API from Moody's RMS — 3 operation(s) for exposure setsv1.
- [Moody's RMS File StorageV1 API](https://apis.io/apis/moodys-rms/moodys-rms-file-storagev1-api/) — The File StorageV1 API from Moody's RMS — 8 operation(s) for file storagev1.
- [Moody's RMS Geocoding API](https://apis.io/apis/moodys-rms/moodys-rms-geocoding-api/) — Geocodes an address
- [Moody's RMS Import Upload API](https://apis.io/apis/moodys-rms/moodys-rms-import-upload-api/) — The Import Upload API from Moody's RMS — 3 operation(s) for import upload.
- [Moody's RMS Imports V1 API](https://apis.io/apis/moodys-rms/moodys-rms-importsv1-api/) — The ImportsV1 API from Moody's RMS — 6 operation(s) for importsv1.
- [Moody's RMS Jobs API](https://apis.io/apis/moodys-rms/moodys-rms-jobs-api/) — The Jobs API from Moody's RMS — 2 operation(s) for jobs.
- [Moody's RMS Line of BusinessV1 API](https://apis.io/apis/moodys-rms/moodys-rms-line-of-businessv1-api/) — The Line of BusinessV1 API from Moody's RMS — 2 operation(s) for line of businessv1.
- [Moody's RMS Location V1 API](https://apis.io/apis/moodys-rms/moodys-rms-locationv1-api/) — The LocationV1 API from Moody's RMS — 30 operation(s) for locationv1.
- [Moody's RMS Logins API](https://apis.io/apis/moodys-rms/moodys-rms-logins-api/) — The Logins API from Moody's RMS — 2 operation(s) for logins.
- [Moody's RMS Metrics V2 API](https://apis.io/apis/moodys-rms/moodys-rms-metricsv2-api/) — The MetricsV2 API from Moody's RMS — 27 operation(s) for metricsv2.
- [Moody's RMS Pate V1 API](https://apis.io/apis/moodys-rms/moodys-rms-patev1-api/) — The PateV1 API from Moody's RMS — 2 operation(s) for patev1.
- [Moody's RMS Policy ConditionV1 API](https://apis.io/apis/moodys-rms/moodys-rms-policy-conditionv1-api/) — The Policy ConditionV1 API from Moody's RMS — 1 operation(s) for policy conditionv1.
- [Moody's RMS Policy V1 API](https://apis.io/apis/moodys-rms/moodys-rms-policyv1-api/) — The PolicyV1 API from Moody's RMS — 15 operation(s) for policyv1.
- [Moody's RMS Portfolio V1 API](https://apis.io/apis/moodys-rms/moodys-rms-portfoliov1-api/) — The PortfolioV1 API from Moody's RMS — 16 operation(s) for portfoliov1.
- [Moody's RMS Portfolio V2 API](https://apis.io/apis/moodys-rms/moodys-rms-portfoliov2-api/) — The PortfolioV2 API from Moody's RMS — 16 operation(s) for portfoliov2.
- [Moody's RMS Producer V1 API](https://apis.io/apis/moodys-rms/moodys-rms-producerv1-api/) — The ProducerV1 API from Moody's RMS — 2 operation(s) for producerv1.
- [Moody's RMS Reports V1 API](https://apis.io/apis/moodys-rms/moodys-rms-reportsv1-api/) — The ReportsV1 API from Moody's RMS — 2 operation(s) for reportsv1.
- [Moody's RMS Risk Lookups API](https://apis.io/apis/moodys-rms/moodys-rms-risk-lookups-api/) — Returns one exposure, hazard, risk score, or loss cost layer for an address
- [Moody's RMS Server Instances API](https://apis.io/apis/moodys-rms/moodys-rms-server-instances-api/) — The Server Instances API from Moody's RMS — 3 operation(s) for server instances.
- [Moody's RMS Step PolicyV1 API](https://apis.io/apis/moodys-rms/moodys-rms-step-policyv1-api/) — The Step PolicyV1 API from Moody's RMS — 3 operation(s) for step policyv1.
- [Moody's RMS Treaty V1 API](https://apis.io/apis/moodys-rms/moodys-rms-treatyv1-api/) — The TreatyV1 API from Moody's RMS — 11 operation(s) for treatyv1.
- [Moody's RMS Underwriter V1 API](https://apis.io/apis/moodys-rms/moodys-rms-underwriterv1-api/) — The UnderwriterV1 API from Moody's RMS — 2 operation(s) for underwriterv1.
- [Moody's RMS Utility V1 API](https://apis.io/apis/moodys-rms/moodys-rms-utilityv1-api/) — The UtilityV1 API from Moody's RMS — 6 operation(s) for utilityv1.
- [Moody's RMS Windstorm Hazard Lookup API](https://apis.io/apis/moodys-rms/moodys-rms-windstorm-hazard-lookup-api/) — The Windstorm Hazard Lookup API from Moody's RMS — 14 operation(s) for windstorm hazard lookup.
- [Moody's RMS Workflows V1 API](https://apis.io/apis/moodys-rms/moodys-rms-workflowsv1-api/) — The WorkflowsV1 API from Moody's RMS — 2 operation(s) for workflowsv1.
- [Moody's RMS Account V2 API](https://apis.io/apis/moodys-rms/moodys-rms-account-v2-api/) — The Account V2 API from Moody's RMS — 21 operation(s) for account v2.
- [Moody's RMS Metrics V1 API](https://apis.io/apis/moodys-rms/moodys-rms-metrics-v1-api/) — The Metrics V1 API from Moody's RMS — 24 operation(s) for metrics v1.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [Platform MCP Server](https://apis.io/servers/moodys-rms/irp-integration-mcp/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Moodys Rms Agentic Access](https://apis.io/agentic-access/moodys-rms/moodys-rms-agentic-access/)

#### Collections (2)

Postman and Open Collection request collections.

- [Data Bridge](https://apis.io/collections/moodys-rms/open-moodys-rms-data-bridge/)
- [Risk Modeler](https://apis.io/collections/moodys-rms/open-moodys-rms-risk-modeler/)

#### Overlays (3)

OpenAPI overlays, including conversational phrasing for each operation.

- [Moodys Rms Data Bridge Overlay](https://apis.io/overlays/moodys-rms/moodys-rms-data-bridge-overlay/)
- [Moodys Rms Location Intelligence Overlay](https://apis.io/overlays/moodys-rms/moodys-rms-location-intelligence-overlay/)
- [Moodys Rms Risk Modeler Overlay](https://apis.io/overlays/moodys-rms/moodys-rms-risk-modeler-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Moodys Rms Authentication](https://apis.io/security/moodys-rms/moodys-rms-authentication/)
- [Moodys Rms Domain Security](https://apis.io/security/moodys-rms/moodys-rms-domain-security/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.moodys.com/web/en/us/who-we-serve/insurance.html)
- [Documentation](https://developer.rms.com/)
- [Getting started](https://developer.rms.com/platform/docs/get-started)
- [API reference](https://developer.rms.com/platform/reference)
- [Support](https://support.rms.com/o/html-doc/OLH_Content/SCGuide_Help_Center/Content/SCGuide/Welcome.htm)
- [Terms of service](https://www.moodys.com/web/en/us/legal/terms-of-use.html)
- [Privacy policy](https://www.moodys.com/web/en/us/legal/privacy-policy.html)
- [GitHub](https://github.com/RMS)
- [Status](https://status.rms.com)

## API Evangelist rating

**Kin Score 34.4** — thin · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 71.7 |
| Contract quality | 43.1 |
| Contract governance | 4.5 |
| Operational transparency | 22.4 |
| Developer ergonomics | 43.5 |
| Access clarity | 21.1 |

**Agent readiness 34.7** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | documented (partial credit) |
| Auth Clarity | bearer (partial credit) |
| Idempotency | documented (partial credit) |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | — |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | — |

**Regulatory alignment 21.9** — Insurance

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/moodys-rms/](https://apis.io/providers/moodys-rms/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Moody's RMS: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/moodys-rms/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
