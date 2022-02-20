# ProtectionStones

This plugin uses a specified type of minecraft block as a protection block. When a player placed a block of that type, they are able to protect a region around them. The size of the protected region is configurable in the plugins config file. You can also set which flags players can change and also the default flags to be set when a new region is created.




### Configuration
<details>
<summary>Configuration</summary>
Run Once First

If you would like to change the basic settings then simply run the plugin once so it creates it's config.yml file then edit the file to change the settings, and then reload the plugin to allow the settings to take effect. The changes only effect newly protected regions and will not effect old ProtectionStone Regions.

ProtectionStones Has The Following Settings:
PS (WorldGuard) Region Flags

Here are some examples of the WorldGuard Region Flags (all are currently able to be set):

Flag.chest-access: (ALLOW/DENY) CHEST-ACCESS Flag set to DENY by default, if set to DENY only the ProtectionStone Owner and Members can use chests in the region.

Flag.entry: (ALLOW/DENY) ENTRY Flag set to ALLOW by Default, if set to DENY only the ProtectionStone Owner and Members can enter the region.

Flag.mob-spawning: (ALLOW/DENY) MOB-SPAWNING Flag set to DENY by default, if set to DENY mobs won't spawn in the region.

Flag.pvp: (ALLOW/DENY) PVP Flag set to DENY by default, if set to DENY PVP is turned off in the region.

Flag.use: (ALLOW/DENY) USE Flag set to DENY by default, if set to DENY only the ProtectionStone Owner and Members can use items in the region.

Flag.greeting: Default GREETING Message Flag message for entering a region. This can use %player% and will replace this token with the player's name.

Flag.farewell: Default FAREWELL Message Flag message for leaving a region. This can use %player% and will replace this token with the player's name.

Visit WorldGuard for the complete list of WorldGuard Region Flags and more information.
PS (WorldGuard) Region Sizes

These are the default blocks that can be used, any block can be used and up to 16 block types, but admin beware what you select.

Blocks.COAL_ORE: Default is size 5 which creates a 11x11x11 region.

Blocks.LAPIS_ORE: Default is size 10 which creates a 21x21x21 region.

Blocks.DIAMOND_ORE: Default is size 20 which creates a 41x41x41 region.

The size number is the distance from the placement of the ProtectionStone (usually the center of the cube) to the outside edge.

Here is a list of all the valid Bukkit Names, many of these names are not blocks, but the blocks you may use.

Note: If you wish to use Redstone Ore use GLOWING_REDSTONE_ORE instead of REDSTONE_ORE, which is data item value 74 (not 73).
Additional Settings

Region.SKYBEDROCK: (overrides the Y-Axis of the created region) default is false, set to true and all regions will be created with a vertical area from sky down to bedrock. This does not effect the X-Axis or the Z-Axis Sizes.

Region.NODROP: Makes all ProtectionStones a single use block, default is false. If set to true, breaking a ProtectionStone removes your region but doesn't give you back the ProtectionStone.

Region.AUTOHIDE: Automatically hides ProtectionStones after placement, defaults to false.

Region.NOSILKTOUCH: Blocks Silk Touch Pickaxe Drops, default is false. If set to true, breaking most blocks in your ProtectionStone block list should return the normal item that is dropped. If you have Region.NOSILKTOUCH set to true and have COAL_ORE as one of your blocks then breaking it with a Silk Touch Pickaxe should return the normal piece of coal. Remember that some blocks always return an ore block, like GOLD_ORE and IRON_ORE. Only effects blocks in your list.

Region.BLOCKPISTONS If you set it to true, all blocks moved by pistons are checked to see if any of the blocks are in the ProtectionStones Blocks List (meaning a material that could be used as a PS), and if they are the piston won't move. This is set to false by default.

