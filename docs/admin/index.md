# For admins

- [Settings](settings.md): repositories, update checks, backups, eggs, games, subdomain domains
  and allowances, default notifications.
- [Permissions](permissions.md): what subusers and admin roles can see and do.
- [Billing API](billing-api.md): let Paymenter or another billing system sell subdomains and
  backup plans.

Every change made through Server Suite (mods, switches, resets, backups, subdomains) shows in the
server's **Activity** log, with who did it. All secrets (Cloudflare tokens, webhook URLs, ntfy
tokens) are encrypted with the panel's `APP_KEY` and never shown again, so keep `APP_KEY` backed up.
