## Mincraft Server Install Location

```bash
/usr/local/games/minecraft/papermc
```

## Systemd Service File

    /etc/systemd/system/minecraft.service

``` bash
[Unit]
Description=Minecraft Server
After=network.target

[Service]
WorkingDirectory=/usr/local/games/minecraft/papermc
Type=forking
User=minecraft
Group=minecraft
TimeoutStopSec=15

Restart=always

ExecStart=/usr/bin/screen -L -dmS minecraft /usr/bin/java -Xms2G -Xmx8G -jar papermc --nogui

ExecStop=/usr/bin/screen -p 0 -S minecraft -X eval 'stuff "say SERVER SHUTTING DOWN IN 10 SECONDS..."\015'
ExecStop=/bin/sleep 5
ExecStop=/usr/bin/screen -p 0 -S minecraft -X eval 'stuff "say SERVER SHUTTING DOWN IN 5 SECONDS..."\015'
ExecStop=/bin/sleep 5
ExecStop=/usr/bin/screen -p 0 -S minecraft -X eval 'stuff "save-all"\015'
ExecStop=/usr/bin/screen -p 0 -S minecraft -X eval 'stuff "stop"\015'


[Install]
WantedBy=multi-user.target
```

## Alias for access to screen command

```bash
alias mc='sudo -u minecraft /usr/bin/bash -c '\''/usr/bin/screen -r'\'''
```



## Minecraft Server

PaperMC is used for the minecraft server.

[PaperMC.io](https://papermc.io/downloads#Paper-1.19)

## Plugin List

PaperMC is a fork of Spigot, so any plugin written for Spigot should generally run in PaperMC
Plugin .jar file should be placed in the "plugins" directory. Restart the server, and then a folder for the plugin will appear in the plugins directory, you can then edit the plugin config file in its own folder.

[BentoBox](https://github.com/bentoboxworld)
	Enables things like SkyBlock for individual players
[dynmap](https://github.com/webbukkit/dynmap)
	Dynamic map generation with player location
[EssentialsX Core](https://essentialsx.net/downloads.html)
	Multiple essential commands
[EssentialsX Chat](https://essentialsx.net/downloads.html)
	Chat integration for things like user titles (MOD, Admin, etc)
[floodgate](https://github.com/GeyserMC/Floodgate)
	Allow Bedrock players to join the server 
[Geyser](https://github.com/GeyserMC/Geyser)
	Allow Bedrock players to join the server
[LuckPerms](https://luckperms.net/)
	Permissions plugin, useful for essentials and worldedit/worldguard plugins
[Multiverse-Core](https://dev.bukkit.org/projects/multiverse-core)
	Allows multiple worlds on the one server
[Multiverse-Inventories](https://dev.bukkit.org/projects/multiverse-inventories/)
	Allows configuring inventories per world on the one server
[Multiverse-Portals](https://dev.bukkit.org/projects/multiverse-portals/)
	Custom portal setup for between worlds or any other location
[SinglePlayerSleep](https://www.spigotmc.org/resources/singleplayersleep.68139/)
	Allows transition from night to day with one player sleeping, even if there are multiple online
[Vault](https://www.spigotmc.org/resources/vault.34315/)
	Used for permissions and chat integration
[WorldEdit](https://dev.bukkit.org/projects/worldedit)
	Allows editing of worlds (copy/paste, special edit commands etc), required for WorldGuard
[WorldGuard](https://dev.bukkit.org/projects/worldguard/)
	Enables the ability to protect specific regions (portals, homes etc) and assign users who own/can edit them