Region.LIMIT: Allows you to place a count limit on created regions, defaults to -1 which means no limits, -2 which means use Group Limits (see below), 0 means all block placement is temporarily blocked, any positive number is the maximum number of regions a player can create. This region limit includes all owned regions both ProtectionStones created regions and normal WorldGuard Regions.

Region.SAVETIMER: WorldGuard Regions for all worlds are saved on server restart or if the plugins are /reload(ed), but this setting allows for more flexibility.

-1 = Save after all PS region changes (which is the default setting and how older versions of PS work).

0 = Don't save PS region changes, which would only get saved on the restart or reload.

n = A number meaning how many minutes to wait until the next PS region save. This number is in minutes. Don't set it to low or you will cause large amounts of server lag, If you use this setting the first save happens five minutes after the server starts, and then once each time your time limit is reached.

Region.PRIORITYOVERRIDE: If set to true (default is false), players are allowed to place "sub-regions" within parent regions that have a priority level set to -1.

For example, a player called "townowner" would create a large PS protected region, then set other sub regions up to protect restricted areas in their town, for example, their home. Then "townowner" would use the "/ps priority -1" command to set the large "town" region's priority to the correct number to allow players to claim regions there.

Then "homeowner" would go to the town and place their PS to create their "plot" in the town.

Priority: Sets the WorldGuard Region Priority Level for all new PS Regions created (default is 0, which is the setting in older versions of PS).
Group Limits

To use Group Limits do the following:

1) Set Region.LIMIT to -2

2) Set your group block placement limits, there are nine groups. The defaults are below.

Group:

LIMIT1: 0

LIMIT2: 1

LIMIT3: 3

LIMIT4: 7

LIMIT5: -1

LIMIT6: 0

LIMIT7: 0

LIMIT8: 0

LIMIT9: 0

Just like the Region.LIMIT setting: -1 means unlimited blocks, 0 means no blocks can be placed.

3) Set your group block type limits, there are nine groups that work with with the limit groups above. The defaults are below.

BLOCKS1: COAL_ORE LAPIS_ORE DIAMOND_ORE

BLOCKS2: COAL_ORE LAPIS_ORE DIAMOND_ORE

BLOCKS3: COAL_ORE LAPIS_ORE DIAMOND_ORE

BLOCKS4: COAL_ORE LAPIS_ORE DIAMOND_ORE

BLOCKS5: COAL_ORE LAPIS_ORE DIAMOND_ORE

BLOCKS6: COAL_ORE LAPIS_ORE DIAMOND_ORE

BLOCKS7: COAL_ORE LAPIS_ORE DIAMOND_ORE

BLOCKS8: COAL_ORE LAPIS_ORE DIAMOND_ORE

BLOCKS9: COAL_ORE LAPIS_ORE DIAMOND_ORE

The blocks listed in the blocks must have a space between them if there is more than one. They must also appear in the Blocks Section of the config.yml. The Limit Number is the total PS/World Guard Regions the player in this group can own, the blocks are the only blocks that the player in this group can place.

4) Give your player permission in your permission plugin, only add them to one group. Here are the permissions all are defaulted to false:

protectionstones.group1, protectionstones.group2, protectionstones.group3, protectionstones.group4, protectionstones.group5, protectionstones.group6, protectionstones.group7, protectionstones.group8, protectionstones.group9

If you forget to set a player to a group in step #4 they will be set to zero ProtectionStones.

If you set a player to more than one group in step #4 they will be set to the first group that they have permissions for. So for best results always set your Group.Limit list in ascending order to protect against a player getting a higher block limit due to a multiple permissions mistake.

Exclusion.WORLDS: This is a list of worlds (seperated by spaces) to exclude from creating ProtectionStone Regions.

Exclusion.PLACEMENT: This option set to "false" will block the placement of ProtectionStones in excluded worlds and give a message about ProtectionStones not being allowed. If you set it to "true" blocks in the ProtectionStones block list are allowed to be placed but don't create ProtectionStone Regions. Both settings only effect worlds that have been added to the Exclusion.WORLDS List.

