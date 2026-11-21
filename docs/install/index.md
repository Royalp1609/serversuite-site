# Install

| | Pterodactyl 1.x |
|---|---|
| Ships as | Composer package + [Blueprint](https://blueprint.zip) extension |
| Panel versions | 1.14.x, 1.15.x |
| PHP | 8.2 or 8.3 (8.4 works) |
| Needs | Blueprint (beta-2026-08+ on 1.15), Node 22, queue worker and scheduler |
| Guide | [Install on Pterodactyl](pterodactyl.md) |

!!! info "Coming later: Pelican and Pterodactyl v2"
    Server Suite for **Pelican** (a native Pelican plugin) and for **Pterodactyl v2** are in
    development. This first public release is for **Pterodactyl 1.x**.

It needs the panel's **queue worker** and **scheduler** running (the standard
`* * * * * php artisan schedule:run` cron line most panels already have): installs, update
checks, scheduled backups and subdomain moves run there.

Download both files from the [latest release](https://github.com/royalp1609/serversuite-pterodactyl/releases/latest):
`serversuite-pterodactyl-backend-v<version>.zip` and `serversuite.blueprint`.

!!! warning "Run panel commands as the web user"
    Every `php artisan` and `composer` command below runs as the web server user
    (`www-data` on Debian/Ubuntu). Running them as root leaves root-owned cache files behind and
    the panel answers with a 500 error afterwards. If that happens:
    `chown -R www-data:www-data storage bootstrap/cache` and `sudo -u www-data php artisan optimize:clear`.
