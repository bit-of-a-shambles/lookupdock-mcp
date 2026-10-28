# LookupDock remote MCP

Connect an MCP client to LookupDock for phone, email and IP checks.

**Remote endpoint:** `https://lookupdock.com/mcp`  
**Transport:** Streamable HTTP  
**Authentication:** your LookupDock bearer API key, or interactive authorization in an OAuth-capable client.

## Setup

1. Create a workspace at [lookupdock.com](https://lookupdock.com/?ref=github-mcp).
2. Create an API key in the workspace. Keep the key in your private client configuration or secret store.
3. Configure a remote Streamable HTTP connection using the endpoint above and `Authorization: Bearer YOUR_LOOKUPDOCK_KEY`. The example JSON is a template; replace its placeholder only in your private copy.
4. Initialize the MCP connection and list tools. Tool availability depends on your workspace and the current [service status](https://lookupdock.com/docs#service-status).

```json
{"mcpServers":{"lookupdock":{"url":"https://lookupdock.com/mcp","headers":{"Authorization":"Bearer YOUR_LOOKUPDOCK_KEY"}}}}
```

Client configuration formats vary. [The live setup guide](https://lookupdock.com/agents) has examples. OAuth resource URLs must match exactly; some clients require the untagged endpoint.

## Tools and limits

| Tool | Input | Result |
| --- | --- | --- |
| `check_phone` | `phone`, optional `country` | Basic numbering-plan signals; current-carrier verification is unavailable. |
| `check_email` | `email` | Format, mail domain, disposable, role and free-provider signals; mailbox existence remains unknown. |
| `check_ip` | `ip` | Location, network/hosting and Tor signals; VPN detection is unknown. |
| `check_signup` | One or more of `email`, `phone`, `ip` | Advisory recommendation and reason codes from the available component checks. |

The optional `idempotency_key` supports retries under the service retention policy. Live tools consume workspace credits; initialization does not run a lookup. Check [pricing](https://lookupdock.com/pricing) before running live checks. Results include uncertainty and do not establish fraud, reachability or a person's identity. Apply your own policy to the signals and submit only data you are entitled to process.

## Status and support

This repository contains connection instructions and listing metadata, not a local server package. Hosted-client compatibility depends on the client and authorization flow; no directory listing or client certification is implied.

- [Documentation](https://lookupdock.com/docs)
- [Privacy](https://lookupdock.com/privacy)
- [Terms](https://lookupdock.com/terms)
- Support: hello@modestambitions.co

Operated by Administrative Burden Ltd, England and Wales company 17363389.