NOTE: Explosion.DETECTION has been removed due to conflicts with some updated plugins.

Don't forget to reload your server plugins to make the changes take effect.
</details>

### Permissions
<details>
<summary>Permissions</summary>
The following permissions are available if you would like to use them.

"protectionstones.create" for placing ProtectionStones (default set to true). Also checks WorldGuard for player permission to place blocks in this location.

"protectionstones.destroy" for breaking ProtectionStones (default set to true). Also checks WorldGuard for player permission to break blocks in this location.

"protectionstones.view" for ProtectionStones View Command (default set to true).

"protectionstones.center" for ProtectionStones Center Command (default set to true).

"protectionstones.info" for ProtectionStones Info Command (default set to true), does not effect the sub commands.

"protectionstones.hide" for ProtectionStones Hide Command (default set to op, changed from true).

"protectionstones.unhide" for ProtectionStones Unhide Command (default set to op, changed from true).

"protectionstones.priority" for ProtectionStones Priority Command (default set to true).

"protectionstones.superowner" Overrides in region commands owner checks (default set to op).

"protectionstones.group1" for ProtectionStones Group Limiting Group #1 (default set to false).

"protectionstones.group2" for ProtectionStones Group Limiting Group #2 (default set to false).

"protectionstones.group3" for ProtectionStones Group Limiting Group #3 (default set to false).

"protectionstones.group4" for ProtectionStones Group Limiting Group #4 (default set to false).

"protectionstones.group5" for ProtectionStones Group Limiting Group #5 (default set to false).

"protectionstones.group6" for ProtectionStones Group Limiting Group #6 (default set to false).

"protectionstones.group7" for ProtectionStones Group Limiting Group #7 (default set to false).

"protectionstones.group8" for ProtectionStones Group Limiting Group #8 (default set to false).

"protectionstones.group9" for ProtectionStones Group Limiting Group #9 (default set to false).

Only place a player in one group, by setting only one to "true".

"protectionstones.owners" for ProtectionStones Owners Commands (default set to op). This includes the following three commands:"/ps addowner [player], /ps removeowner [player], /ps info owners

"protectionstones.members" for ProtectionStones Members Commands (default set to true). This includes the following three commands:"/ps add [player], /ps remove [player], /ps info members

"protectionstones.flags" for ProtectionStones Flags Commands (default set to true). This includes the following three commands:"/ps info flags, /ps flag [flag name] [setting], /ps flag defaults

See the Commands Page to see the available flags.

Commands associated to the permissions above must be used while standing in the ProtectionStones Protected Area that you own.

"protectionstones.toggle" for ProtectionStones Toggle Command (default set to op).

"protectionstones.region" for ProtectionStones Region Commands for Admins (default set to op). This includes the following five commands:"/ps region count [player], /ps region list [player], /ps region remove [player], /ps region regen [player], /ps region disown [player]

As a note /ps info region must be performed while standing in a region.

"protectionstones.admin" for ProtectionStones Admin Commands for Admins (default set to op). This includes the following ten commands:"/ps admin version, /ps admin settings, /ps admin lastlogon [player], /ps admin lastlogons [days], /ps admin hide, /ps admin unhide, /ps admin stats [player], /ps admin cleanup remove [days], /ps admin cleanup regen [days], /ps admin cleanup disown [days]
Flag Setting Permissions

These permissions only effect the /ps flag command, not the default flags set to a new region.

"protectionstones.flag.passthrough" (default set to true)

"protectionstones.flag.build" (default set to false)

"protectionstones.flag.pvp" (default set to true)

"protectionstones.flag.chest-access" (default set to true)

"protectionstones.flag.pistons" (default set to true)

"protectionstones.flag.tnt" (default set to true)

"protectionstones.flag.lighter" (default set to true)

"protectionstones.flag.use" (default set to true)

"protectionstones.flag.vehicle-place" (default set to true)

