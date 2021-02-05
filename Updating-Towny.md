Here are instructions for performing a Towny Upgrade from a previous version:

## Towny Upgrade Instructions

1. Stop your server completely.
2. Backup your entire server!
    - If you use Towny in flatfile, Towny makes backups of the Towny files. (This doesn't include the blocks in the world! Full server backups do.)
    - You may want to take the latest .zip from the plugins\towny\backups\ folder and set it aside somewhere safe.
3. Download Towny_Advanced.zip, extract the .jar files, and upload them to your plugins folder.
    - Be sure you have removed any old Towny .jar files you already have in your plugins folder.
4. Read the [changelog](https://github.com/TownyAdvanced/Towny/blob/master/resources/ChangeLog.txt) or Release page to see what's new. 
    * The changelogs will detail things you must change manually (which doesn't happen very often now.)
    * All other config changes (new settings) be added automatically.
      * Towny's config will automatically add most new settings with their default settings.
    * **You do not have to delete/re-edit your config every time you update Towny.**
5. Start your server.
6. Make changes to newly added config values.
7. Stop your server.

## Special instructions
* Upgrade from pre-0.79.0.0
  * The chat section of config.yml has been move to a new file, channels.yml. Edit the new channels.yml to your liking.

* Upgrade from pre-0.82.0.0
  * Towny has had TownyPerms added. This new file located at townysettings\townyperms.yml will be generated when you first start your server using Towny 0.82.0.0 or higher.
    * TownyPerms adds town/nation ranks so server admins can specify what each rank can do (nomads, residents, mayors, kings, etc) Admins can also create custom ranks with custom permission sets. Any existing players set as assistants will lose their rank and need to have it re-assigned.

