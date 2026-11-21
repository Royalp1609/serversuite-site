# Billing API

For billing systems such as [Paymenter](https://paymenter.org): the things they sell on top of a
server. Mods, modpacks and versions aren't sold, so they aren't in the API; customers use the
panel pages for those.

Use the panel's own **application API keys** (**Admin →
Application API**). Reads need **Servers: Read**, changes need **Servers: Read & Write**.
`{server}` is the panel's server id, or `external:<id>` for the billing system's service id (the
server's `external_id`).

| Method | Path | Body |
|---|---|---|
| GET | `/api/application/serversuite/servers/{server}` | — returns subdomains (allowance, used, `over_allowance`, names), loader/version, backup plan and next run |
| PUT | `/api/application/serversuite/servers/{server}/subdomains` | `{"allowance": 2}` (0-100). Lowering it never removes subdomains; `over_allowance` says so |
| PUT | `/api/application/serversuite/servers/{server}/backups` | `{"enabled": true, "interval_hours": 24, "hour": 4, "keep": 5}` (`hour` 0-23 in the backup timezone, or null; `keep` is capped by the server's backup limit) |

- Every write is safe to repeat: the same request twice changes nothing.
- Real changes go to the server's Activity log as the API key's owner.
- Errors use the panel's normal JSON error format.

Example:

```bash
curl -X PUT https://panel.example.com/api/application/serversuite/servers/external:1234/subdomains \
  -H "Authorization: Bearer <application API key>" \
  -H "Content-Type: application/json" -H "Accept: application/json" \
  -d '{"allowance": 2}'
```
