This page lists common problems and their solutions.
- [Admin-solvable Problems](https://github.com/TownyAdvanced/Towny/wiki/Troubleshooting#admin-solvable-problems)
  - [Towny locked in safe mode](https://github.com/TownyAdvanced/Towny/wiki/Troubleshooting#towny-locked-in-safe-mode)
  - [Multiple Prefixes Seen on the Chatline](https://github.com/TownyAdvanced/Towny/wiki/Troubleshooting#multiple-prefixes-seen-on-the-chatline)
- [Player-solvable Problems](https://github.com/TownyAdvanced/Towny/wiki/_Troubleshooting#player-solvable-problems)
  - [Residents can build/destroy in town plots they do not own](https://github.com/TownyAdvanced/Towny/wiki/Troubleshooting#residents-can-builddestroy-in-town-plots-they-do-not-own)

# Admin-solvable Problems

## Towny locked in safe mode

Upon starting your server you might sometimes not be able to move, bouncing back to your login position. This happens when Towny goes into Safe Mode. Safe Mode only occurs when the Towny data files (flatfile or sql) become corrupted, and require repairs. To prevent griefing Towny automatically locks players' positions.

To fix your data files, there are two methods.

### Method One
The easier of the two methods is to use one of Towny's self-made backups. Backups are made automatically each time your server is started and upon each Towny New Day. Backups are only made if your server is running a flatfile database for Towny.

1. Stop your server.
2. Navigate to the plugins\towny folder.
3. Find the data folder and rename it to olddata, if you successfully fix the problem you can delete this folder later on.
4. Open the backup folder.
5. Select the latest or second-to-latest archive there and open it with winrar/winzip/your archiving program of choice.
6. Move the data folder found within into the plugins\towny folder.
7. Start your server and check your server.log's Towny section. If you see Towny still in safe mode you will need to start the process over again at step 3, this time using an older backup from the plugin\towny\backup folder.

### Method Two
This is for experienced users only. Manually editing the Towny data should only be done in extreme cases where backups are too old to revert to or do not exist at all.

1. Stop your server.
2. Navigate to the plugins\towny\ folder.
3. Copy your data folder to somewhere safe and rename it to databackup. This is so that if you do not properly edit the data folder you have something to fall back on.
4. In your config.yml set debug_mode: true.
5. Start your server up, open your server.log and find the Towny portion.

**Note: Most of the instructions below are for Towny versions older than 0.96.3.0.**
>In 0.96.3.0 and onwards the relationships between Towns and Nations, and Residents and Towns, are more disconnected with Residents storing their Town, and Towns storing their Nation. Because of this Towny will self-correct any incorrect data. If you are using an older version of Towny the tips below could be helpful in solving a safemode experience.

There can be 4 types of things wrong with the data. Usually there is something in a file that names something not found in the rest of the files. ie: A townname.txt that lists a resident that is not found in the residents.txt, or a worldname.txt that lists a town not found in the towns.txt.

Worlds : Worlds are listed in the worlds.txt and have individual worldname.txt files. If Towny wont load because of a bad World find its worldname.txt and confirm that all the towns listed in the file are also listed in the towns.txt. If there is an extra town in the list then you must decide what to do next: 

>If the towns.txt does not include the town, but there is a townname.txt file for that town in the towny\data\towns folder, you should probably add the town's name to the towns.txt file. 

>If the towns.txt does not include the town, and there is no townname.txt found in the towny\data\towns folder, then you should probably delete the town from the towns list in the worldname.txt file.

Nations: Nation file's mainly become corrupt by a bad town being listed. Open the nationname.txt found in the towny\data\nations folder and look at the towns listed there, making sure that all of the towns are also listed in the towns.txt in the towny\data folder. If there is an extra town in the list then you must decide what to do next: 

> If the towns.txt does not include the town, but there is a townname.txt file for that town in the towny\data\towns folder, you should probably add the town's name to the towns.txt file. 

>If the towns.txt does not include the town, and there is no townname.txt found in the towny\data\towns folder, then you should probably delete the town from the towns list in the nationname.txt file.

Towns: Town files mainly become corrupt by a bad resident being listed in them. Open the townname.txt found in the towny\data\towns folder and look at the residents listed there, making sure that all of them are also found in the residents.txt found in the towny\data folder. If there is an extra resident in the list then you must decide what to do next: 

> If the residents.txt does not include the player, but there is a residentname.txt file for that player in the towny\data\residents folder, and that file lists the town in their residentname.txt, you should probably add the resident's name to the townname.txt file. 
> If the residents.txt does not include the player, and there is no residentname.txt found in the towny\data\residents folder, then you should probably delete the player from the townname.txt file.

Residents: Bad resident data usually means that a player in the residents.txt has no residentname.txt in the towny\data\residents folder. You can, in most cases delete the entry in the residents.txt and this will solve the problem.

After editing the data files manually start the server and check the server.log's Towny section to see if the corruption is fixed. It may list a new-found piece of bad data. Repeat the above trouble-shooting steps to attempt to fix this new-found corruption.


## Multiple Prefixes Seen on the Chatline
If you find that your chat line looks like this: [Owner]Owner[Owner]Steve with 2 or more prefixes you need to change your chatconfig.yml to work with your settings.

Three chat tags can be at fault here. 
1. {group} which is the group name from your permission plugin. 
2. {permprefix} which is the prefix sections of your permission plugin. 
3. {modplayername} which would contain parts added by other plugins altering chat.

To fix this follow these steps:

1. In the \towny\settings\chatconfig.yml
    - Find the 'channel_formats:' section and the 'global:' line.
    - Change {modplayername} to {playername}.
    - Remove {group}.

2. In-game type '/townychat reload'. This should solve your problem.

Doing these steps make townychat use the {permprefix} chat tag only, pulling the coloured prefix from your permission plugin.

# Player-solvable Problems

## Residents can build/destroy in town plots they do not own
If a mayor finds his players can build/destroy everywhere in town and only wants them to build/destroy in their own plots he needs to do the following.

1. Type the command /town set perm off
2. Type the command /town set perm reset

The first command shuts off all permissions for residents/allies/outsiders in the town. The second command sets the newly changed default perm-line to all town-owned plots. Neither command affects the mayor's personally owned plots in town.