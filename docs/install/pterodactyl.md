# Install on Pterodactyl

Server Suite for Pterodactyl is two parts that always go together:

| Part | File | What it is |
|---|---|---|
| Backend | `serversuite-pterodactyl-backend-v<version>.zip` | Composer package `pterodactyl-serversuite/serversuite`: the logic, database tables and scheduled jobs |
| Extension | `serversuite.blueprint` | Blueprint extension: the server tabs and the admin page |

**Requirements:** Pterodactyl 1.14.x or 1.15.x, [Blueprint](https://blueprint.zip)
(beta-2026-08 or newer on 1.15), Node 22, PHP 8.2+, the queue worker and the scheduler.

## Fresh install

```bash
cd /var/www/pterodactyl

# 1. Backend: unzip so composer.json lands at packages/serversuite/composer.json
sudo mkdir -p packages/serversuite
sudo unzip -q serversuite-pterodactyl-backend-v<version>.zip -d packages/serversuite
sudo chown -R www-data:www-data packages/serversuite

# Point Composer at it, then require it
sudo -u www-data composer config repositories.serversuite '{"type": "path", "url": "packages/serversuite"}'
# @rc lets Composer accept release candidates such as 1.0.0-rc.1 as well as stable releases
sudo -u www-data composer require "pterodactyl-serversuite/serversuite:*@rc"
grep '"version"' vendor/pterodactyl-serversuite/serversuite/composer.json   # check the version

sudo -u www-data php artisan migrate --force
sudo -u www-data php artisan optimize:clear
sudo -u www-data php artisan queue:restart

# 2. Extension: put serversuite.blueprint in the panel root
blueprint -install serversuite
```

Then hard-refresh the browser (Ctrl+Shift+R): the panel's JavaScript is cached hard.

!!! warning "Check the zip layout"
    The backend zip must land as `packages/serversuite/composer.json`, not in a nested folder.

## After installing

- Open **Admin → Extensions → Server Suite** to set up repositories, the CurseForge key,
  update checks, backups, eggs and subdomains (see [Admin settings](../admin/settings.md)).
- Subusers get two new permission groups, **Mods** and **Subdomains**, plus Players and
  Notifications, on each server's **Users** page (see [Permissions](../admin/permissions.md)).

## After a Pterodactyl upgrade

A panel upgrade replaces `composer.json` and removes Server Suite's Composer entry, and it
overwrites the files Blueprint patched. After upgrading the panel, before bringing it back up:

```bash
cd /var/www/pterodactyl
# 1. Upgrade Blueprint to a release that supports the new panel version (Blueprint's guide)
# 2. Re-add the backend
sudo -u www-data composer config repositories.serversuite '{"type": "path", "url": "packages/serversuite"}'
sudo -u www-data composer require "pterodactyl-serversuite/serversuite:*@rc"
sudo -u www-data php artisan migrate --force
sudo -u www-data php artisan optimize:clear
sudo -u www-data php artisan queue:restart
# 3. Reinstall the extension
blueprint -install serversuite
```

| Pterodactyl | Blueprint | Server Suite |
|---|---|---|
| 1.14.x | beta-2026-06 or newer | 1.0.0-rc.1+ |
| 1.15.x | beta-2026-08 or newer | 1.0.0-rc.1+ |
| 2.x | — | not yet (coming later) |
