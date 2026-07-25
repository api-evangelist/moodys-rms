---
name: Move EDM and RDM databases with Data Bridge
description: Provision a database on a Data Bridge SQL Server instance, move an EDM or RDM in or out of the Intelligent Risk Platform with multipart upload or export-to-URI, and administer the network ACL and logins that gate it.
api: openapi/moodys-rms-data-bridge-openapi.json
generated: '2026-07-25'
method: generated
operations:
  - getinstances
  - getinstance
  - createdatabase
  - getdatabasesbyinstance
  - getdatabasebyinstance
  - getuploaddirectoryuri
  - initiatemultipartupload
  - geturiformultipartupload
  - uploaddatapartbynumber
  - completemultipartupload
  - importdatabase
  - exportdatabase
  - getjobstatus
  - getjobdetails
  - getclientip
  - getipaddresses
  - updateacl
  - identifyencryptedconnection
---

# Move EDM and RDM databases with Data Bridge

Data Bridge is the plumbing under the Intelligent Risk Platform: it administers SQL Server
instances and moves whole EDM and RDM databases in and out. Use it when you are moving a
*database*, not individual exposure records.

## Before you start

- API key in the `Authorization` header; regional host `api-use1.rms.com` or `api-euw1.rms.com`;
  the Data Bridge app path is `/databridge`.
- Your client IP must be allowed through the Data Bridge ACL before a connection will succeed.

## Steps

1. **Open the network path.** `getclientip` returns the IP the platform sees you from.
   `getipaddresses` lists the currently allowed addresses, and `updateacl` adds yours.
   `overwriteacl` replaces the whole list — prefer `updateacl` unless you mean to reset it.
   `deleteipaddress` and `deleteipaddresses` remove single addresses or a CIDR range.
   `identifyencryptedconnection` reports the cluster's security posture and
   `settlsprotocolversion` sets the TLS protocol version.

2. **Find the server instance.** `getinstances` lists the SQL Server instances the tenant owns;
   `getinstance` returns one. `getdatabasesbyinstance` lists the databases on it and
   `getdatabasebyinstance` returns a single database.

3. **Create the target database.** `createdatabase` provisions a new EDM or RDM on the chosen
   instance. `pindatabase` pins one so it is not reclaimed.

4. **Upload.** For a straightforward transfer, `getuploaddirectoryuri` returns the upload
   directory URI and `importdatabase` imports the database from a flat file. For large files use
   the multipart sequence: `initiatemultipartupload`, then per part
   `geturiformultipartupload` (pre-signed URL) and `uploaddatapartbynumber`, then
   `completemultipartupload`.

5. **Download.** `exportdatabase` exports a database to a URI you supply.

6. **Poll.** Every transfer is a job. `getjobstatus` returns the state of a job id;
   `getjobdetails` returns the detail record — read it when a job fails, because the failure
   reason lives there and not in the status.

7. **Grant access.** `getgroupbydatabase` and `updategroupaccess` control which groups reach a
   database; `getgroupsbyinstance` and `updategroupaccessbyinstance` do the same at instance
   level. `createlogin`, `updateloginpassword` and `deleteinstancelogin` manage SQL logins.

## Rules

- **These are destructive operations on real tenant data.** `deletedatabase`-class calls,
  ACL overwrites and login deletion have no undo. Confirm the instance and database name against
  `getdatabasesbyinstance` before you act.
- **Idempotency.** Use `x-rms-requestid` with a client-generated UUID on `POST` and `PATCH`.
  Re-issuing a multipart upload initiation without one can strand a partial upload.
- **Errors.** Data Bridge declares `400`, `403`, `404`, `409`, `410` and `500` responses. The
  body is the vendor `{code, message, logId}` envelope; `DATA-BRIDGE-*`, `DATABASE_STORE-*` and
  `DBM-*` codes are the ones to expect. See `errors/moodys-rms-error-codes.yml`.
- **Registration.** A database moved in with Data Bridge still has to be registered with Risk
  Modeler before it is usable there — `registerDatabaseV2` in the Risk Modeler API.
