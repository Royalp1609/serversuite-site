# FAQ

**Is it free?**
Yes. Server Suite is free and open source under the AGPL-3.0. Mod, modpack and version installs
are never sold: they're free on Modrinth, CurseForge and Hangar, and Server Suite keeps them free.

**Does it work with my panel?**
Pterodactyl 1.14 and 1.15 (with Blueprint). Versions for **Pelican** and **Pterodactyl v2** are
in development and coming later.

**Do files go through my panel server?**
No. Mods, modpacks and server jars are downloaded by Wings straight to the game server. The panel
only sends the instructions.

**Which loaders are supported?**
Paper, Purpur, Folia, Spigot, Fabric, Quilt, Forge, NeoForge, Velocity and Vanilla for Java;
Bedrock Dedicated Server with add-ons. Rust and Valheim get their own set of pages.

**Will it change my server without asking?**
Only for things you switch on: scheduled backups, automatic mod updates and automatic version
upgrades are all opt-in. Anything that replaces files offers a backup first.

**What happens if a switch fails?**
A backup is taken before every switch (unless the server has no backup allocation, which the
dialog warns about). If the server doesn't come back, you're told which backup to restore.

**Can subusers use it?**
Yes, with the permissions you give them. See [Permissions](admin/permissions.md).

**Can I sell subdomains or backup plans?**
Yes: raise a server's allowance by hand, or use the [Billing API](admin/billing-api.md) from
Paymenter or another billing system.

**Where do I report a bug?**
Open an issue on the project's GitHub repository.