"protectionstones.flag.vehicle-destroy" (default set to true)

"protectionstones.flag.sleep" (default set to true)

"protectionstones.flag.mob-damage" (default set to true)

"protectionstones.flag.mob-spawning" (default set to true)

"protectionstones.flag.deny-spawn" (default set to true)

"protectionstones.flag.invincible" (default set to true)

"protectionstones.flag.creeper-explosion" (default set to true)

"protectionstones.flag.ghast-fireball" (default set to true)

"protectionstones.flag.enderman-grief" (default set to true)

"protectionstones.flag.greeting" (default set to true)

"protectionstones.flag.farewell" (default set to true)

"protectionstones.flag.notify-enter" (default set to true)

"protectionstones.flag.notify-leave" (default set to true)

"protectionstones.flag.exit" (default set to true)

"protectionstones.flag.exit-group" (default set to true)

"protectionstones.flag.entry" (default set to true)

"protectionstones.flag.entry-group" (default set to true)

"protectionstones.flag.heal-amount" (default set to true)

"protectionstones.flag.heal-delay" (default set to true)

"protectionstones.flag.heal-min-health" (default set to true)

"protectionstones.flag.heal-max-health" (default set to true)

"protectionstones.flag.feed-delay" (default set to true)

"protectionstones.flag.feed-amount" (default set to true)

"protectionstones.flag.feed-min-hunger" (default set to true)

"protectionstones.flag.feed-max-hunger" (default set to true)

"protectionstones.flag.snow-fall" (default set to true)

"protectionstones.flag.snow-melt" (default set to true)

"protectionstones.flag.ice-form" (default set to true)

"protectionstones.flag.ice-melt" (default set to true)

"protectionstones.flag.mushroom-growth" (default set to true)

"protectionstones.flag.leaf-decay" (default set to true)

"protectionstones.flag.grass-growth" (default set to true)

"protectionstones.flag.fire-spread" (default set to true)

"protectionstones.flag.lava-fire" (default set to true)

"protectionstones.flag.lava-flow" (default set to true)

"protectionstones.flag.water-flow" (default set to true)

"protectionstones.flag.teleport" (default set to true)

"protectionstones.flag.teleport-group" (default set to true)

"protectionstones.flag.spawn" (default set to true)

"protectionstones.flag.spawn-group" (default set to true)

"protectionstones.flag.blocked-cmds" (default set to true)

"protectionstones.flag.allowed-cmds" (default set to true)

"protectionstones.flag.price" (default set to true)

"protectionstones.flag.buyable" (default set to true)</br>
Visit WorldGuard for the complete list of WorldGuard Region Flags and more information.
WG Permission to Modify Other Regions

If you have this permission you can modify other players WorldGuard Regions.

worldguard.region.bypass.<world>

Or: worldguard.region.bypass.* for all worlds.
Default Permissions

PS was created with the most common permission defaults preset. To make PS easy to configure or to use it without a permissions plugin. All the PS Permissions are listed above on this page with their defaults of either, true (allowed), false (denied), or op (operator allowed).

To change these defaults you would either need to allow a false or op permission in your permissions plugin by adding that permission to the players group or the player directly for unique situations.

But for permissions that are set as true (allowed) many people may find it easier or the only way to deny a player would be to alter PS's defaults directly in the plugin.

To do this to any permission in PS do the following:

Open the protectionstones.jar with an archive program like 7zip, then edit the plugin.yml file inside the jar.

Find the permission section you want to change like the one controlling all flags commands...

protectionstones.flags:
  description: Allows Use of Flags Commands
  default: true

And change the "default: true" to "default: false"

Don't forget to reload your plugins so it will take effect.

As an additional note, if you go this route you will need to do this each time you update PS to a new version.
</details>


Gradle setup based on the [CFW](https://github.com/CuukyOfficial/CFW)/[VaroPlugin](https://github.com/CuukyOfficial/VaroPlugin) by Cuuky