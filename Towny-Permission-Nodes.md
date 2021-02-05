-   [Admin/Moderator Nodes](#adminmoderator-nodes)
-   [/Plot Nodes](#plot-nodes)
-   [/Resident Nodes](#resident-nodes)
-   [/Town Nodes](#town-nodes)
-   [/Nation Nodes](#nation-nodes)
-   [/Towny Nodes](#towny-nodes)
-   [/Townyworld Nodes](#townyworld-nodes)
-   [Chat Nodes](#chat-nodes)
-   [Wilderness Nodes](#wilderness-nodes)
-   [Miscellaneous Nodes](#miscellaneous-nodes)
-   [Info/Option/Meta Nodes](#infooptionmeta-nodes)

Towny has many permission nodes with which you can customize your server and it's separate worlds. By default Towny has already given out the correct permission nodes for a standard install in the townyperms.yml. Towny will read nodes from the townyperms.yml always, but it will also read permission nodes given by your (optional) permission plugin ie, GroupManager, LuckPerms. **Some admins make the mistake of placing Towny permission nodes into their permission plugin.** The only permission nodes you must give in your permission plugin is `towny.admin.*` to your admin group(s).

The only other permission node that isn't already given out is `towny.wild.*`. Giving this node will grant full build/destroy/switch/itemuse rights to players in the wilderness. You must decide if you want to give this out, and how:

* One option is to put it in the nomad section of the townyperms.yml file, which will enable all players server-wide to use the wilderness.
* The other option is to give it in your permission plugin, to whichever rank you want to use the wilderness.

_**Again because so many people seem to have trouble reading the above 2 paragraphs, in order to allow the use of the wilderness, you add exactly this node:**_

<h2 align=center>towny.wild.*</h2>
<br><br>

## Admin/Moderator Nodes

-   towny.admin: User is able to use /townyadmin, as well as the ability to build/destroy anywhere.
-   towny.admin.nation_zone : Made so that mods who dont have towny.admin can bypass the nation zone protection. Child node of towny.admin.
-   towny.admin.outlaw.teleport_bypass: User is unaffected by the outlaw-teleport feature, able to enter towns in which they are outlawed.
-   towny.admin.spawn: User is able to bypass the costs, warmups and cooldowns for spawning.
    - towny.admin.spawn.nocharge: User will not be charged to spawn to towns.
    - towny.admin.spawn.nocooldown: User will not have to wait to use the spawn commands after spawning.
    - towny.admin.spawn.nowarmup: User will not have to wait to spawn after using the spawn commands.

-   towny.command.townyadmin.*
    -   towny.command.townyadmin
    -   towny.command.townyadmin.set.*
        -   towny.command.townyadmin.set.mayor
        -   towny.command.townyadmin.set.plot - For mods who don't have the full towny.admin permission node but are able to change plots to other towns.
        -   towny.command.townyadmin.set.capital
        -   towny.command.townyadmin.set.title
        -   towny.command.townyadmin.set.surname
    -   towny.command.townyadmin.plot.*
        -   towny.command.townyadmin.plot.claim
    -   towny.command.townyadmin.resident.*
        -   towny.command.townyadmin.resident.friend
    -   towny.command.townyadmin.town.* - Allows a player to use '/ta town add/kick'
        -   towny.command.townyadmin.town.new
        -   towny.command.townyadmin.town.add
        -   towny.command.townyadmin.town.kick
        -   towny.command.townyadmin.town.delete
        -   towny.command.townyadmin.town.rename
        -   towny.command.townyadmin.town.bankhistory
        -   towny.admin.spawn
            -   towny.command.townyadmin.town.spawn.freecharge
    -   towny.command.townyadmin.nation.* - Allows a player to use '/ta nation add/kick'
        -   towny.command.townyadmin.nation.new
        -   towny.command.townyadmin.nation.add
        -   towny.command.townyadmin.nation.delete
        -   towny.command.townyadmin.nation.rename
        -   towny.command.townyadmin.nation.bankhistory
    -   towny.command.townyadmin.toggle.* - Allows use of '/ta toggle ...'
        -   towny.command.townyadmin.toggle.war
        -   towny.command.townyadmin.toggle.neutral
        -   towny.command.townyadmin.toggle.npc
        -   towny.command.townyadmin.toggle.devmode
        -   towny.command.townyadmin.toggle.debug
        -   towny.command.townyadmin.toggle.townwithdraw
        -   towny.command.townyadmin.toggle.nationwithdraw
    -   towny.command.townyadmin.givebonus - Allows use of '/ta givebonus...'
    -   towny.command.townyadmin.reload - Allows use of '/ta reload'
    -   towny.command.townyadmin.reset - Generate a fresh config.yml and perform a full reload of Towny.
    -   towny.command.townyadmin.backup - Perform a backup
    -   towny.command.townyadmin.newday - Run a new day event for taxes.
    -   towny.command.townyadmin.purge - Remove old resident files 'ta purge 30'
    -   towny.command.townyadmin.unclaim - Unclaims the plot you are standing in.
    -   towny.command.townyadmin.resident.delete - Deletes a specific resident '/ta res delete {name}'

-   towny.claimed.* : User can build/destroy/switch/item_use in all towns. **This node should be given to moderator ranks only in most cases.**
    > This node should only be given to server staff/moderators/admins. It should not be put into the townyperms.yml
    -   towny.claimed.alltown.*
        -   towny.claimed.alltown.build.* : User can build in all towns.
        -   towny.claimed.alltown.destroy.* : User can destroy in all towns.
        -   towny.claimed.alltown.switch.* : User can switch in all towns.
        -   towny.claimed.alltown.item_use.* : User can use use items in all towns.
    > This node can be given to the Assistant-type rank in townyperms.yml and they will be able to build/destroy over the entire town.
    -   towny.claimed.owntown.*
        -   towny.claimed.owntown.build.* : User can build in their town.
        -   towny.claimed.owntown.destroy.* : User can destroy in their town.
        -   towny.claimed.owntown.switch.* : User can switch in their town.
        -   towny.claimed.owntown.item_use.* : User can use items in their town.
        
    > This node can be given to the Assistant-type rank in townyperms.yml and they will be able to build/destroy over town-owned plots and not player owned plots.
    -   towny.claimed.townowned.* : User is able to edit specified/all block types in their town's owned plots (Town only, not resident owned).    
        -   towny.claimed.townowned.build.* : User can build in all town-owned plots.
        -   towny.claimed.townowned.destroy.* : User can destroy in all town-owned plots.
        -   towny.claimed.townowned.switch.* : User can switch in all town-owned plots.
        -   towny.claimed.townowned.item_use.* : User can use items in all town-owned plots.

## /Plot Nodes


-   towny.command.plot.*
    -   towny.command.plot.asmayor - For town plot management, grant this to any ranks you want to have the ability to:
        -   reclaim plots from players for the town.
        -   Toggle perms and plot settings on any plot in the town.
        -   Put plots up for sale and take them down again.
        -   Mayors and Assistants can still set plots for sale without the node.
    -   towny.command.plot.claim
    -   towny.command.plot.unclaim
    -   towny.command.plot.notforsale
    -   towny.command.plot.forsale
    -   towny.command.plot.evict
    -   towny.command.plot.perm
        - towny.command.plot.perm.hud
    -   towny.command.plot.toggle.*
        -   towny.command.plot.toggle.pvp
        -   towny.command.plot.toggle.explosion
        -   towny.command.plot.toggle.fire
        -   towny.command.plot.toggle.mobs
    -   towny.command.plot.set.*
        -   towny.command.plot.set.perm
        -   towny.command.plot.set.reset
        -   towny.command.plot.set.shop
        -   towny.command.plot.set.embassy
        -   towny.command.plot.set.arena
        -   towny.command.plot.set.wilds
        -   towny.command.plot.set.inn
        -   towny.command.plot.set.jail
        -   towny.command.plot.set.spleef
    -   towny.command.plot.clear
    -   towny.command.plot.group.*
        - towny.command.plot.group.add
        - towny.command.plot.group.remove
        - towny.command.plot.group.rename
        - towny.command.plot.group.set
        - towny.command.plot.group.toggle
        - towny.command.plot.group.forsale
        - towny.command.plot.group.notforsale

## /Resident Nodes

-   towny.command.resident.*
    -   towny.command.resident.list
    -   towny.command.resident.tax
    -   towny.command.resident.jail
    -   towny.command.resident.otherresident
    -   towny.command.resident.set.*
        -   towny.command.resident.set.perm
        -   towny.command.resident.set.mode
    -   towny.command.resident.spawn
    -   towny.command.resident.toggle.*
        -   towny.command.resident.toggle.pvp
        -   towny.command.resident.toggle.explosion
        -   towny.command.resident.toggle.fire
        -   towny.command.resident.toggle.mobs
        -   towny.command.resident.toggle.townclaim
        -   towny.command.resident.toggle.plotborder
        -   towny.command.resident.toggle.constantplotborder
        -   towny.command.resident.toggle.ignoreplots
        -   towny.command.resident.toggle.map
    -   towny.command.resident.friend

## /Town Nodes

-   towny.town.* : User has access to all .town permission nodes.
    -   towny.town.resident : User is able to join a town.
    -   towny.town.spawn.* : Grants all Spawn travel nodes
        -   towny.town.spawn.town : Ability to spawn to your own town.
        -   towny.town.spawn.nation : Ability to spawn to other towns in your nation.
        -   towny.town.spawn.ally : Ability to spawn to towns in nations allied with yours.
        -   towny.town.spawn.public : Ability to spawn to unaffilated public towns.
        -   towny.town.spawn.outpost : Ability to spawn to your own town's outposts. This is a child node of towny.town.spawn.town and must be negated if you do not want players to teleport to their outposts (ex in Groupmanager: - -towny.town.spawn.outpost)

- towny.command.town.*
    - towny.command.town.here
    - towny.command.town.list.*
        - towny.command.town.list.residents
        - towny.command.town.list.open
        - towny.command.town.list.balance
        - towny.command.town.list.name
        - towny.command.town.list.townblocks
        - towny.command.town.list.online
        - towny.command.town.list.public
        - towny.command.town.list.ruined
        - towny.command.town.list.bankrupt
    - towny.command.town.new : Required to create a town.
    - towny.command.town.leave
    - towny.command.town.withdraw
    - towny.command.town.deposit
    - towny.command.town.bankhistory
    - towny.command.town.rank.*
    - towny.command.town.reslist
    - towny.command.town.outlaw : Allows outlawing players in your town.
    - towny.command.town.outpost.list : Child node of towny.town.spawn.town
    - towny.command.town.set.*
        -   towny.command.town.set.board
        -   towny.command.town.set.mayor
        -   towny.command.town.set.homeblock
        -   towny.command.town.set.spawn
        -   towny.command.town.set.spawncost
        -   towny.command.town.set.outpost
        -   towny.command.town.set.perm
        -   towny.command.town.set.taxes
        -   towny.command.town.set.plottax
        -   towny.command.town.set.shoptax
        -   towny.command.town.set.embassytax
        -   towny.command.town.set.plotprice
        -   towny.command.town.set.shopprice
        -   towny.command.town.set.embassyprice
        -   towny.command.town.set.name : player can rename their town
        -   towny.command.town.set.tag
        -   towny.command.town.set.taxpercentcap
        -   towny.command.town.set.title
        -   towny.command.town.set.surname
    - towny.command.town.buy
    - towny.command.town.othertown
    - towny.command.town.plots : Use of the /town {name} plots
    - towny.command.town.say
    - towny.command.town.toggle.* : User has access to all town toggle commands (if a mayor or assistant, residents can toggle on their personal land.)
        -   towny.command.town.toggle.pvp
        -   towny.command.town.toggle.public
        -   towny.command.town.toggle.explosion
        -   towny.command.town.toggle.fire
        -   towny.command.town.toggle.mobs
        -   towny.command.town.toggle.taxpercent
        -   towny.command.town.toggle.open
        -   towny.command.town.toggle.jail
    - towny.command.town.mayor
    - towny.command.town.delete : player can delete their town
    - towny.command.town.join : a player can join an open town
    - towny.command.town.add : player can add a player to their town.
    - towny.command.town.kick :player can kick a player from their town.
    - towny.command.town.claim.*
        -   towny.command.town.claim.town : User is able to expand his town with /town claim (used when world is set as unclaimable in /townyworld)
        -   towny.command.town.claim.outpost : to allow/block claiming of outposts via permissions. (Will still require outposts to be enabled in the config.)
        -   towny.command.town.claim.town.multiple : to allow/block claiming of multiple plots using /town claim auto, /town claim rect, etc. Not given by default, you will have to add this to the mayor group in the townyperms.yml if you'd like to allow your mayors to do this.
    - towny.command.town.unclaim : player is able to unclaim town land.
        -   towny.command.town.unclaim.all
    - towny.command.town.online
    - towny.command.town.invite.*
        -   towny.command.town.invite.manage.* : User can manage invites.
            -   towny.command.town.add : User can add residents to towns.
                -   towny.command.town.invite.add 
            -   towny.command.town.invite.accept
            -   towny.command.town.invite.deny
        -   towny.command.town.invite.sent : User can see sent invites from their town.
        -   towny.command.town.invite.received : User can see received invites for their town.
        -   towny.command.town.invite : User can see invite help page.
        
        

## /Nation Nodes

- towny.nation.spawn.* : Grants all Spawn travel nodes
	-   towny.nation.spawn.nation: Ability to spawn to your own nation.
	-   towny.nation.spawn.ally : Ability to spawn to nations allied with yours.
	-   towny.nation.spawn.public : Ability to spawn to unaffilated public nations.

- towny.command.nation.*
	-   towny.command.nation.list
	    -   towny.command.nation.list.residents
	    -   towny.command.nation.list.towns
	    -   towny.command.nation.list.open
	    -   towny.command.nation.list.balance
	    -   towny.command.nation.list.name
	    -   towny.command.nation.list.townblocks
	    -   towny.command.nation.list.online
	    -   towny.command.nation.list.public
	-   towny.command.nation.new
	-   towny.command.nation.leave
	-   towny.command.nation.withdraw
	-   towny.command.nation.deposit
	-   towny.command.nation.deposit.other
	-   towny.command.nation.bankhistory
	-   towny.command.nation.rank.*
	-   towny.command.nation.king
	-   towny.command.nation.othernation
	-   towny.command.nation.say
	-   towny.command.nation.join
	-   towny.command.nation.set.*
            -   towny.command.nation.set.board
	    -   towny.command.nation.set.spawncost
	    -   towny.command.nation.set.spawn
	    -   towny.command.nation.set.king
	    -   towny.command.nation.set.capitol
	    -   towny.command.nation.set.taxes
	    -   towny.command.nation.set.name
	    -   towny.command.nation.set.title
	    -   towny.command.nation.set.surname
	    -   towny.command.nation.set.tag
	    -   towny.command.nation.set.mapcolor
	-   towny.command.nation.toggle.*
	    -   towny.command.nation.toggle.neutral
	    -   towny.command.nation.toggle.open
	    -   towny.command.nation.toggle.public
	-   towny.command.nation.invite.*
	    -   towny.command.nation.invite.manage.* : Ability to manage nation town invites.
	        -   towny.command.nation.add : User can add towns to nations.
	            -   towny.command.nation.invite.add
	        -   towny.command.nation.invite.accept
	        -   towny.command.nation.invite.deny
	    -   towny.command.nation.invite.sent : User can see sent invites from their nation.
	    -   towny.command.nation.invite.received : User can see received invites for their nation.
	    -   towny.command.nation.invite : User can see invite help page.
	-   towny.command.nation.ally.*
	    -   towny.command.nation.ally.manage.* : Ability to manage nation ally invites.
	        -   towny.command.nation.ally.add
	        -   towny.command.nation.ally.remove
	        -   towny.command.nation.ally.accept
	        -   towny.command.nation.ally.deny
	    -   towny.command.nation.ally.sent : User can see the sent ally invites for their nation.
	    -   towny.command.nation.ally.received : User can see the received ally invites for their nation.
	    -   towny.command.nation.ally : User can see the ally help page.
	-   towny.command.nation.enemy
	-   towny.command.nation.delete
	-   towny.command.nation.online
	-   towny.command.nation.add
	-   towny.command.nation.kick
	-   towny.command.nation.spawn
	-   towny.command.nation.townlist
        -   towny.command.nation.allylist
        -   towny.command.nation.enemylist
        -   towny.command.nation.merge

## /Towny Nodes

-   towny.command.towny.*
    -   towny.command.towny.map
    -   towny.command.towny.prices
    -   towny.command.towny.top
    -   towny.command.towny.tree
    -   towny.command.towny.time
    -   towny.command.towny.universe
    -   towny.command.towny.version
    -   towny.command.towny.war
    -   towny.command.towny.war.hud
    -   towny.command.towny.spy

## /Townyworld Nodes

-   towny.command.townyworld.*
    -   towny.command.townyworld.list
    -   towny.command.townyworld.set
    -   towny.command.townyworld.toggle.*
        -   towny.command.townyworld.toggle.claimable
        -   towny.command.townyworld.toggle.usingtowny
        -   towny.command.townyworld.toggle.pvp
        -   towny.command.townyworld.toggle.forcepvp
        -   towny.command.townyworld.toggle.explosion
        -   towny.command.townyworld.toggle.forceexplosion
        -   towny.command.townyworld.toggle.fire
        -   towny.command.townyworld.toggle.forcefire
        -   towny.command.townyworld.toggle.townmobs
        -   towny.command.townyworld.toggle.worldmobs
        -   towny.command.townyworld.toggle.revertunclaim
        -   towny.command.townyworld.toggle.revertexpl
    -   towny.command.townyworld.regen
    -   towny.command.townyworld.undo

## Chat Nodes

-   towny.chat.general : Allows a player to use the globalchat channel
-   towny.chat.town : Allows a player to use townchat
-   towny.chat.nation : Allows a player to use nationchat
-   towny.chat.mod : Allows a player to use moderatorchat
-   towny.chat.admin : Allows a player to use adminchat
-   towny.chat.local : Allows a player to use localchat channel
-   towny.chat.spy : Allows a player to see all chat in all channels

-   towny.chat.join.{channelname} : Allows a player to /join {channelname}
-   towny.chat.leave.{channelname} : Allows a player to /leave {channelname}

-   townychat.mod.mute : Allows a moderator to /chmute {channel} {player}, muting another player in a channel.
-   townychat.mod.unmute: Allows a moderator to /chunmute {channel} {player}, un-muting another player in a channel.

-   townychat.chat.color: Allows players to use colors to format chat messages.
-   townychat.chat.format.*: Allows the use of all chat format modifiers like bold, italics. Defaults to Ops.
    - Child nodes:
    - townychat.chat.format.bold
    - townychat.chat.format.italic
    - townychat.chat.format.magic
    - townychat.chat.format.underlined
    - townychat.chat.format.strike
-   townychat.chat.format.reset: Allows the use of &r to reset chat formatting. Defaults to everyone.

## Wilderness Nodes

-   towny.wild.*
    -   towny.wild.build.*
    -   towny.wild.destroy.*
    -   towny.wild.switch.*
    -   towny.wild.item_use.*
        -   towny.wild.build.{materialname}
        -   towny.wild.destroy.{materialname}
        -   towny.wild.switch.{materialname}
        -   towny.wild.item_use.{materialname}

## Miscellaneous Nodes

- towny.outlaw.jailer : Required to cause otlaws killed in your town to be sent to your jail. Given to mayors, assistants and sheriffs by default.

- towny.tax_exempt - Grant this permisison to any rank you do not want to pay taxes. ** ONLY works in TownyPerms **. Will not work in external permission plugins.

- towny.bypass_death_costs - Stops a player from paying the death costs.

- towny.town.{townname}:

  Players who are in towns now receive a permission node, towny.town.{townname}.

  -   This can be useful for server operators who want to test if a player has a permission node to make sure they are part of a town.
  -   Examples could include an NPC that required a specific permission node to interact with.

-   TownyPerms feature: town/nation placeholder nodes
    -   You can now add placeholder permission nodes into Townyperms.
    -   Will not work for nomads with no town.
    -   For example: adding stargate.network.{townname} to the default Town section in the townyperms.yml will assign the permission node stargate.network.england, to all the online members of the town England.
    -   use {townname} for towns, and {nationname} in your nation section.

- For servers who's Permission Plugin doesn't support info/option nodes:
  -   prefix.prefixhere
  -   suffix.suffixhere
      -   Used for the towny chat configuration's {permprefix} and {permsuffix} when using a permission plugin without prefix: and suffix: sections.
  -   towny_maxplots.x {with x being a number eg towny_maxplots.2}
  -   towny_extraplots.x {with x being a number eg towny_extraplots.2}
  -   towny_maxoutposts.x {with x being a number eg towny_maxoutposts.2}



## Info/Option/Meta Nodes

> This is similar to a permission node as it is added to your permission nodes file(s). Added to the info: section of Groupmanagers' groups or the options: section of PEX's groups. They are called meta nodes in LuckPerms.

-   Setting default chat channels/modes on join to the server.
    -   towny_default_modes: 'map,townclaim,plotborder,global,local,town,nation,mod,admin'
        -   sets the default modes on residents, found in the /res set mode command stub.
        -   puts players into a townychat chatchannel when they join the server.

-   towny_maxoutposts: {number}

> This info node is used to limit the number of outposts a player can claim based on what permission group they are in.

-   towny_maxplots: {number}

> This info node is used to limit the number of plots a player can own based on what permissions group they are in. If a group doesn't have this node or the node is set to -1 Towny will default back to the max_plots_per_resident in config. Setting max_plots_per_resident to -1 with no permission node, or a node set to -1 will allow infinite plots.

> Example:
>
> ``` {.prettyprint}
>        groups:
>           Default:
>             default: true
>             permissions:
>             - general.spawn
>             inheritance: []
>             info:
>               prefix: ''
>               build: true
>               suffix: ''
>               towny_maxplots: 1
>               towny_default_modes: 'local'
>               towny_maxoutposts: 2
>
>           Admins:
>             default: false
>             permissions:
>             - '*'
>             inheritance:
>             info:
>               prefix: ''
>               build: true
>               suffix: ''
>               towny_maxplots: -1
> ```

town_extraplots: {number}

-   Used like the towny_maxplots node, ie: in GM's info node section where prefix and suffix's are set.
-   ex: towny_extraplots: 1
-   Used to give players who have the town_maplots permission node, but who are also a mayor or assistant.
-   Giving these extra plots, allows them to claim their maxplot amount plus the extra plot amount


