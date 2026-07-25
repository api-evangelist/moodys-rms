---
name: Connect an agent to the Platform MCP Server
description: Configure an MCP host against Moody's RMS irp-integration-mcp, then use the knowledge-graph and discovery tools to find the right Platform API operations before dispatching them through execute-api.
api: mcp/moodys-rms-mcp.yml
generated: '2026-07-25'
method: generated
operations:
  - graph-suggest-workflow
  - graph-validate-chain
  - search-api-spec
  - get-operation-spec
  - get-workflow
  - execute-api
  - set-variable
  - get-variables
---

# Connect an agent to the Platform MCP Server

Moody's RMS ships a real, hosted MCP server — `irp-integration-mcp`, released in 2026.07.c. It
is a *meta-tool* server: fifteen of its sixteen tools reason over a knowledge graph built from
the Platform API specifications and docs, and exactly one — `execute-api` — actually calls the
platform. Use the graph to decide what to call, then call it.

## Before you start

- You need an Intelligent Risk Platform API key issued by your tenant administrator, and that
  key must belong to a user group assigned the **IRP Agentic Tools User** role. Without that
  role, connection fails; without its write permission, `execute-api` is unavailable.
- Pick the endpoint matching your data centre:
  - Americas: `https://api-use1.rms.com/platform/integration/v1/mcp`
  - Europe: `https://api-euw1.rms.com/platform/integration/v1/mcp`
- Transport is Streamable HTTP; the key goes in an `Authorization` header.

## Steps

1. **Register the server.** In Claude Code:

   ```bash
   claude mcp add --transport http irp-integration-mcp \
     https://api-use1.rms.com/platform/integration/v1/mcp \
     --header "Authorization: YOUR_IRP_API_KEY"
   ```

   Claude Desktop, Cursor, Devin, JetBrains AI Assistant and VS Code take the equivalent JSON
   block — see `mcp/moodys-rms-mcp.yml` for each. Verify with `claude mcp list`.

2. **Set session context.** `set-variable` stores the host and credentials for the session;
   `get-variables` lists what is set. Do this once rather than repeating context per call.

3. **Ask the graph what to do, before you call anything.** `graph-suggest-workflow` turns a
   stated goal ("run a hurricane analysis on this portfolio and get EP metrics") into a proposed
   chain of Platform API operations. `vector-search` finds operations by semantic similarity;
   `graph-find-related` and `graph-explore` walk upstream and downstream from an operation.

4. **Check the chain is real.** `graph-validate-chain` tests whether the proposed workflow is
   feasible. Do this before executing anything — it is far cheaper than a failed model run.

5. **Read the contract.** `search-api-spec` searches the Platform API specifications by
   operation, description, endpoint or resource; `get-operation-spec` returns the complete
   specification for one operation. That specification — not a guess — is the input contract for
   the call you are about to make.

6. **Fetch a runnable workflow.** `search-workflows` searches the workflow library and
   `get-workflow` returns a complete runnable collection. `graph-get-workflow` returns proven
   patterns from the graph. `get-doc-context` pulls the developer documentation for an operation
   or a chain.

7. **Execute.** `execute-api` runs the Platform API operation, subject to the roles on the key.
   This is the only tool that mutates tenant state.

## Rules

- **The tool list is not the API surface.** There is no tool per endpoint. All 780 published REST
  operations, plus the ~24 undocumented-as-OpenAPI Platform API families, are reachable only
  through `execute-api`. See `mcp/moodys-rms-tool-crosswalk.yml`.
- **Entitlements still apply.** Role-based access controls decide which operations `execute-api`
  can reach. A tool being listed does not mean the caller can run every operation behind it.
- **Data stays put.** All tenant data remains on the Intelligent Risk Platform; nothing is
  duplicated or moved into an AI environment outside it.
- **Skill tools are beta.** `skill-workflow-assist` (which requires MCP sampling support in the
  host) and `skill-fetch-api-data` are pre-launch; do not build production flows on them yet.
- **Live introspection is gated.** An anonymous `tools/list` against the endpoint returns
  `401 Unauthorized`, so per-tool input schemas are only visible to an authenticated tenant.
