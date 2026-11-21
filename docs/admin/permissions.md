# Permissions

Server Suite uses the panel's own permission system. Server owners and root admins can do
everything. Subusers get exactly what you tick, and each page only shows for subusers holding one
of its permissions. Buttons they can't use are hidden, and the server checks every request too.

## Server pages

| Page | To see it | To change things |
|---|---|---|
| Mods | Mods: read | install, update, remove; *configure* to adopt or forget files found on disk |
| Configs | File: read content | File: update |
| Modpacks | Mods: read | installing or updating a pack needs Mods install + remove and Control: stop |
| Backups | Backup: read | create (back up now, rename), delete (delete, lock), restore, download; the schedule needs create + delete |
| Versions | Startup: read | switches need Startup: update + docker image, Settings: reinstall and Backup: create |
| Properties | File: read content | File: update; *Save and restart* also needs Control: restart |
| Players | Players: view | Players: manage |
| Errors | File: read content | — |
| Notifications | Notifications | Notifications (targets hold webhook URLs and tokens) |
| Subdomains | Subdomains: read | Subdomains: manage (claim, release, move, status cards, own domain) |
| Velocity | owner or root admin only | owner or root admin only |

Server permissions are on each server's **Users** page, in the new **Mods** and
**Subdomains** groups (plus Players and Notifications). The admin page is for root admins.
