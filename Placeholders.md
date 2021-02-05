Since Towny Version 0.94.0.18, Towny has provided some PlaceholderAPI support without needing an extension from the PAPI eCloud. Use of these placeholders requires PlaceholderAPI to be installed to be functional. Towny can not be configured to use placeholders at this time, though TownyChat can. 

If you are unable to run at minimum Towny 0.94.0.18, you can download the [old PAPI Towny Expansion](https://api.extendedclip.com/expansions/towny/) instead. 

You are able to format some of the Placeholder's appearances via the Towny [config.yml](https://github.com/TownyAdvanced/Towny/wiki/Default-Config.yml)'s papi_chat_formatting section. (Ex: removing the []'s, or changing colours.)

<details>
<summary> Available Tags in order of oldest to newest</summary>

_Introduced as of v0.95.0.0_
- `%townyadvanced_town%` - Displays town name (if they have one.)
- `%townyadvanced_town_formatted%` - Displays long-form town name (if they have one.)
- `%townyadvanced_nation%` - Displays nation name (if they have one.)
- `%townyadvanced_nation_formatted%` - Displays long-form nation name (if they have one.)
- `%townyadvanced_town_balance%` - Displays town bank value.
- `%townyadvanced_nation_balance%` - Displays nation bank value.
- `%townyadvanced_town_tag%` - Displays town tag (if they have one.)
- `%townyadvanced_town_tag_override%` - Displays town tag (if they have one,) or the full town name.
- `%townyadvanced_nation_tag%` - Displays nation tag (if they have one.)
- `%townyadvanced_nation_tag_override%` - Displays nation tag (if they have one,) or the full nation name.
- `%townyadvanced_towny_tag%` - Displays town and nation tags.
- `%townyadvanced_towny_tag_override%` - Displays town and nation tags if they exist, falling back to names if they don't.
- `%townyadvanced_towny_tag_formatted%` - Displays town and nation tags if they exist, falling back to long-form names if they don't.
- `%townyadvanced_title%` - Displays king-granted title.
- `%townyadvanced_surname%` - Displays king-granted surname.
- `%townyadvanced_towny_name_prefix%` - Displays mayor and king prefix.
- `%townyadvanced_towny_name_postfix%` - Displays mayor and king postfix.
- `%townyadvanced_towny_prefix%` - Displays title if it exists, falls back to mayor and king prefixes.
- `%townyadvanced_towny_postfix%` - Displays surname if it exists, falls back to mayor and king postfixes.
- `%townyadvanced_towny_colour%` - Used to show colours before nomads, residents, mayors and kings. (Set in the config.yml.)  

_Introduced as of v0.95.1.0_
- `%townyadvanced_town_residents_amount%` - Number of residents in a town.
- `%townyadvanced_town_residents_online%` - Number of residents in a town that are currently online.
- `%townyadvanced_town_townblocks_used%` - Number of townblocks claimed by a resident's town.
- `%townyadvanced_town_townblocks_bought%` - Number of townblocks bought by a resident's town.
- `%townyadvanced_town_townblocks_bonus%` - Number of bonus blocks given to a resident's town.
- `%townyadvanced_town_townblocks_maximum%` - Number of townblocks a town has available to claim.
- `%townyadvanced_town_townblocks_natural_maximum%` - Number of townblocks a town has available to claim, not counting bonus/bought townblocks.
- `%townyadvanced_town_mayor%` - A resident's town's mayor's name.
- `%townyadvanced_nation_king%` - A resident's nation's king's name.
- `%townyadvanced_resident_friends_amount%` - Number of friends a resident has.
- `%townyadvanced_nation_residents_amount%` - Number of residents in a resident's nation.
- `%townyadvanced_nation_residents_online%` - Number of residents in a resident's nation that are currently online.
- `%townyadvanced_nation_capital%` - Name of a resident's nation's capital.

_Introduced as of v0.95.2.0_
- `%townyadvanced_daily_town_upkeep%` - Shows town's upkeep cost.
- `%townyadvanced_daily_nation_upkeep%` - Shows nation's upkeep cost.
- `%townyadvanced_has_town%` - Returns true or false whether the resident has a town.
- `%townyadvanced_has_nation%` - Returns true or false whether the resident has a nation.

_Introduced as of v0.96.0.0_
- `%townyadvanced_nation_tag_town_formatted%` - Shows the nation tag and the full town name. If nation tag is not set, only the town name is shown.

_Introduced as of v0.96.2.0_
- `%townyadvanced_town_ranks%` - Displays either Mayor, or the various town ranks a player has or nothing if they have none.
- `%townyadvanced_nation_ranks%` - Displays either King, or the various nation ranks a player has or nothing if they have none.
- `%townyadvanced_player_status%` - Displays Nomad, Resident, Mayor or King, depending on what position the player is in.

_Introduced as of v0.96.3.0_
- `%townyadvanced_town_prefix%` - Display the config-defined prefix of the player's town (ex: ruins, settlement, ...)
- `%townyadvanced_town_postfix%` - Display the config-defined postfix of the player's nation (ex: ruins, settlement, ...)
- `%townyadvanced_nation_prefix%` - Display the config-defined prefix of the player's town (ex: lands, realms, ...)
- `%townyadvanced_nation_postfix%` - Display the config-defined postfix of the player's nation (ex: lands, realms, ...)
- `%townyadvanced_player_jailed%` - Display true is the player is jailed, otherwise false.
- `%townyadvanced_player_plot_type%` - Display the townblock's type at the resident's location (ex: shop), or "" if none.
- `%townyadvanced_player_plot_owner%` - Display true if the resident is owning the townblock at his location.
- `%townyadvanced_nation_tag_town_name%` - Displays nation tag (if set, otherwise blank,) followed by the Town name (if the player is part of a town.)
- `%townyadvanced_daily_town_tax%` - Displays the daily tax charged by the town on the residents.
- `%townyadvanced_daily_nation_tax%` - Displays the daily tax charged by the nation on the towns.

_Introduced as of v0.96.6.0_
- `%townyadvanced_player_location_town_or_wildname%` - Displays either the townname at the location or the wilderness name.
- `%townyadvanced_player_location_formattedtown_or_wildname%` - Displays either the formatted townname at the location or the wilderness name.
- `%townyadvanced_player_location_town_prefix%` - Displays the town's prefix or blank.
- `%townyadvanced_player_location_town_postfix%` - Displays the town's postfix or blank.
- `%townyadvanced_player_location_pvp%` - Displays (PVP) or blank, depending on pvp status of the location.
- `%townyadvanced_nation_map_color_hex%` - Returns the hex colour code of the nation's mapcolor set with /t set mapcolor (seen in dynmap-towny.)

</details>

<details>
<summary> Available Tags in Order of Type</summary>

#### Town&Nation Prefixes/Tags
- `%townyadvanced_town%` - Displays town name (if they have one.)
- `%townyadvanced_town_formatted%` - Displays long-form town name (if they have one.)
- `%townyadvanced_town_tag%` - Displays town tag (if they have one.)
- `%townyadvanced_town_tag_override%` - Displays town tag (if they have one,) or the full town name.


- `%townyadvanced_nation%` - Displays nation name (if they have one.)
- `%townyadvanced_nation_formatted%` - Displays long-form nation name (if they have one.)
- `%townyadvanced_nation_tag%` - Displays nation tag (if they have one.)
- `%townyadvanced_nation_tag_override%` - Displays nation tag (if they have one,) or the full nation name.
- `%townyadvanced_nation_tag_town_formatted%` - Shows the nation tag and the full town name. If nation tag is not set, only the town name is shown.
- `%townyadvanced_nation_tag_town_name%` - Displays nation tag (if set, otherwise blank,) followed by the Town name (if the player is part of a town.)


- `%townyadvanced_towny_tag%` - Displays town and nation tags.
- `%townyadvanced_towny_tag_override%` - Displays town and nation tags if they exist, falling back to names if they don't.
- `%townyadvanced_towny_tag_formatted%` - Displays town and nation tags if they exist, falling back to long-form names if they don't.


#### Resident:
- `%townyadvanced_title%` - Displays king-granted title.
- `%townyadvanced_surname%` - Displays king-granted surname.
- `%townyadvanced_towny_name_prefix%` - Displays mayor and king prefix.
- `%townyadvanced_towny_name_postfix%` - Displays mayor and king postfix.
- `%townyadvanced_towny_prefix%` - Displays title if it exists, falls back to mayor and king prefixes.
- `%townyadvanced_towny_postfix%` - Displays surname if it exists, falls back to mayor and king postfixes.
- `%townyadvanced_town_ranks%` - Displays either Mayor, or the various town ranks a player has or nothing if they have none.
- `%townyadvanced_nation_ranks%` - Displays either King, or the various nation ranks a player has or nothing if they have none.
- `%townyadvanced_player_status%` - Displays Nomad, Resident, Mayor or King, depending on what position the player is in.
- `%townyadvanced_towny_colour%` - Used to show colours before nomads, residents, mayors and kings. (Set in the config.yml.)  

- `%townyadvanced_resident_friends_amount%` - Number of friends a resident has.
- `%townyadvanced_has_town%` - Returns true or false whether the resident has a town.
- `%townyadvanced_has_nation%` - Returns true or false whether the resident has a nation.
- `%townyadvanced_player_jailed%` - Display true is the player is jailed, otherwise false.

#### Town:
- `%townyadvanced_town_residents_amount%` - Number of residents in a town.
- `%townyadvanced_town_residents_online%` - Number of residents in a town that are currently online.
- `%townyadvanced_town_townblocks_used%` - Number of townblocks claimed by a resident's town.
- `%townyadvanced_town_townblocks_bought%` - Number of townblocks bought by a resident's town.
- `%townyadvanced_town_townblocks_bonus%` - Number of bonus blocks given to a resident's town.
- `%townyadvanced_town_townblocks_maximum%` - Number of townblocks a town has available to claim.
- `%townyadvanced_town_townblocks_natural_maximum%` - Number of townblocks a town has available to claim, not counting bonus/bought townblocks.
- `%townyadvanced_town_mayor%` - A resident's town's mayor's name.
- `%townyadvanced_town_prefix%` - Display the config-defined prefix of the player's town (ex: ruins, settlement, ...)
- `%townyadvanced_town_postfix%` - Display the config-defined postfix of the player's nation (ex: ruins, settlement, ...)


#### Nation:
- `%townyadvanced_nation_residents_amount%` - Number of residents in a resident's nation.
- `%townyadvanced_nation_residents_online%` - Number of residents in a resident's nation that are currently online.
- `%townyadvanced_nation_king%` - A resident's nation's king's name.
- `%townyadvanced_nation_capital%` - Name of a resident's nation's capital.
- `%townyadvanced_nation_prefix%` - Display the config-defined prefix of the player's town (ex: lands, realms, ...)
- `%townyadvanced_nation_postfix%` - Display the config-defined postfix of the player's nation (ex: lands, realms, ...)
- `%townyadvanced_nation_map_color_hex%` - Returns the hex colour code of the nation's mapcolor set with /t set mapcolor (seen in dynmap-towny.)

#### Money:
- `%townyadvanced_town_balance%` - Displays town bank value.
- `%townyadvanced_nation_balance%` - Displays nation bank value.
- `%townyadvanced_daily_town_upkeep%` - Shows town's upkeep cost.
- `%townyadvanced_daily_nation_upkeep%` - Shows nation's upkeep cost.
- `%townyadvanced_daily_town_tax%` - Displays the daily tax charged by the town on the residents.
- `%townyadvanced_daily_nation_tax%` - Displays the daily tax charged by the nation on the towns.

#### Location:
- `%townyadvanced_player_plot_type%` - Display the townblock's type at the resident's location (ex: shop), or "" if none.
- `%townyadvanced_player_plot_owner%` - Display true if the resident is owning the townblock at his location.
- `%townyadvanced_player_location_town_or_wildname%` - Displays either the townname at the location or the wilderness name.
- `%townyadvanced_player_location_formattedtown_or_wildname%` - Displays either the formatted townname at the location or the wilderness name.
- `%townyadvanced_player_location_town_prefix%` - Displays the town's prefix or blank.
- `%townyadvanced_player_location_town_postfix%` - Displays the town's postfix or blank.
- `%townyadvanced_player_location_pvp%` - Displays (PVP) or blank, depending on pvp status of the location.


</summary>