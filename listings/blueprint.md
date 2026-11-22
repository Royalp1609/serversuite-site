# Blueprint extension listing (Pterodactyl)

**Name:** Server Suite
**Identifier:** `serversuite`
**Licence:** AGPL-3.0-only · free
**Requires:** Pterodactyl 1.14 or 1.15 · Blueprint beta-2026-08+ (1.15) · plus the Server Suite
backend Composer package (both files are on every release)
**Links:** Website `https://royalp1609.github.io/serversuite-site/` · Install guide `https://royalp1609.github.io/serversuite-site/install/pterodactyl/` · Source `https://github.com/royalp1609/serversuite-pterodactyl`

## Short description
Mod manager, modpacks, scheduled backups, version switching, configs, players and Cloudflare
subdomains as new server tabs.

## Description
Server Suite adds the tools Minecraft server owners ask for, as tabs on every server.

- **Mods**: Modrinth, CurseForge (with an API key) and Hangar, filtered to the server's loader
  and version. Dependencies resolved, install queue, bulk update and remove, files found on disk
  adopted, and Wings downloads everything straight to the server.
- **Modpacks**: Modrinth `.mrpack` install and update, reviewed first, with a backup.
- **Backups**: schedules from every 6 hours to weekly at a fixed hour, rotation that keeps locked
  backups, and mod lists restored with the backup.
- **Versions**: change version or loader (Paper, Purpur, Folia, Fabric, Quilt, Forge, NeoForge,
  Velocity), always behind a recent backup, with opt-in automatic upgrades and a world or full
  reset.
- **Configs** and **Properties**: config files and `server.properties` as forms.
- **Players**, **Errors**, **Notifications** (Discord/ntfy), **Velocity** networks and **Bedrock
  crossplay** (Geyser + Floodgate in one click).
- **Subdomains**: Cloudflare A/AAAA + SRV records on the panel's domains or the owner's own, with
  public status cards and badges.
- **Admin**: repositories, update checks, backups, an Egg Manager for the community egg catalogue,
  subdomain domains and allowances.

Uses Pterodactyl's own subuser permissions (new **Mods** and **Subdomains** groups).

## Install
Install the backend package first (`composer require`), then `blueprint -install serversuite`.
Full steps: `https://royalp1609.github.io/serversuite-site/install/pterodactyl/`.

## Screenshots (in order)
1. `pterodactyl/mods-browse.png`
2. `pterodactyl/mods-manage.png`
3. `pterodactyl/configs-form.png`
4. `pterodactyl/versions.png`
5. `pterodactyl/backups.png`
6. `pterodactyl/players.png`
7. `pterodactyl/subdomains.png`
8. `pterodactyl/admin-settings.png`
