Use this page to learn how Towny works, how various settings affect the gameplay, what you can do to customize Towny to your liking.

-   [The Hierarchy](#the-hierarchy)
    -   [Nomads](#nomads)
    -   [Residents](#residents)
    -   [Towns](#towns)
    -   [Mayors](#mayors)
    -   [Outlaws](#outlaws)
    -   [Nations](#nations)
    -   [Kings](#kings)
    -   [Configuring Townyperms.yml and the Roles of the Ranks Within](#configuring-townypermsyml-and-the-roles-of-the-ranks-within)
    -   [Configuring Mayor and King Titles, Town and Nation Names](#configuring-mayor-and-king-titles-town-and-nation-names)
    -   [Configuring town_level and nation_level](#configuring-town_level-and-nation_level)
-   [How Towns Grow](#how-towns-grow)
    -   [Starting a Town](#starting-a-town)
    -   [Joining Towns](#joining-yowns)
-   [Plot System of Land Ownership](#plot-system-of-land-ownership)
    -   [Town Blocks](#town-blocks)
    -   [Plot Groups](#plot-groups)
    -   [Plot Types](#plot-types)
    -   [Outposts](#outposts)
    -   [Buying and Selling Land](#buying-and-selling-land)
    -   [Using the Maps](#using-the-maps)
    -   [Plot Regeneration & Unclaimed Plots](#plot-regeneration--unclaimed-plots)
-   [How Towny Lets Players Protect Their Blocks](#how-towny-lets-players-protect-their-blocks)
    -   [Towny Plot Perms](#towny-plot-perms)
    -   [Protection Additions Found in Towny Advanced](#protection-additions-found-in-towny-advanced)
-   [How Towny Controls PVP Combat](#how-towny-controls-pvp-combat)
-   [Money](#money)
    -   [Taxes and Upkeep](#taxes-and-upkeep)
    -   [Town and Nation Banks](#town-and-nation-banks)
    -   [Town Bankruptcy](#town-bankruptcy)
-   [Town Ruins](#town-ruins)
-   [Chat](#chat)
    -   [PlaceholderAPI Support](#placeholderapi-support)
    -   [Townychat.jar](#townychatjar)
    -   [Chatconfig.yml](#chatconfigyml)
    -   [Chat Channels](#chat_channels)
    -   [Kings' minions' prefixes and suffixes](##kings-minions-prefixes-and-suffixes)
    -   [Spying on chat channels](#spying-on-chat-channels)
-   [Multiworld](#multiworld)
    -   [World Toggles](#world-toggles)
-   [Towny War](#towny-war)
-   [Using SQL instead of Flatfile](#using-sql-instead-of-flatfile)
    -   [Configuring SQL](#configuring-sql)
    -   [Converting Flatfile to SQL](#converting-flatfile-to-sql)
    -   [Converting SQL to Flatfile](#converting-sql-to-flatfile)

------------------------------------------------------------------------

[]()The Hierarchy
=================

[]()Nomads
----------

Nomads are simply players who are not part of any town. They are landless and their permission nodes are configurable via [TownyPerms](https://github.com/TownyAdvanced/Towny/wiki/Default-Townyperms.yml).yml. Nomads can purchase [Embassy plots](#embassy-plots) if they have been given `towny.command.plot.claim` in the Townyperms.yml

[]()Residents
-------------

Every person who joins your server can become a resident of a town, (by default they are given the towny.town.resident permission node in townyperms.yml's nomad section.) Residents have their own [command](https://github.com/TownyAdvanced/Towny/wiki/Towny-Commands) `/resident` which used by itself outputs a Resident Status Screen, displaying Money, Town, Plots owned and Friends. Residents can join towns or choose to start a town of their own. 

Residents can also be put into one town automatically when they join the server for the first time by setting `default_town_name: ''` in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml). 

Residents who join towns can claim plots that the Mayor of the town has set for sale. When a resident owns 1 or more plots, they will see a new line on their Resident Screen, showing plots owned and a default perm line showing the [plot perms](https://github.com/TownyAdvanced/Towny/wiki/How-Towny-Works#towny-plot-perms) given on all plots that resident owns, (which haven't had a custom plot line set.)

Residents have their permission nodes configurable via [TownyPerms](https://github.com/TownyAdvanced/Towny/wiki/Default-Townyperms.yml).yml.

[]()Towns
---------
<p><a href="https://www.youtube.com/watch?v=A8DD8050SUI"><img alt="Click here for Major Graft's Towns & Nations Video" src="https://img.youtube.com/vi/A8DD8050SUI/0.jpg" align=right height="200"></a>
A town is a collection of residents (or just one resident) with one resident as the mayor. A town also has a bank which the mayor can withdraw from. A mayor can also have assistants who have the same powers as him/herself. Towns can have taxes that will be taken at the end of each day interval. 

Towns usually grow outwards from their home block, the townblock the mayor stood in during town creation. Townblocks need to be claimed beside other townblocks, unless the mayor claims an outpost in the wilderness using `/t claim outpost`. Towns can be limited to a number of residents using the config option `global_town_settings.max_residents_per_town`, by default this is not limited. All of the towns on a server can be seen in a list using `/town list`.

As of Towny 0.95.1.0 it is possible to store MetaData on a town, see [here](https://github.com/TownyAdvanced/Towny/wiki/Configuring-Metadata-in-Towns-and-Townblocks) for details.

[]()Mayors
----------

Mayors run towns and with the help of their assistants, manage a town and its residents. Mayors have their permission nodes configurable via [TownyPerms](https://github.com/TownyAdvanced/Towny/wiki/Default-Townyperms.yml).yml. 

Mayors can decide which ranks their residents fall into, in their town. This can be a Town Assistant or any other custom ranks created by the server admin in the townyperms.yml file. Mayors can see the available ranks using `/town ranklist` command. Players are ranked using `/town rank {add|remove} {playername} {rankname}`. A player can have more than one rank assigned, allowing admins to create diverse town-roles such as bankers, builders, inviters for the mayor to choose for their trusted residents. 

Mayors also determine what sort of [tax](#taxes) and tax rates the town will charge the residents.

It is not possible to run two towns unless you are also an admin. An admin can do the following to manage two or more towns:


>Example: Admin Bob / How to create NPC Towns.

>Admin Bob wants to have a server-town, and his own town. Bob would start by creating his Server Town and setting up taxes, plotprices, permissions. This sort of town should not give residents, allies or outsiders permissions in the Server Town.
>
>Bob can give himself more townblocks using the `/ta givebonus {townname} {#}` command.
>
>When Bob is finished making his town the way he wants he uses `/townyadmin set mayor {townname} npc` to place a fake 'npc' resident as mayor of the Server Town. This is usually enough to protect the Spawn areas of most servers.
>
>Then Bob leaves Server Town and creates his own town. Using the `/townyadmin set mayor {townname} npc` command Bob can flip back and forth between towns.
>
>Bob doesn't have to leave his town to add players to the Server Town though! He can use `/townyadmin town {townname} add {playername}` to add players to the Server Town or set default_town_name: 'Server_Town' in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml).
>
>Bob can also add the NPC town into a nation using /ta nation {nation} add {town}.


As of Towny 0.95.1.0 mayors have the ability to set titles (prefixes) and surnames (postfixes) to the residents of their town. This is done with:

-   `/town set title {name} titlegoeshere`
-   `/town set surname {name} surnamegoeshere`

[]()Outlaws
-----------

As of Towny 0.92.0.0, towns (typically mayors by default, but possibly other town ranks,) can set a list of Outlaws. Outlaws are set using `/town outlaw [add/remove] [name]` and the command requires the `towny.command.town.outlaw` permission node. Outlaws can be any player and do not have to be in a town or nation. 

If the newly-minted outlaw is a member of your town they will be kicked. Towns that have themselves set to Open-status (anyone can join using the `/town join` command,) can use the outlaw list to prevent these players from joining their town freely. Players cannot spawn to public towns which consider them outlaws.

Players that enter into a town where they are considered to be an outlaw will see a warning-title-message informing them. If a player is online and they are made into an Outlaw they will see a message in chat. 

Outlaws can be jailed if they die in the town where they are considered to be an outlaw. This requires the `jail.is_jailing_attacking_outlaws` option in the Towny [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) to be set to true. It also requires the person who's done the killing to have the `towny.outlaw.jailer` permission node. It also requires the town to own at least one jail plot. By default only Mayors, Assistants and Sheriff ranks have the `towny.outlaw.jailer` permission node. 

A town member can view their town's outlaw list using `/town outlawlist`. Anyone can view any town's outlawlist using `/town outlawlist {townname}`

As of Towny 0.96.4.0 you can optionally have outlaws teleport away from the towns they're not allowed in. When `allow_outlaws_to_enter_town` is set to false in the Towny [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) outlaws will be teleported away. The `outlaw_teleport_warmup` setting will determine how quickly this will happen, when set to 0 it will be instant or it can be any number of seconds.

[]()Nations
-----------
<p><a href="https://www.youtube.com/watch?v=A8DD8050SUI"><img alt="Click here for Major Graft's Towns & Nations Video" src="https://img.youtube.com/vi/A8DD8050SUI/0.jpg" align=right height="200"></a>
A nation is a collection of towns (or just one town) with one town as the capital. The mayor of that capital is the king. A nation can join the war event, as well as ally other nations. A nation also has it's own bank. It can also tax the towns that belong to it. 

Nations can also have a spawn reached using `/nation spawn` which if the nation is considered 'Public' can be reached by nearly any non-enemy players. The nation spawn can be restricted to the capital in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at `global_nation_settings.capital_spawn` otherwise the spawn point can be anywhere in the nation. 

Two nations can decide to join in an alliance, which allows them to be protected from friendly fire, help on each others plots (if the plot's perm line allows allies,) and to help each other in war. As of 0.91.0.0, you may restrict nation alliances to be 2-way only. So that Nation A cannot consider Nation B an ally unless the Nation B also considers Nation A an ally. You may turn this setting on in the config: `war.disallow_one_way_alliance`, which defaults to false. 

Also, as of 0.91.0.0, you may restrict who can create, join and maintain a nation by requiring a minimum number of residents. See the Global Town Settings section of the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml). 

As of 0.92.0.0, you may set a maximum distance between the nation capital and towns which are allowed to join the nation. See the Global Town Settings section of the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml). 

As of 0.93.0.0, nations can grant a NationZone which surrounds the towns which are members. This is enabled at `global_nation_settings.nationzone.enable` in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml). NationZones are just like normal wilderness except the only players which can modify the area are members of the nation. This can be useful to prevent greifing near to towns who have a nation. NationZones can be increased in size by increasing the population of the nation using the NationLevels in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml), you can optionally make the capital town have a larger NationZone. NationZones can be disabled during war time in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at `global_nation_settings.nationzone.war_disables`. 

As of 0.96.2.0 you can configure a maximum number of residents per-town if they do not have a nation, at `global_town_settings.maximum_number_residents_without_nation`. When set above 0 towns will have to form nations to add more residents.

Nations can grant many perks to their towns which can increase as the nation population increases, these include:

-   Bonus townblocks to be claimed.
-   Cheaper town upkeep costs.
-   Larger surrounding NationZones.
-   An increased outpost limit.

[]()Kings
---------

Kings lead Nations and are the mayor of the capital city. Kings have their permission nodes configurable via [TownyPerms](https://github.com/TownyAdvanced/Towny/wiki/Default-Townyperms.yml).yml. Kings can decide which ranks their residents fall into, in their nation. This can be a Nation Assistant or any other custom ranks created by the server admin in the townyperms.yml file. Kings can see the available ranks using `/nation ranklist` command. Players are ranked using `/nation rank {add|remove} {playername} {rankname}`. A player can have more than one rank assigned, allowing admins to create diverse nation-roles such as bankers, inviters for the king to choose for their trusted residents. 

Kings have the ability to set titles (prefixes) and surnames (postfixes) to the residents of the towns they have in their nation. This is done with:

-   `/nation set title {name} titlegoeshere`
-   `/nation set surname {name} surnamegoeshere`

Typing the commands with nothing after the player's name resets the title or surname to blank.

[]()Configuring Townyperms.yml and the Roles of the Ranks Within
----------------------------------------------------------------

As of Towny 0.82.0.0 Towny has a permission configuration file, [TownyPerms](https://github.com/TownyAdvanced/Towny/wiki/Default-Townyperms.yml).yml, located in the towny\settings\ folder. This system pushes permissions directly to Bukkit and works along side all other perms plugins. It allows you to define sets of permissions based upon a players status (nomad/resident/mayor/king). You can also assign additional permissions based upon any assigned town/nation ranks (assistant/vip etc). This system is not limited to Towny permission nodes. You can assign any permissions for any plugins in its groups. This file allows admins to decide what each player-rank can do. Some ranks are assigned automatically:

-   Players without towns are Nomads.
-   Players in towns are Residents.
-   Owners of towns are Mayors.
-   Owners of nations are Kings.

Some ranks are assigned by Mayors or Kings, and supplement the ranks the players already have:

-   Mayors can make a resident a Town Assistant.
-   Kings can make a resident a Nation Assistant.
-   Mayors and kings can grant admin-created ranks, allowing for diverse customization.
    -   A player can attain many Supplemental ranks from their mayor or king, allowing for diverse nation/town-roles.
    -   Examples of this would be town-builders, town-bankers, nation-bankers, town-inviters, etc.

A resident of a town can see the ranks within their town using `/town ranklist`. A mayor can use `/town rank {add|remove} {playername} {rankname}` to give a player a new rank within their town. A king can use `/nation rank {add|remove} {playername} {rankname}` to give a player a new rank within their nation.

[]()Configuring Mayor and King Titles, Town and Nation Names
------------------------------------------------------------

Towny gives you the ability to customize the naming scheme applied to Mayors, Kings, Towns, Capital Cities and Nations. This is done with two sections in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) 

[]()Configuring town_level and nation_level
------------------------------------------------------------

#### town_level:

-   The basic layout of the townLevel lines are as follows:

```
  - numResidents: 1
    namePrefix: ''
    namePostfix: ' (Settlement)'
    mayorPrefix: 'Hermit '
    mayorPostfix: ''
    townBlockBuyBonusLimit: 0
    townBlockLimit: 16
    upkeepModifier: 1.0
    townOutpostLimit: 0
    debtCapModifier: 1.0

  - numResidents: 2
    namePrefix: ''
    namePostfix: ' (Hamlet)'
    mayorPrefix: 'Chief '
    mayorPostfix: ''
    townBlockBuyBonusLimit: 0
    townBlockLimit: 32
    upkeepModifier: 1.0
    townOutpostLimit: 1
    debtCapModifier: 1.0
```

These are read as follows:
| variable | description | 
| ---- | ---- | 
|`numresidents: 1` | This is how many residents a town needs to reach the town_level.|
|`namePrefix: ''`| This is added to the front of the town name. | 
|`namePostfix: ' (Settlement)'` | This is added to the end of the town name.| 
|`mayorPrefix: 'Hermit '` | This is added to the front of the mayor's name. |
|`mayorPostfix: ''`| This is added to the end of the mayor's name. |
|`townBlockBuyBonusLimit: 0` | This is the maximum number of plots which the town can buy using /town buy bonus. <br> Requires `town.max_purchased_blocks_uses_town_levels` set to true in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml). |
|`townBlockLimit: 16`| This overrides the `town_block_ratio` config setting and decides how many townblocks a town gets.<br> Requires `town_block_ratio: '0'` set in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml). |
|`upkeepModifier: 1.0`| Use a higher multiplier to increase the upkeep as towns get more residents.<br> Does not affect servers with `town_plotbased_upkeep:true` in which case it is based off of plot-count rather than resident-count, *unless* you've also got `town_plotbased_upkeep_affected_by_town_level_modifier:true` )|
|`townOutpostLimit: 1`| This is how many outposts a Town can claim.<br> Requires `limit_outposts_using_town_and_nation_levels` set to true in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml). | 
|`debtCapModifier: 1.0`| When `debt_cap_uses_town_levels` is set to true in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml), the `debt_cap` `override` price will be multiplied by the debtCapModifier in the town_level. (Ex: debtCapModifier of 3.0 and debt_cap.override of 1000.0 would set a debtcap of 3.0 x 1000 = 3000.)|

-   The two levels above are for towns of 1 and 2 residents. When a town is created the mayor's new town has (Settlement) added to the end of his townname and he is given the prefix of Hermit. When the mayor gets a second resident his town becomes Townname (Hamlet) and he receives the prefix of Chief.

#### nation_level:

-   The basic layout of the nationLevel lines are as follows:

```
        -   numResidents: 10
            capitalPrefix: ''
            capitalPostfix: ''
            namePrefix: 'Federation of '
            namePostfix: ' (Nation)'
            kingPrefix: 'Count '
            kingPostfix: ''
            townBlockLimitBonus: 10
            upkeepModifier: 1.0
            nationTownUpkeepModifier: 1.0
            nationZonesSize: 1
            nationBonusOutpostLimit: 2

        -   numResidents: 20
            capitalPrefix: ''
            capitalPostfix: ''
            namePrefix: 'Dominion of '
            namePostfix: ' (Nation)'
            kingPrefix: 'Duke '
            kingPostfix: ''
            townBlockLimitBonus: 20
            upkeepModifier: 1.0
            nationTownUpkeepModifier: 1.0
            nationZonesSize: 2
            nationBonusOutpostLimit: 3
```

These are read as follows:
| variable | description | 
| ---- | ---- | 
|`numResidents: 10`| This is how many residents a nation must have to reach the nation level.|
|`capitalPrefix: ''`| This is added to the front of the capital city of the nation.|
|`capitolPostfix: ''`| This is added to the end of the capital city of the nation.|
|`namePrefix: 'Federation of '`| This is added to the front of the nation name.|
|`namePostfix: ' (Nation)'`| This is added to the end of the nation name.|
|`kingPrefix: 'Count '`| This is added to the front of the nation-leader.|
|`kingPostfix: ''`| This is added to the end of the nation-leader's name.|
|`townBlockLimitBonus: 10`| This is the number of bonus townblocks given to a town when they join a nation.|
|`upkeepModifier: 1.0`| Use a higher multiplier to increase the upkeep as nations get more residents (unless you use `town_plotbased_upkeep:true` in which case it is based off of plot-count rather than resident-count.)|
|`nationTownUpkeepModifier: 1.0`| Joining a nation will lower/raise how much town upkeep your town pays. This multiplier is calculated after all other multipliers have their effect on the town upkeep cost. When set at 1.0, there is no change to upkeep.|
|`nationZonesSize: 2`| How many plots wide the NationZone is surrounding a town.|
|`nationBonusOutpostLimit: 2`| How many outposts more that the town can claim on top of it's usual limit.|

------------------------------------------------------------------------

[]()How Towns Grow
==================

[]()Starting a Town
-------------------

Mayors start towns using the command `/town new {townname}`. This will often require an amount of money set in the config at `price_new_town`.

The townblock they are standing in will be the home block for the town, the exact spot/position will be the spawn point for the town. A mayor can move the spawn point within the homeblock using `/t set spawn`. The homeblock can be moved to another claimed townblock using `/t set homeblock`.

More townblocks can be claimed using `/town claim`. These townblocks need to be directly adjacent to already claimed townblocks, unless it is an [outpost](#outposts).

[]()Joining Towns
-----------------

There are two ways to join towns, the first is by being invited by a Mayor or a Town assistant. The second is by joining an open town. 

Mayors and assistants can add players to their town with the command `/town add {playername}`. The player will receive a prompt to either `/accept` or `/deny` the invitation. 

Mayors can set their towns to open using `/town toggle open`. A player who isn't in a town already can use the command `/town join {townname}` to join open towns. Open towns can be viewed using the `/town list by open`.

When residents join towns they increase the number of townblocks accessible to the mayor for claiming.

------------------------------------------------------------------------

[]()Plot System of Land Ownership
=================================

[]()Town Blocks
---------------

Towny provides a server admin a hands-off approach to block-protection. Block protection is broken down into plots of land, called townblocks, which by default are 16x16x256 (the full height of the world.) Think of them as cells on a uniform grid, all aligned and with no space in between each other, every one the same size. Townblocks are claimed by town mayors who can then sell/give individual plots to their town's residents.

As of Towny 0.95.1.0 it is possible to store MetaData on a townblock, see [here](https://github.com/TownyAdvanced/Towny/wiki/Configuring-Metadata-in-Towns-and-Townblocks) for details.

### []()Town Block Size

You change the townblock size in [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at `town_block_size: 16`. **Changing this value is suggested only when you first install Towny.** Doing so after entering data will shift things unwantedly. Using smaller value will allow higher precision, at the cost of more work setting up. Also, extremely small values will render the caching system used by Towny useless (it is not recommended to go below 4.) Each cell is (`town_block_size` x `town_block_size` x 256) in size, with 256 being from bedrock to clouds.

### []()Claiming Townblocks

Towns' residents can claim townblocks for the town as long as they have the right permission nodes. By default this is restricted to Mayors and people with the Assistant rank. The player uses `/town claim` or `/town claim #` or `/town claim rect|circle #|auto` or `/town claim auto` to claim townblocks for their town. 

|command | result|
|:----:|:----|
|`/town claim`| Claims one plot, where the player is standing.|
|`/town claim #` | Claims a square with a radius equal to the given #, sometimes down-sizing the radius to make a perfect square, surrounding the command user.|
|`/town claim rect #` | Claims a square with a radius equal to the given #, sometimes down-sizing the radius to make a perfect square, surrounding the command user.|
|`/town claim rect auto` | Claims all possible townblocks in a square shape, centered around the command user.|
|`/town claim circle #` | Claims a circle with a radius equal to the given #, sometimes down-sizing the radius to make a perfect circle, surrounding the command user. | 
|`/town claim circle auto` | Claims all possible townblocks in a circle shape, centered around the command user. | 
|`/town claim auto` | Claims all possible townblocks in a square shape centered around the command user.|

Using the `/town` command will list how many townblocks are available to be claimed. 

As of 0.95.0.0 you may set a refund amount for unclaiming townblocks at `economy.new_expand.price_claim_townblock_refund`, it is not recommended that this be set at or higher than the cost to claim a townblock.

As of 0.95.0.0 you may make the cost of claiming townblocks increase at `economy.new_expand.price_claim_townblock_increase`. When set to 1 this is deactivated. 1.3 means +30% to every bonus claim block cost. Cost increase can be seen in `/towny prices` output.

As of 0.96.3.0 you can set the maximum price that the `economy.new_expand.price_claim_townblock_increase` can reach. This is set at `economy.new_expand.max_price_claim_townblock` in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml).

### []()Setting How Many Town Blocks A Town Receives

You can change how many town blocks a town gets to claim. This is done in two places. Towny checks first in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at ` town_block_ratio: 8 ` and by default gives a town 8 townblocks per resident. You can override this by setting ` town_block_ratio: 0 ` and using the town_level section of the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) More information on the town_level line and how to configure it is [here.](#configuring-town_level-and-nation_level)

### []()Buying Townblocks

Mayors can buy townblocks using `/town buy bonus {amount}`. There are two methods you can limit how many townblocks can be purchased by a town:

1. If `town.max_purchased_blocks_uses_town_levels` is set to false: the max is set in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at `max_purchased_blocks: '0'`.
2. If `town.max_purchased_blocks_uses_town_levels` is set to true: the max is dictated via the town_level's `townBlockBuyBonusLimit` setting, allowing towns with more residents to purchase more townblocks.

The price of a bought townblock is also set in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at `price_purchased_bonus_townblock: '25.0'`. The price can be configured to increase with each purchase using the `price_purchased_bonus_townblock_increase: '1.0'` config setting. Using this feature, mayors can grow their town without needing new residents. Increasing costs can be seen in `/town buy bonus` output.

As of Towny 0.96.3.0 you can set a maximum price that the `price_purchased_bonus_townblock_increase` will be able to go to. This is set at `economy.new_expand.price_purchased_bonus_townblock_max_price` in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml).

[]()Plot Groups
---------------
Plots can be grouped together into _plot groups_. This allows plots to be sold/bought and manipulated as if it were one Plot. To create a group a player must have the proper permissions to operate on it. The player then stands in the plot and executes: `/plot group add {group_name}`, Towny will add the plot you're standing in, into a group if it exists, or create a new one if a group with that name doesn't exist. Simply repeat the command `/plot group add {same_group_as_above}` while standing in other plots to add those plots to the group. 

Most of the other commands used to manipulate plots are the same with one exception, instead of starting with the prefix `/plot`, plot group operations start with the `/plot group` prefix. For example to set a property for sale you do `/plot fs 10000`, but for a plot group named highlands you would do `/plot group fs 10000`. Perms, types and others follow this convention. See `/plot group ?` for full command list.

[]()Plot Types
--------------
<p><a href="https://www.youtube.com/watch?v=7nB8kUDkV-A"><img alt="Click here for Major Graft's Video about Plot Types" src="https://img.youtube.com/vi/7nB8kUDkV-A/0.jpg" align=right height="200"></a>
Players can use `/town plots {townname}` to view the counts of various plot types in a town. Towny post-0.75 has added plot types besides the default. This is to give mayors more control over their towns. 

As of Towny 0.95.1.0 you can configure costs to set plot types at `plot_type_costs` in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml).

The plot types are as follows:

### []()Default Plots

These plots do not need any specific command to be designated. They are put up for sale with `/plot forsale {$$}`. A plot which is not of default type can be reset to a default plot with `/plot set reset`.

### []()Shop Plots

Shop plots are designated with `/plot set shop`. A mayor can use `/town set shopprice {$$}` to set how much shop plots are sold at by default. This can be overridden when a mayor puts the actual plot up for sale with `/plot forsale {$$}`. A mayor can also charge an additional shoptax with `/town set shoptax {$$}`. This tax is charged in addition to the normal plottax.

### []()Arena Plots

Arena plots are designated with `/plot set arena.` PVP is on all the time in arena plots as well as friendly-fire damage. Town health regen is also disabled in arena plots.

### []()Embassy Plots

Embassy plots are designated with `/plot set embassy`. A mayor can use `/town set embassyprice {$$}` to set how much embassy plots are sold at by default. This can be overriden when a mayor puts the actual plot up for sale with `/plot forsale {$$}`. A mayor can also charge an additional embassytax with `/town set embassytax {$$}`. This tax is charged in addition to the normal plottax. An embassy plot can be bought by any player, whether they are in a town or not, as long as they have the `towny.command.plot.claim` permission node. The townblock remains owned by the host-town and a mayor from the host-town can take the plot from the owner at any time. Embassy plots can also be changed into shop plots, allowing for larger shop towns, where many different towns' players can set up shops. When a player leaves a town they do not lose ownership of their plots if those plots are set to be Embassy plots.

### []()Wilds Plots

Wilds plots are designated with `/plot set wilds`. A wilds plot allows residents to destroy the blocks found on the wild ignore ID list. This includes ores, trees, flowers, mushrooms and other harvestable blocks by default. 
It does not include stone, dirt, grass and other terrain blocks. It is useful for creating tree farms, and protecting the terrain around a town, while still allowing residents to cut trees and explore caves. 

A player can use `/towny wildsblocks` to see a server's allowed wilds plots blocks.

Setting up wilds plots can be slightly complex, here are instructions.

<blockquote>

1.  Navigate to your towny\data\worlds\WORLDNAME.txt file
2.  Set:
    -   unclaimedZoneBuild=false
    -   unclaimedZoneDestroy=false

3.  Configure the unclaimedZoneIgnoreIds line to include the blocks you would like players to break/build.
4.  Go to the Wilds plots you can set using `/plot set wilds`

By default residents will have build/destroy enabled for them, you can also set allies or outsiders perms if you want non-town-members to use the Wilds plots.
</blockquote>

### []()Inn Plots

Inn plots are designated with `/plot set inn`. Inns are most useful when the `deny_bed_use` setting is true in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml). This setting makes it so that players cannot use beds in plots they do not personally own, *except* when that plot is an Inn plot.

Inn plot allows anyone to use a bed to set their `/res spawn` and spawn on death locations. However, Inn plots cannot be used by enemies of your nation.

### []()Jail Plots

Jail plots are designated with `/plot set jail`.

Players can become jailed if:
-   The player's mayor/sheriffs send them to jail using the `/t toggle jail [jailnumber] [residentname] {days}` command.
-   An attacker who attacks a town which considers him an Enemy (Nation-relationship) dies in that Town. He is sent to the first available Jail plot of the defending town.
-   An attacker who attacks a town which considers him an Outlaw dies in that Town by a player with the `towny.outlaw.jailer` permission node. He is sent to the first available Jail plot of the defending town. In the config `jail.is_jailing_attacking_outlaws` must be true.

Jailed players become unjailed if:
-   they leave their town and become a nomad,
-   the mayor/sheriff unjails them,
-   the player pays a bail amount to the town which jailed them, (using: `/resident jail paybail`)
-   they manage to escape the jail plot and the town and get into Wilderness.

In addition:
-   Jailed players cannot teleport.
-   Jailed players cannot use Ender Pearls unless enabled in the config.
-   Jailed players who die are sent back to their prescribed jail plot.
-   Jailed players do not give monetary payouts when they are killed.
-   Jailed players show their jailed status in the `/res [playername]` screen, along with the town they are jailed in.
-   It is suggested you make a new town rank in the townyperms.yml called Sheriff, and give that rank the `towny.command.town.toggle.jail` node. Newly generated townyperms.yml files will contain this rank by default.
-   There is a list in the config at `jail.blacklisted_commands` where you can set a list of commands which jailed players cannot use.

### []()Farm Plots
<p><a href="https://www.youtube.com/watch?v=gJihLaYeWR4"><img alt="Click here for Major Graft's Video about Plot Types" src="https://img.youtube.com/vi/gJihLaYeWR4/0.jpg" align=right height="200"></a></p>

Farm plots are designated with `/plot set farm`. A Farm plot players to only build/destroy blocks designated in the Towny [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at `global_town_settings.farm_plot_allow_blocks`. By default this list includes: ```BAMBOO,BAMBOO_SAPLING,JUNGLE_LOG,JUNGLE_SAPLING,JUNGLE_LEAVES,OAK_LOG,OAK_SAPLING,OAK_LEAVES,BIRCH_LOG,BIRCH_SAPLING,BIRCH_LEAVES,ACACIA_LOG,ACACIA_SAPLING,ACACIA_LEAVES,DARK_OAK_LOG,DARK_OAK_SAPLING,DARK_OAK_LEAVES,SPRUCE_LOG,SPRUCE_SAPLING,SPRUCE_LEAVES,BEETROOTS,COCOA,CHORUS_PLANT,CHORUS_FLOWER,SWEET_BERRY_BUSH,KELP,SEAGRASS,TALL_SEAGRASS,GRASS,TALL_GRASS,FERN,LARGE_FERN,CARROTS,WHEAT,POTATOES,PUMPKIN,PUMPKIN_STEM,ATTACHED_PUMPKIN_STEM,NETHER_WART,COCOA,VINE,MELON,MELON_STEM,ATTACHED_MELON_STEM,SUGAR_CANE,CACTUS,ALLIUM,AZURE_BLUET,BLUE_ORCHID,CORNFLOWER,DANDELION,LILAC,LILY_OF_THE_VALLEY,ORANGE_TULIP,OXEYE_DAISY,PEONY,PINK_TULIP,POPPY,RED_TULIP,ROSE_BUSH,SUNFLOWER,WHITE_TULIP,WITHER_ROSE,CRIMSON_FUNGUS,CRIMSON_STEM,CRIMSON_HYPHAE,CRIMSON_ROOTS,MUSHROOM_STEM,NETHER_WART_BLOCK,BROWN_MUSHROOM,BROWN_MUSHROOM_BLOCK,RED_MUSHROOM,RED_MUSHROOM_BLOCK,SHROOMLIGHT,WARPED_FUNGUS,WARPED_HYPHAE,WARPED_ROOTS,WARPED_STEM,WARPED_WART_BLOCK,WEEPING_VINES_PLANT,WEEPING_VINES,NETHER_SPROUTS``` 

Players can use `/towny farmblocks` to see a list of a server's farmblocks.

Who can build/destroy these blocks is still determined by the plot's perm line seen in the `/plot perm` screen. This means that if B=rnao, anyone can plant/place the allowed blocks in the plot. If the B=r--- then only town residents can plant/place the allowed blocks. 

If admins want, they can add FARMLAND to the allowed blocks list, which will allow anyone allowed via the perm line to also make farmland with a hoe. By default FARMLAND is not included and only admins/mayors/assistants will be able to create farmland with a hoe. Towny already protects farmland from being stomped into grass, so farmland will only return to dirt if it is not irrigated. 

Farm plots also allow player to kill animals in the plot. In order to kill the configured animals list the player must be able to break wheat blocks on the plot. The list of animals is set in the config at `global_town_settings.farm_animals`. By default this list includes `PIG,COW,CHICKEN,SHEEP,MOOSHROOM`.


### []()Bank Plots

Bank plots are designated with `/plot set bank`. Bank plots can be used to limit town and nation bank depositing/withdrawing. By default this setting is off but can be turned on at `bank.is_banking_limited_to_bank_plots ` in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) Bank plots are more useful for other plugins which would want to limit their banking features to within Towny bank plots.

[]()Outposts
------------

Normally townblocks are claimed around the home block, always connected to the town's other townblocks. To claim a townblock out in the wilderness or in another world, a mayor or assistant must claim an outpost. In order for players to claim outposts, the config must be set to `allow_outposts: true` and players require `towny.town.claim.outpost` in their permission node group. The outpost list can be viewed by using `/town outpost list` command. The spawn point inside of an outpost townblock can be moved using the `/t set outpost` command.

The residents of the Town can teleport to outposts to using `/town outpost x|name|name:x`

>-   with x being a number 1 - however many outposts the town has
>-   where name is the plot name of the outpost (seen in `/t outpost list` and set using `/plot set name {name}`.) 
>-   where name:1asdasda - useful for when a plot name begins with a number.


An admin can configure how many outposts a player can claim, this is set in your permissions plugin's info/option/meta node section using the towny_maxoutposts: {number} info node. [See here.](https://github.com/TownyAdvanced/Towny/wiki/Towny-Permission-Nodes) 

Alternatively, as of 0.93.0.0, you can use the config.yml's town_level and nation_level maxoutpost values to give larger towns more outposts to claim, and bonus outposts to towns in nations. This requires enabling the feature in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at `global_town_settings.limit_outposts_using_town_and_nation_levels`.

An admin can also set a number of residents required by a town before they can claim outposts, using the `minimum_amount_of_residents_in_town_for_outpost` setting. By default there is no resident requirement. 

Outposts cannot be claimed too close to other home blocks, just like when a mayor starts a town they cannot be too close. The exact number is set in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at `min_distance_from_town_homeblock: 5`. In the default setting an outpost cannot be claimed within 5 townblocks of any other homeblock. 

You can also configure how close an outpost can get to any other town's plots using `town.min_distance_for_outpost_from_plot`. 

You can also set the cost of claiming an outpost in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at `price_outpost: 500.0`. 

[]()Buying and Selling Land
----------------
<p><a href="https://www.youtube.com/watch?v=kiOb2dxu0Zw"><img alt="Click here for Major Graft's Plot Claiming Video" src="https://img.youtube.com/vi/kiOb2dxu0Zw/0.jpg" align=right height="200"></a>
Land is sold by Mayors to Residents that are a part of their town. `using_economy: true` must be set in [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) in order for costs to be applied. Mayors have a command used in game to set the cost of all the plots that are set for sale hence-forth.

<blockquote>

-   `/town set plotprice {$} `
    -   This sets the cost of newly-set-for-sale plots, already set-for-sale plots keep their costs. 
    -   If it is not set, the plots will cost $0 by default.
</blockquote>
To put a plot up for sale a mayor, while standing in the plot, type `/plot forsale {optional cost}`. The resident would then type `/plot claim` (while standing in the plot,) to buy it.

[]()Using the Maps
------------------

The map in towny displays the grid system of plots. The map can be viewed once using `/towny map` one time or you can set the map to show every time you move from one block to another:

>-   Use `/resident toggle map` to turn it on or off.

A larger version of the map can be seen using `/towny map big`.

[]()Plot Regeneration & Unclaimed Plots
---------------------------------------

There are 4 options for affecting townblocks/plots.

### []()Reverting unclaimed townblocks to their original state on unclaim

When a town plot is unclaimed (by a player using `/t unclaim` or through upkeep) it will slowly begin to revert to a pre-town state. Blocks will slowly change back to a snapshot taken of the plot when it was first claimed. A townblock must revert completely before the snapshot of the townblock is removed. If townblock is reclaimed mid-revert, a new snapshot is not taken and if the townblock is unclaimed again it will revert to the original snapshot.

>-   Disabling this feature is done in the towny\data\worlds\worldname.txt @ `usingPlotManagementRevert=false`,
>-   or by using `/tw toggle revertunclaim` while standing in the world you want to toggle it in.
>-   Disabling this feature for new worlds is done in the config at `new_world_settings.plot_management.revert_on_unclaim.enabled`.

You can configure certain block types you don't want restored to prevent players exploiting regen for diamond ores.

>-   Block types to not restore are configured in `plotManagementIgnoreIds` in the world's txt file towny\data\worlds\worldname.txt.
>-   Defaults for new worlds are set in the config at `new_world_settings.plot_management.revert_on_unclaim.block_ignore`

### []()Deleting pre-defined blocks on unclaim

When a town plot is unclaimed (by a player using `/t unclaim` or through upkeep) block materials matching a list will be deleted within that townblock. This can be useful for deleting all signs within a townblock, ensuring any chests locked with Lockette or Deadbolt signs are unlocked.

>-   Disabling this feature is done in the towny\data\worlds\worldname.txt @ `usingPlotManagementdelete=false`
>-   Disabling this feature for new worlds is done in the config at `new_world_settings.plot_management.block_delete.enabled`

You can configure the list of Material names to be removed on a per-world basis.

>-   The materials listed in the towny\data\worlds\worldname.txt @ `plotManagementDeleteIds=` will be removed from the townblock.
>-   Defaults for new worlds are set in the config at `new_world_settings.plot_management.block_delete.unclaim_delete`

### []()Plot-Owners' and Mayors' `/plot clear` command

A feature available only to Town Mayors on public town land: `/plot clear`. This command is meant to be used after a plot was personally owned by a resident, who either moved to another plot or left town. By default this list includes only signs, useful for mayors to remove sign-protection on doors, chests, furnaces, dispensers and trapdoors given via Lockette or Deadbolt.

A player can use `/towny plotclearblocks` to see which blocks will be removed when /plot clear is used.

>-   Disabling this feature is done in the in the towny\data\worlds\worldname.txt @ `usingPlotManagementMayorDelete=false` or via the `/tw toggle plotcleardelete` command, in the applicable world.
>-   Disabling this feature for new worlds is done in the config at `new_world_settings.plot_management.mayor_plotblock_delete.enabled`

You configure the list of Material names to be removed when this command is used.

>-   The list of blockIDs is listed in the towny\data\worlds\worldname.txt @ `plotManagementMayorDelete=`
>-   Defaults for new worlds are set in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at `new_world_settings.plot_management.mayor_plotblock_delete.mayor_plot_delete`

As of Towny 0.79.1.0, players can use this command within plots they personally own.

### []()Wilderness Regeneration

The wilderness explosion regeneration has two settings:

#### Entity Explosions
This feature regenerates explosions made by entities, such as TNT, Creepers, WitherSkulls, EnderDragons and others (it is a configurable list.) These settings are copied to the individual world files, so you must make changes per world.

>-   Disabling this feature for entity explosions is done in the in the towny\data\worlds\worldname.txt @ `usingPlotManagementWildRegen=true`
>-   or by using '/tw toggle revertentityexpl' while standing in the world you want to toggle it in.
>-   Disabling this feature for new worlds is done in the config at `new_world_settings.plot_management.wild_revert_on_mob_explosion.enabled`
>-   The list of entities whose explosions will revert is set in the towny\data\worlds\worldname.txt @ `PlotManagementWildRegenEntities`
>-   The default list applied to new worlds is set in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) @ `new_world_settings.plot_management.wild_revert_on_mob_explosion.entities`

#### Block Explosions
As of Towny 0.96.3.0 you can now specify a list of blocks whose explosions will be reverted (think: beds in the nether,) again per-world with the default for new worlds set in the config.

>-   Disabling this feature for block explosions is done in the in the towny\data\worlds\worldname.txt @ `usingPlotManagementWildRegenBlocks=true`
>-   or by using '/tw toggle revertblockexpl' while standing in the world you want to toggle it in.
>-   Disabling this feature for new worlds is done in the config at `new_world_settings.plot_management.wild_revert_on_mob_explosion.enabled`
>-   The list of blocks whose explosions will revert is set in the towny\data\worlds\worldname.txt @ `PlotManagementWildRegenBlocks` 
>-   The default list applied to new worlds is set in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) @ `new_world_settings.plot_management.wild_revert_on_block_explosion.blocks`


#### Explosion revert delay
You can configure how quickly the blocks will regenerate, specifically how much time in between each block being reverted.

>-   The timer is changed in the towny\data\worlds\worldname.txt @ `usingPlotManagementWildRegenDelay=5`
>-   The default for new worlds is set in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at `new_world_settings.plot_management.wild_revert_on_mob_explosion.delay`

------------------------------------------------------------------------

[]()How Towny Lets Players Protect Their Blocks
===============================================

Towny's genius is the way it lets players protect themselves. An admin doesn't need to go around protecting land for players, and players can't run rampant claiming massive amounts of land without working for it and building their towns. 

>Available in Towny 0.77.0.0 and onward are per-plot permissions. When a plot is claimed by a mayor for their town using `/town claim` the plot will receive the perm line seen in the `/town` status screen. When a plot is claimed by a resident from a town using `/plot claim` the plot will receive the perm line see in the `/res` status screen. The owner of the plots can set different perms to different plots. To view a plots perm type `/plot perm` and to set a plots' perms use `/plot set perm`.

The first concept you need to digest are the 4 perm-types and 4 groups.

[]()Towny Plot Perms
--------------------

There are 4 permission-type values, which can be set for personal plots and for town plots as well (town permissions can be set by the mayor and affect plots who are not owned by any player.) The basic command for this is either `/resident set perm` or `/town set perm` followed by the proper flags for each permission. 

Players can see the server's switch blocks by using the `towny switches` command.

Players can see the server's item_use items by using the `towny itemuse` command.

### []()Perm-Types

The 4 permission-types available are Build, Destroy, Switch and Itemuse.

-   Build allows players to add blocks in your town/plot.

-   Destroy allows players to remove blocks in your town/plot, or in some cases alter the states of existing blocks (think changing redstone repeater settings.)

-   Switch covers the use of:
    -   CHEST,
    -   SHULKER_BOXES, 
    -   TRAPPED_CHEST,
    -   FURNACE,
    -   BLAST_FURNACE,
    -   DISPENSER,
    -   HOPPER,
    -   DROPPER,
    -   JUKEBOX, 
    -   STONECUTTER,
    -   SMITHING_TABLE,
    -   FLETCHING_TABLE,
    -   SMOKER,
    -   LOOM,
    -   GRINDSTONE,
    -   COMPOSTER,
    -   CARTOGRAPHY_TABLE,
    -   BELL,
    -   BARREL,
    -   BREWING_STAND,
    -   LEVER,
    -   PRESSURE_PLATES,
    -   BUTTONS,
    -   WOOD_DOORS,
    -   FENCE_GATES,
    -   TRAPDOORS,
    -   MINECARTS,
    -   LODESTONE,
    -   RESPAWN_ANCHOR,
    -   TARGET
    -   .... or any other type of block which is clicked on.

-   Itemuse covers the use of:
    -   MINECARTS,
    -   BOATS,
    -   ENDER_PEARL,
    -   FIREBALL,
    -   CHORUS_FRUIT,
    -   LEAD
    -   .... or any other type of item which is used in some manner.

- ItemUse and Switch lists have the follow pre-configured catch-all groups you can add to them: BOATS,MINECARTS,WOOD_DOORS,PRESSURE_PLATES,FENCE_GATES,TRAPDOORS,SHULKER_BOXES,BUTTONS.
- Note: Vehicles like MINECARTS and BOATS can be added to the switch_ids. If you want to treat other rideable mobs like switches add SADDLE to protect HORSES, DONKEYS, MULES, PIGS, STRIDERS (This is not recommended, unless you want players to not be able to re-mount their animals in towns they cannot switch in.)

### []()Perm-Groups

Each permission-type has 4 perm-groups to which the pemissions can be set for. 

The four perm-groups are:

- Friend/Resident
- Town/Nation
- Ally
- Outsider

These are displayed on your `/resident` perm line as **FTAO** and stand for **F**riend, **T**own, **A**lly, **O**utsider. For residents the Friend group consists of a player's friend list and Town consists of townmembers. 

For towns, the perm line reads **RNAO**, with R representing **R**esidents (players in that town) and **N**ation representing residents of towns in your nation. 

Mayors need to use `/t set perm resident blah on/off` instead of `/t set perm friend blah on/off`.

The other groups are:

-   **A**lly
    -   On personally-owned plots allies consist of players in your nation and players in your nation's allies.
    -   On town-owed plots it is players in your nation's allies.
-   **O**utsiders
    -   Players who are not part of your town or nation or nation's allies.

[All commands are found on the Wiki's Commands page.](https://github.com/TownyAdvanced/Towny/wiki/Towny-Commands)

### []()Setting perms in-game with commands
<p><a href="https://www.youtube.com/watch?v=wvshFTv3l6A"><img alt="Click here for Major Graft's Plot Permission Video" src="https://img.youtube.com/vi/wvshFTv3l6A/0.jpg" align=right height="200"></a>
Setting perms for your town's public land or your personal plots is easy! There are two distinct levels of protection provided by towns. First are the town blocks, protected because they are part of a town and not owned by anyone. When you enter one of these plots from the wilderness or an owned plot the notification will show "~ Unowned". Mayors are able to set the permission for unowned plots using the the `/town set perm` command. A full list of commands is on the [commands](https://github.com/TownyAdvanced/Towny/wiki/Towny-Commands) page, here are some examples:

-   `/town set perm {on/off}` - This turns on or off all permissions for all perm-types and all perm-groups.
-   `/town set perm ally {on/off}` - This turns on or off all perm-types and for the town's allies (Nations to which their nation is allied with.)
-   `/town set perm resident build {on/off}` - This turns on or off all permissions for building done by residents of the town.

Second are the town blocks owned personally by a resident of a town. A resident is able to set the permission for unowned plots using the the `/resident set perm` command. A full list of commands is on the [commands](https://github.com/TownyAdvanced/Towny/wiki/Towny-Commands) page, here are some examples:

-   `/resident set perm {on/off}` - This turns on or off all permissions for all perm-types and all perm-groups.
-   `/resident set perm friend {on/off}` - This turns on or off all permissions for the resident's friend list.
-   `/resident set perm ally {on/off}` - This turns on or off all permissions for all perm-types to the resident's ally list. This consists of the nation's fellow towns and their nation's allied nations.
-   `/resident set perm outsider switch {on/off}` - This turns on or off permissions for switch use by outsiders.

Lastly, don't forget those are just the defaults for plots, any owned plot can be set with it's own individual perms:

-   `/plot set perm {on/of}` - This turns on or off all permissions for all perm-types and all perm-groups on the plot which is being stood in.
-   `/plot set perm friend {on/off}` - This turns on or off all permissions for the resident's friend list on the plot which is being stood in.
-   `/plot set perm ally {on/off}` - This turns on or off all permissions for all perm-types to the resident's ally list. This consists of the nation's fellow towns and their nation's allied nations. This affects the plot which is being stood in.
-   `/plot set perm outsider switch {on/off}` - This turns on or off permissions for switch use by outsiders on the plot which is being stood in.

Mayors can changed the protection of their town with the following commands:

-   `/town toggle explosion`
-   `/town toggle fire`
-   `/town toggle pvp`
-   `/town toggle mobs`

Mayors and Residents can change each of their plots individually using these commands:

-   `/plot toggle explosion`
-   `/plot toggle fire`
-   `/plot toggle pvp`
-   `/plot toggle mobs`

Explosion and fire toggles are overridden by a mayor's town toggles. The preceding commands by themselves will change the perm line seen from `/town` or `/res`. They will also change any plots that were using the previously-set default perm line (town-owned or player-owned plots.) They will not change plots which were not set to the default perm line see in `/town` or `/res`. In order to change all plots a mayor or resident must use the following command, which will propagate the current perm line seen in `/town` or `/res` to ALL plots owned by the town or resident.

-   `/res set perm reset` - Propagates the perm line in `/res` to ALL plots owned by that resident.
-   `/town set perm reset` - Propagates the perm line in `/town` to ALL town-owned plots owned by that town.
-   These commands also affect the `/town toggle` and `/plot toggle` settings.

[]()Protection Additions Found in Towny Advanced
------------------------------------------------

New in Towny Advanced (0.72+) are three new protection types, anti-explosion and anti-firespread and piston-protection. On the town level, a mayor can set these flags using:

-   `/town toggle explosion`
-   `/town toggle fire`

Explosion protection stops all explosions. This stops TNT, TNT cannons and creeper explosions. Firespread protection stops all fires from spreading, including lava, lightning and lighters. Piston-protection allows pistons to operate between similarly owned townblocks or wild areas.

As of 0.95.0.0 Animal Luring (drawing animals' attention using their preferred food,) is controlled in the following fashion: In town-owned plots and in the wilderness, luring is not stopped. In personally-owned resident plots, the player must be able to break dirt in the plot to lure an animal.

As of 0.95.1.0 Villagers are protected from evil-doers.

As of 0.96.2.0 Lighting Nether Portals will now require a player to place Portal Blocks. This means that servers who want players to be able to make nether portals to a world where they do not grant towny.wild permissions will be able to build a portal. The node required to build a portal that would connect into the wilderness would be `towny.wild.build.NETHER_PORTAL`. This means servers that do not grant wild permissions do not have to give `towny.wild.build.OBSIDIAN`, which would mean players could place obsidian anywhere in the wild.

------------------------------------------------------------------------

[]()How Towny Controls PVP Combat
=================================

Towny affects PVP combat, deciding who can be damaged where and by whom.

Plots, Towns and Worlds all have PVP settings, here is how they work.

### []()World PVP Settings

World settings for PVP are controlled using in-game commands

<blockquote>

-   `/townyworld toggle pvp`
    -   This command disables and enables PVP world-wide. If you type `/tw` you will see will see a red {PVP} next to the name of the world at the top of the output. If PVP is off in the world, no pvp combat can occur, even in Arena plots.
-   `/townyworld toggle forcepvp`
    -   This command forces pvp on world-wide, disregarding any plot or town pvp settings. Friendly-fire is still obeyed.
    -   As of Towny 0.93.0.0 there is a new [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) option at `global_town_settings.homeblocks_prevent_forcepvp` which can be enabled to stop forcepvp from affecting town homeblocks.
    -   There is a way to override forcing pvp on in towns. Using `/ta town {townname} toggle forcepvp` you can override the forcepvp setting. This is useful for forcing pvp on worldwide but leaving it off in a spawn-town.
-   `/townyworld toggle friendlyfire`
    -   This command toggles friendly fire on and off per-world. By default Towny disables friendly-fire between townmembers, nationmembers and residents whose nation considers the attacker's nations an ally.
</blockquote>

### []()Town PVP Settings

Towns pvp settings are controlled using this in-game command

>- `/town toggle pvp` - This toggles pvp on and off town-wide.
    
Additionally, admins have `/ta town {townname} toggle forcepvp` which will set a town's secret AdminEnabledPVP setting to true or false.

### []()Plot PVP Settings

Plots can have their pvp status controlled individually with this in-game command

>- `/plot toggle pvp` - This toggles a single plot's pvp status.

------------------------------------------------------------------------

[]()Money
=========

If you do not want Towny to have anything to do with money you can set `using_economy: false` in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) and no taxes/upkeep will occur, and no claiming or town/nation creation will cost money.

[]()Taxes and Upkeep
--------------------

Taxes and Upkeep are two separate functions with to different results. `using_economy: true` must be set in [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) in order for Taxes and Upkeep to be applied. Taxes and Upkeep are charged at the same time, each 'Towny Day' or each time an admin uses the `/townyadmin newday` command. The time of a 'Towny Day' can be set in [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at `day_interval: 1d` and by default is 24 real-life hours. Any one can check how long until the next day starts by using `/towny time`.

The [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) has an entry to turn taxation and upkeep on or off at `daily_taxes: true`.

### []()Taxes

Taxes are collected on the town level from residents and on the nation level from towns. Any player can check the taxes which apply to them with the in-game command `/res tax`. Town mayors can use two commands to set their tax-rates.

<blockquote>

-   `/town set taxes {$}`
    -   This can be either a flat rate (ex: 10) or a percentage.
        -   Toggling taxes from flatrate to percentage is done using `/town toggle taxpercent`.
        -   Flatrate:
            -   This charges each resident of a town the same amount. Setting it to 10 would charge each resident each 'Towny Day'.
            -   If a resident can't pay his town tax when using flatrate taxation then he is kicked from the town.
            -   This has a maximum amount which can be set in the config at `economy.daily_taxes.max_town_tax_amount`.
        -   Percentage:
            -   This charges a player a percentage of their money. If a player has no money left, he pays no taxes and is not kicked from the town.
            -   A maximum amount taken by the taxpercent can be configured per-town using `/town set  taxpercentcap {$}`.
            -   This has a maximum amount which can be set in the config at `economy.daily_taxes.max_town_tax_percent`.
-   `/town set plottax {$}`
    -   This charges each resident of a town for each plot they own. Setting it to 10 would charge Miner Steve 40 dollars if he owned 4 plots.
    -   If a resident can't pay his plot tax he loses his plot.
    -   This has a maximum amount which can be set in the config at `economy.daily_taxes.max_plot_tax_amount`.
</blockquote>

Nation leaders can use one command to set a tax on their towns.

<blockquote>

-   `/nation set taxes {$}`
    -   This charges each town that is a member of the nation. Setting it to 100 would charge each town's townbank 100 each 'Towny Day'.
    -   If a town can't pay it's tax then it is kicked from the nation.
    -   This has a maximum amount which can be set in the config at `economy.daily_taxes.max_nation_tax_amount`.
</blockquote>

Admins can set options in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) for controlling maximum/minimum tax amounts on towns. The above `max_town|nation|plot_tax_amount` options default to 1000 and `max_town_tax_percent` which defaults to 25%. Which one is used depends on how the town is taxing, a flat rate or by percentage. `town.default_taxes.minimumtax` sets the minimum tax required when mayors use the '/t set taxes' command. There are also settings for default taxes in new towns, which can set default plottax, embassy taxes, shop taxes.

#### []()How to pay landowners

A new option added to post-0.78.0.0 versions of Towny allows you to pay players money each day, based on the number of plots they own. To use this do the following:

-   Set a negative town upkeep and enable `use_plot_payments: true` in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml)
-   At a new day the negative upkeep will be used to calculate the towns upkeep, but instead of taking it from the town, it will be divided between the plot owners.
-   These funds are paid by the server, not the town.

### []()Upkeep

Upkeep collection can be set on towns and on nations separately. Upkeep money is taken from townbanks and nationbanks and removed from the game. You can set the upkeep amounts to negative numbers to pay towns and nations instead of charging them. Upkeep is used by a server admin to remove inactive towns and nations from the server, it will also help reduce inflation in a server economy. Setting the upkeep to a negative number gives the town or nation-banks that amount each new day. Upkeep is set in [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) with two flags:

-   `price_nation_upkeep: 100.0`
    -   The server's daily charge on each nation. If a nation fails to pay this upkeep, all of it's member towns are kicked and the Nation is removed.
-   `price_town_upkeep: 10.0`
    -   The server's daily charge on each town. If a town fails to pay this upkeep, all of it's residents are kicked and the town is removed.

Upkeep can be modified in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) to affect different-sized towns differently. There are two ways to calculate the upkeep using the upkeep modifier found in the town_level and nation_level lines. By default the town_level and nation_level lines use the resident-count to determine upkeep via the upkeep modifier. The other option is to base it off plot-count rather than resident count. If you would like to set it based on plot-count set `town_plotbased_upkeep:true` in your [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml). More information on the townLevel line and how to configure it is [here.](#configuring-town_level-and-nation_level)

As of 0.95.0.0 you may now charge nations upkeep per-town at `economy.daily_taxes.nation_pertown_upkeep`. Uses total number of towns in the nation to determine upkeep instead of nation level (Number of Residents), calculated by (`number of towns in nation` X `price_nation_upkeep`). If `economy.daily_taxes.nation_pertown_upkeep_affected_by_nation_level_modifier` is true, the nation levels upkeep modifier will have an affect.

As of 0.95.0.0 you may now penalize towns which have claimed more townblocks than they are allowed. By setting `price_town_overclaimed_upkeep_penalty_plotbased` to true and putting an amount at `economy.daily_taxes.price_town_overclaimed_upkeep_penalty` towns will be charged this amount per townblock they are overclaimed by, in addition to their normal upkeep.

[]()Town and Nation Banks
-------------------------

Towns and Nations both have banks, to which any resident can deposit money but only town mayors and nation kings (and assistants) can withdraw from. Any money collected via taxes is deposited to the nation/town bank. When a town needs money, to claim a townblock or an outpost, it is taken from the townbank. Since mayors and kings can deposit money to their respective banks, some servers will find that mayors and kings shield their wealth from plugins that take a players money for dying from pvp combat. To prevent townbanks from being exploited an admin can use two options:

-   Admins can set a cap on a town/nation banks at `town_bank_cap` and `nation_bank_cap` in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml).
-   Admins can use '/ta toggle withdraw' to prevent mayors and kings from removing money from their bank.

As of Towny 0.82.0.0 and on-wards the cap on banks is a hard cap and does not allow any money to be added to the town/nation banks if it would put the bank over the limit. This does not remove money from town/nation banks which are already over the limit.

As of Towny 0.96.6.0 there are bank history commands which open book GUIs showing transactions made to and from the town and nation banks:
```
  - /town bankhistory {pages}
  - /nation bankhistory {pages}
  - /ta town {townname} bankhistory {pages}
  - /ta nation {nationname} bankhistory {pages}
```


[]()Town Bankruptcy
-------------------

As of Towny 0.96.3.0, Towny has an optional bankruptcy feature which can be enabled in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) by setting `economy.bankruptcy.enabled: true`. When enabled a town can have their bank go into a negative balance via paying upkeep and/or paying their nation's tax. 

Towns that are bankrupt can use `/t deposit {amount}` to deposit money into the bank to pay back and remove the bankrupt status.

While bankrupt:
 - Towns cannot invite members.
 - Towns cannot set their town to open status.
 - Towns cannot claim more land.
 - Towns cannot have anything built in their land.

### Debt Caps
How far a town can go into debt is up to the admin's discretion, but by default Towny will use the following formula to determine how much a town's debt-cap will be:


`(Town Cost) + ((TownBlocks - 1)* Townblock Claim Cost) + (Outposts * (Outpost Cost - Townblock Claim Cost))`

This roughly amounts to what the Town has had to spend to get to their current claims. The debt cap can be seen in the `/town` status screen.

This can be overriden in multiple ways:
1. `economy.bankruptcy.debt_cap.maximum` : When set to greater than 0.0, this will be used to determine every town''s maximum debt, overriding the above calculation if the calculation would be larger than the set maximum.

2. `economy.bankruptcy.debt_cap.override` : When set to greater than 0.0, this setting will override all other debt calculations and maximums, making all towns have the same debt cap.

3. `economy.bankruptcy.debt_cap.debt_cap_uses_town_levels: true` : When true the debt_cap.override price will be multiplied by the debtCapModifier in the [town_level section](#configuring-town_level-and-nation_level) of the config. (Ex: debtCapModifier of 3.0 and debt_cap.override of 1000.0 would set a debtcap of 3.0 x 1000 = 3000.)

### Other bankruptcy rules
When `economy.bankruptcy.upkeep.delete_towns_that_reach_debt_cap` is set to true a Town that hits their debt cap will be deleted. If it is false they will not be deleted, but not go further into debt.

When `economy.bankruptcy.nation_tax.do_bankrupt_towns_pay_nation_tax` is set to true a Town will pay their nation tax out of their debt up to the point they hit their debt cap. If false towns that are bankrupt will not pay any nation tax and will leave their nation. True is recommended when using a Siege War style war/conquering system, otherwise conquered towns will be able to leave the nation simply by not paying the nation tax. False is recommended otherwise so that nations are not using abandoned towns to gather taxes.

When `economy.bankruptcy.nation_tax.kick_towns_that_reach_debt_cap` is true a Town that has hit their debt cap will be kicked from the nation for not being able to pay their tax.

------------------------------------------------------------------------

[]()Town Ruins
=========

Added in Towny 0.96.6.0, the Town Ruins feature enables deleted Towns to enter into a pseudo-deleted state. It is enabled in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) in the Town Ruining section. Simply put: when a town would be deleted, be it from not paying the upkeep, or someone using the delete command, the town becomes Ruined. After the configured amount of time set at `town_ruining.town_ruins.max_duration_hours` the town will become fully deleted.

While ruined a town is subject to the following:
  - The townblocks cannot be claimed by other towns (they are still claimed by the town,)
  - The town will be placed under the control of an NPC mayor,
  - The town can be griefed,
  - The town's residents will not be able to execute most /town commands and no /plot commands,
    - /town, /town reclaim|list|leave are allowed.

Town ruining is a useful method of preventing conquered towns from escaping their Nation by deleting their town and immediately and reclaiming their land under a new town. Town ruining was originally developed by Goosius for [SiegeWar](https://github.com/TownyAdvanced/SiegeWar).

### Town Reclaiming
Town reclaiming is enabled in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at `town_ruining.town_ruins.reclaim_enabled`. When enabled any town member will be able to use the `/town reclaim` command in order to become the town's new mayor. This command will cost money, which is configured at `economy.new_expand.price_reclaim_ruined_town` and can be seen in the `/towny prices` screen.

Town reclamation can be limited to only be allowed after an amount of time has passed, configured at `town_ruining.town_ruins.min_duration_hours` which by default is set to 4 hours.
  


------------------------------------------------------------------------

[]()Chat
========

[]()PlaceHolderAPI Support
--------------------------

PlaceholderAPI placeholders that Towny provides are link on [this wiki page](https://github.com/TownyAdvanced/Towny/wiki/Placeholders).


[]()Townychat.jar
-----------------

If you want Towny’s variables in chat, or the town/nation channels, you must download and install TownyChat.jar.

### []()Using TownyChat with Other Chat Plugins

To use Towny and another Chat plugin follow these instructions:

-   Go into the Towny [ChatConfig](https://github.com/TownyAdvanced/Towny/wiki/Default-ChatConfig.yml).yml and locate: `modify_chat.enable:` and be sure to set it to true like this: `modify_chat.enable: 'true'`
-   Now add Towny’s chat variables to your chat plugins config. The variables can be found in the comments of the [ChatConfig](https://github.com/TownyAdvanced/Towny/wiki/Default-ChatConfig.yml).yml
-   Make sure that no players have the towny.chat.general node or they'll be talking in the towny channel and not your other chat plugins default chat channel. You might need to negate the permission node for your admins if they have the `'*'` in their permission nodes.

Examples:

-   iChat:
    -   ingame-format: '[+prefix+group+suffix&f]{townytag} {townycolor}{townyprefix}+displayname{townypostfix}'
-   mChat:
    -   mchat-message-format: '{townytag} +p{townycolor}{townyprefix}+dn{townypostfix}+s&f: +m'
-   RoyalChat:
    -   [Guide on configuring towny prefixes in RoyalChat](http://dev.bukkit.org/server-mods/royalchat/pages/configuration/)

### []()Using TownyChat Without Another Chat Plugin

To use Towny as your sole chat plugin follow these instructions:

-   Go into the Towny [ChatConfig](https://github.com/TownyAdvanced/Towny/wiki/Default-ChatConfig.yml).yml and locate: `modify_chat.enable:` and be sure to set it to true like this: `modify_chat.enable: 'true'`
-   Configure the chat lines using the information found in the section below.

[]()Chatconfig.yml
------------------

The first config file for Towny's chat is the [ChatConfig](https://github.com/TownyAdvanced/Towny/wiki/Default-ChatConfig.yml).yml found in the \plugins\towny\settings\ folder.

### []()Towny chat formats

These are the pieces which can be used to make the Channel_format lines.

```
  {worldname} - Displays the world the player is currently in.
  
  {town} - Displays town name if a member of a town.
  {townformatted} - Displays town name (if a member of a town) using tag_format.town.
  {towntag} - Displays the formated town tag (if a member of a town) using modify_chat.tag_format.town.
  {towntagoverride} - Displays the formated town tag (if a member of a town and present) or falls back to the full name (using modify_chat.tag_format.town).
   
  {nation} - Displays nation name if a member of a nation.
  {nationformatted} - Displays nation name (if a member of a nation) using tag_format.town.
  {nationtag} - Displays the formated nation tag (if a member of a nation) using modify_chat.tag_format.nation.
  {nationtagoverride} - Displays the formated nation tag (if a member of a nation and present) or falls back to the full name (using modify_chat.tag_format.nation).
   
  {townytag} - Displays the formated town/nation tag as specified in modify_chat.tag_format.both.
  {townyformatted} - Displays the formated full town/nation names as specified in modify_chat.tag_format.both.
  {townytagoverride} - Displays the formated town/nation tag (if present) or falls back to the full names (using modify_chat.tag_format.both).
   
  {title} - Towny resident Title
  {surname} - Towny resident surname
  {townynameprefix} - Towny name prefix taken from the townLevel/nationLevels
  {townynamepostfix} - Towny name postfix taken from the townLevel/nationLevels.
  {townyprefix} - Towny resident title, or townynameprefix if no title exists
  {townypostfix} - Towny resident surname, or townynamepostfix if no surname exists
   
  {townycolor} - Towny name colour for king/mayor/resident
  {group} - Players group name pulled from your permissions plugin
  {permprefix} - Permission group prefix
  {permsuffix} - Permission group suffix.
  {permuserprefix} - Permission group prefix
  {permusersuffix} - Permission group suffix.
   
  {playername} - Default player name.
  {modplayername} - Modified player name (use if Towny is over writing some other plugins changes).
  {msg} - The message sent.

  {channelTag} - Defined in the channels entry in Channels.yml
  {msgcolour} - Defined in the channels entry in Channels.yml
```

Message spam control is set at spam_time: 0.5 The channel_formats section determines what each chat channel will look like. The tag_formats section determines what the tags will appear as. The colour section determines colours applied with {townycolor} for mayors, kings and residents. The modify_chat section is where you can disable all chat additions from Towny. You can also set per_world to true if you'd like to use the worlds: section to change chat lines' channels on a per-world basis.

[]()Chat Channels
-----------------

Chat Channels are set in Channels.yml found at \plugins\towny\settings\Channels.yml There are six chat channels by default in Towny, although an admin can create as many chat channels as they'd like in Channels.yml. Channels.yml allows you to set commands for joining and using each channel:

-   /g
    -   Put in from of text to speak in general/global chat, or without text afterwards to enter the channel.
-   /l or /lc
    -   Put in from of text to speak in local chat, or without text afterwards to enter the channel.
-   /tc
    -   Put in from of text to speak with members of your town only, or without text afterwards to enter the channel.
-   /nc
    -   Put in from of text to speak with members of your nation only, or without text afterwards to enter the channel.
-   /ac
    -   Put in from of text to speak with all members of your nation as well as any member of a nation you are allied with, or without text afterwards to enter the channel.
-   /a or /admin
    -   Put in from of text to speak in adminchat, or without text afterwards to enter the channel.
-   /m or /mod
    -   Put in from of text to speak in modchat, or without text afterwards to enter the channel.
-   /res set mode reset
    -   Reset chat mode to default chat.

The tags for each channel can be set, these are used in the [ChatConfig](https://github.com/TownyAdvanced/Towny/wiki/Default-ChatConfig.yml).yml for {channelTag}. Permission nodes for each channel can be set. Ranges for each channel can be set:

-   -1 = no limits
-   0 = same world only
-   any positive value = limited range in the same world.

### []()Putting players into channels on join

Using the info|option|meta nodes provided by GroupManger, PEX and bPermissions it is possible to put users into chat channels upon joining the server. In the same section as prefix: and suffix: add a node towny_default_modes: '' Possible channels are general, town, nation, admin, mod and local. Example in group manager:

```
                groups:
                  Default:
                    default: true
                    permissions:
                    - general.spawn
                    inheritance: []
                    info:
                      prefix: ''
                      build: true
                      suffix: ''
                      towny_maxplots: 1
                      towny_default_modes: 'local'
                  Admins:
                    default: false
                    permissions:
                    - '*'
                    inheritance:
                    info:
                      prefix: ''
                      build: true
                      suffix: ''
                      towny_maxplots: -1  
                      towny_default_modes: 'admin'
```

[]()Kings' minions' prefixes and suffixes
-----------------------------------------

Kings of nations can use two commands to change the displayed chat names of their minions:

-   `/nation set title {resident} {text of prefix} `
    -   Adds a prefix to the player.
-   `/nation set surname {resident} {text of suffix} `
    -   Adds a suffix to the player.
-   A title/surname given to a mayor will override the MayorPrefix/MayorPostfix set in the townLevels of the config. He will still retain the colouring set on mayor names (default is light blue.)

[]()Spying on chat channels
---------------------------

Admins can spy on all chat channels by using the command `/towny spy` or `/res set mode spy`. Any player can be given the ability to spy by being given the permission node towny.chat.spy

------------------------------------------------------------------------

[]()Multiworld
==============

Towny has mutliworld support. Each world has a datafile located at \plugins\towny\data\worlds\worldname.txt and each world is listed in \towny\data\worlds.txt.

[]()World Toggles
-----------------

Towny can be turned off in a world in-game. While standing in a world type `/townyworld toggle usingtowny`. Other toggles:

-   usingtowny - Turns towny off in a world.
-   claimable - Whether townblocks can be claimed by mayors in this world.
-   pvp - Whether PVP is on in the world.
-   forcepvp - Used to force pvp on in towns.
-   friendlyfire - Used to turn friendlyfire on or off.
-   explosion - Used to toggle explosions off/on in the wilderness.
-   forceexplsion - Used to force explosions on in towns.
-   fire - Used to toggle fire off/on in the wilderness.
-   forcefire - Used to force firespread on in towns.
-   townmobs - Used to turn off mobremoval in all towns. Restricted mobs are listed in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at `town_mob_removal_entities`.
-   worldmobs - Toggles mobremoval over the entire world. Restricted mobs are listed in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at `world_mob_removal_entities`.
-   wildernessmobs - Toggles mobremoval in the wilderness. Restricted mobs are listed in the [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) at `wilderness_mob_removal_entities`.

-   revertunclaim - toggles the revert-on-unclaim setting for that world.
-   revertentityexpl - toggles the revert-on-explosion (caused by entity explosions) in the wilderness setting for that world.
-   revertblockexpl - toggles the revert-on-explosion (caused by block explosions) in the wilderness setting for that world.
-   plotcleardelete - toggles the ability of players to use `/plot clear` in plots they own.
-   warallowed - toggles whether event war is allowed in the world.

------------------------------------------------------------------------

[]()Towny War
=============

There are a number of war systems which are both built-in and available as add-ons to Towny, check them out at the [War Hub.](https://townyadvanced.github.io/wars.html)

------------------------------------------------------------------------

[]()Using SQL instead of Flatfile
=================================

As of Towny 0.80.0.0 admins can choose to use an SQL database instead of flatfile.

[]()Configuring MySQL
-------------------

-   Open the \towny\settings\[config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) and find the Plugin Interfacing section.
-   Navigate to the sql: section.
-   Configure towny with your mysql database hostname/port/username and password.
-   Set the desired mysql flags in the flags section.
-   Save the config and read below for conversion instructions.



[]()Converting Flatfile to SQL
------------------------------

1.  Stop your server
2.  Open the \towny\settings\[config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) and find the Plugin Interfacing section.
3.  Find the `database_load`, make sure it's set to flatfile.
4.  Find the `database_save`, set it to either mysql, sqlite or h2.
5.  Save the config and start your server.
6.  While your server is running:
    -   Set the database_load to mysql, sqlite or h2.
    -   Type `/ta reload all` ingame.

7.  Open the Towny\Data\ folder and remove all but the plot-block-data folder. This folder contains the plot-snapshots used in the revert-on-unclaim feature. If you do not use that feature you may delete the entire Towny\data\ folder.
8.  It is important to note that Towny does not back up the sql database. It is up to you to do this.

[]()Converting SQL to Flatfile
------------------------------

1.  Stop your server
2.  Open the \towny\settings\[config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml) and find the Plugin Interfacing section.
3.  Find the `database_load`, make sure it's set to your database type (mysql, sqlite or h2.
4.  Find the `database_save`, set it to flatfile
5.  Save the config and start your server.
6.  While your server is running:
    -   Set the database_load to flatfile
    -   Type `/ta reload all` ingame.


