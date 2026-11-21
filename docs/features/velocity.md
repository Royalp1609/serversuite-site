# Velocity networks

Put servers behind a **Velocity** proxy without editing configs by hand.

1. Switch a server to Velocity on its [Versions](versions.md) page.
2. On the Velocity server's **Velocity** page, tick the servers to put behind it, give each the
   name Velocity uses, and set the order players are tried in.
3. **Apply**.

That writes `velocity.toml` (the `[servers]` table and `try` list, modern forwarding with the
proxy's own secret) and, on each backend, the forwarding secret and `online-mode=false`: Paper,
Purpur and Folia through `config/paper-global.yml`, Fabric and Quilt through FabricProxy-Lite.

- Every server reports what changed, or what you still need to do (start it once, install
  FabricProxy-Lite; Forge and NeoForge need setting up by hand).
- If applying fails, the changes are rolled back.
- Taking a server out of the network sets it back.
- Restart everything after applying, and point your [subdomain](subdomains.md) at the proxy.

Only the servers' owner (or a root admin) sees this page, and all servers must belong to the same
owner.
