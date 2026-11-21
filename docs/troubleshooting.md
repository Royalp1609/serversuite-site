# Troubleshooting

## The panel shows a 500 error after a command

A command ran as root and left root-owned cache files. Run, from the panel root:

```bash
chown -R www-data:www-data storage bootstrap/cache
sudo -u www-data php artisan optimize:clear
```

Always run `php artisan` and `composer` as the web user (`sudo -u www-data ...`).

## Backup restore: blocked address { #backup-restore-blocked-address }

*"The provided backup link resolves to a blocked address."* Your S3 storage (self-hosted MinIO,
Garage, ...) is on a private address, and recent Wings versions refuse restores from private
addresses. On each Wings node, add the S3 hostname under `system.backups` in the Wings config
(`/etc/pterodactyl/config.yml`), then restart Wings:

```yaml
  backups:
    restore_host_allowlist:
    - s3.example.internal
```

Keep it to that exact hostname. Public S3 doesn't need it, and creating backups isn't affected.

## Scheduled backups or update checks never run

The panel's scheduler cron isn't running. Add `* * * * * php /var/www/<panel>/artisan schedule:run`
for the web user, and make sure the queue worker is running.

## Old behaviour after an update

PHP is still serving the old code from its opcode cache. Run `php artisan queue:restart` and
reload PHP-FPM or Apache. On Pterodactyl, hard-refresh the browser after reinstalling the
extension.

## Pterodactyl: "could not be found in any version"

The Composer path repository is missing, which always happens after a panel upgrade. Run the
`composer config repositories.serversuite ...` line from the [install guide](install/pterodactyl.md#after-a-pterodactyl-upgrade),
then require the package again.

## Pterodactyl: "Unknown column" or a missing table

Run `sudo -u www-data php artisan migrate --force`.

## Pterodactyl: `__PHP_Incomplete_Class` in the queue

Stale queue workers: `sudo -u www-data php artisan queue:restart`.

## CurseForge results are missing

CurseForge needs an API key in the admin settings. Modrinth and Hangar work without one.

## A subdomain can't be claimed

The name already has a record in the zone (yours or anyone's), the server is at its allowance,
or the domain is disabled. The page says which.
