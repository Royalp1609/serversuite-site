# Updating

Read the release notes first: they say whether a release has database migrations or needs the
Pterodactyl extension reinstalled. Take a panel backup before updating.

```bash
cd /var/www/pterodactyl
# replace the contents of packages/serversuite with the new backend zip
sudo -u www-data composer require "pterodactyl-serversuite/serversuite:*@dev"
grep '"version"' vendor/pterodactyl-serversuite/serversuite/composer.json   # check it
sudo -u www-data php artisan migrate --force
sudo -u www-data php artisan optimize:clear
sudo -u www-data php artisan queue:restart
sudo systemctl reload php8.3-fpm    # or apache2 - whatever runs PHP

# put the new serversuite.blueprint in the panel root, then:
blueprint -install serversuite
```

Reinstalling the extension replaces the panel's frontend: anyone with the panel open needs
a hard refresh (Ctrl+Shift+R).

## Versions

Releases use [Semantic Versioning](https://semver.org/), starting at `1.0.0-rc.1`. Every release
is on the [Releases page](https://github.com/royalp1609/serversuite-pterodactyl/releases), with
what changed.
