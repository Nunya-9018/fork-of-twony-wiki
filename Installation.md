Installing Towny is easy. There are usually just two things that admins miss.
>* Configuring the existing worlds.
>* Townyperms.yml already has 99% of the Towny permission nodes given out correctly.

Read the steps here carefully and you'll save yourself a lot of head-scratching and trouble.

## Server Preparation
1. Stop your server completely.
2. Download either of the following:
   * Latest release build from the [Releases tab](https://github.com/TownyAdvanced/Towny/releases).
     * Includes **Towny.jar** and **TownyChat.jar**.
   * Latest pre-release/development build from the [Releases tab](https://github.com/TownyAdvanced/Towny/releases).
     * Includes **Towny.jar**.
     * TownyChat's latest files can be gotten from their Releases tabs [here](https://github.com/TownyAdvanced/TownyChat/releases).
     * The documentation on the wiki does not get updated until a Release build is out. You will need to read the [changelog](https://github.com/TownyAdvanced/Towny/blob/master/resources/ChangeLog.txt) to learn what's been added/removed/fixed since the last Release.
   * You can consult the [Readme](https://github.com/TownyAdvanced/Towny#current-recommended-versions) to see which version you should use for older Minecrafts.
3. Copy the contents to your _Plugins_ folder.
   * **Towny.jar** is required at all times
   * **TownyChat.jar** is required if you want Towny to modify chatting:
     * Adding prefixes and suffixes from your permissions plugin to chat
     * Adding town, nation-related tags to chat.
     * Adding general/local/town/nation/mod/admin to chat channels.
   * [Vault.jar](https://www.spigotmc.org/resources/vault.34315/) **or** [Reserve.jar](https://www.spigotmc.org/resources/reserve.50739/) (separate downloads) is required if you use an economy plugin.
4. Start your server.
5. Stop your server.
6. Continue reading below, do not skip the Configuring Existing Worlds section of this guide.

## Configuring Existing Worlds
Towny has a config section called Default New World Settings. When you started the server it took the default Default Settings and applied it to all your existing worlds. This includes the revert-on-unclaim and explosion-revert settings for each world. You must configure your worlds' settings. _Many admins wonder why the revert-on-unclaim feature is rolling back towns when they cannot pay their upkeep and fall to ruin, when they've turned the revert-on-unclaim off in the config; **it is because they skipped this step of the installation.**_
1. Navigate to the newly-created _plugins/Towny/data/worlds_ folder.
2. Open each **worldname.txt**.
3. Edit each file accordingly.

## Configuring config.yml
1. Navigate to _plugins/Towny/Settings_
2. Open **config.yml**
3. Carefully edit **config.yml** to your liking, including:
   * Townblock size defaulting at 16x16 (CANNOT BE CHANGED LATER!).
   * Settings for future worlds (Settings for future **worldname.txt** files).
   * Settings for new towns and nations.
4. Change the economy settings:
   * If you do not use an economy plugin, set `using_economy: false`.
   * If you are using a UUID version of _EssentialsEco_, add _NPC:_ to the beginning of _Town-_ and _Nation-_ in `new_world_settings`:
     * From this:
         ```bash
         town:
         prefix: Town-
         nation:
         prefix: Nation-
         ```
     * To this:
         ```bash
         town:
         prefix: NPC:Town-
         nation:
         prefix: NPC:Nation-
         ```
5. Save **config.yml**.
6. Start your server. You are now ready to begin your own town.

## Configuring townyperms.yml (semi-optional)
Some admins make the mistake of placing Towny permission nodes into their permission plugin. The only permission nodes you must give in your permission plugin is `towny.admin.*` to your admin group(s).

The only other permission node that isn't already given out is `towny.wild.*`. Giving this node will grant full build/destroy/switch/itemuse rights to players in the wilderness. You must decide if you want to give this out, and how.

* One option is to put it in the nomad section of the **townyperms.yml** file, which will enable all players server-wide to use the wilderness.
* The other option is to give it in your permission plugin, to whichever rank you want to use the wilderness.

1. Navigate to _plugins/Towny/Settings_.
2. Open **townyperms.yml**
3. Carefully read over the default groups/ranks.
4. Add and remove permission nodes as you see fit.
5. Optionally, add your own ranks for mayors to promote (or demote) their residents to.
6. Save **townyperms.yml**.
7. Perform `/ta reload` in-game to see your changes.

## Configuring channels.yml (optional)

_This step is optional if you have **TownyChat.jar**._

1. Navigate to _plugins/Towny/Settings_
2. Open **channels.yml**.
3. Edit **channels.yml** to your liking.
4. Save **channels.yml**.
6. Perform `/townychat reload` in-game to see your changes.

## Configuring chatconfig.yml (optional)

_This step is optional if you have **TownyChat.jar**._

1. Navigate to _plugins/Towny/Settings_
2. Open **chatconfig.yml**.
3. Edit **chatconfig.yml** to your liking.
4. Save **chatconfig.yml**.
6. Perform `/townychat reload` in-game to see your changes.