# Rust & Valheim

Server Suite recognises the game each server runs. Minecraft servers get every page. **Rust**
and **Valheim** get the pages that make sense for them; other games get Backups,
Notifications and Subdomains.

Version and loader switches, resets and modpacks are refused on non-Minecraft servers, so a plan
sold as one game can't be turned into a Minecraft server.

## Errors

=== "Rust"

    Reads the log of the framework the server runs: Oxide's newest `oxide/logs/oxide_<date>.txt`,
    or Carbon's `carbon/logs/Carbon.Core.log`. Compile errors, failed hooks and failed timers name
    the plugin. When several plugins hit missing methods or types (or any plugin does around
    force-wipe day), a notice says Rust has probably changed under Oxide/Carbon: wait for the
    framework update and restart, rather than removing plugins.

=== "Valheim"

    Reads `BepInEx/LogOutput.log`. Errors a plugin logs, plugins BepInEx couldn't load (missing
    dependencies) and exceptions in a plugin's code name the plugin. The Unity noise every
    headless Valheim server prints is left out.

## Configs

The [config editor](configs.md) on the game's folders, saved straight away (and still refused if
the server rewrote the file since you opened it).

=== "Rust"

    `oxide/config`, `oxide/data`, `carbon/configs`, `carbon/data` and `server/rust/cfg`. Source
    style convar files such as `server.cfg` (`server.hostname "My server"`) open as a form too.

=== "Valheim"

    `BepInEx/config`.

## Players

Players are listed by SteamID64 (17 digits).

=== "Rust"

    **Owners** (admins), **Moderators** and **Banned**, with an optional name and reason. While
    the server runs, changes go in through the console (`ownerid`, `moderatorid`, `banid`, ...)
    followed by `server.writecfg`, so they apply at once. While it's stopped, `users.cfg` and
    `bans.cfg` are edited.

=== "Valheim"

    **Admins**, **Banned** and **Permitted** (`adminlist.txt`, `bannedlist.txt`,
    `permittedlist.txt`). Valheim reads them on start, so changes apply at the next start. While
    anyone is on the permitted list, only those players can join.

## Subdomains

Rust and Valheim don't use SRV records, so their subdomain is an address record and players join
with `name:port` (shown on the page).

!!! info "Coming later"
    Plugin managers for Oxide/Carbon (uMod) and Valheim (Thunderstore), Rust map wipes and
    framework switching are planned.
