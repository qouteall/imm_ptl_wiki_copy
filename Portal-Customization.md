This mod provides a new block called "Portal Helper". Use this block to create two identical frames, light it using flint and steel, a two-way portal (4 portal entities) will be generated. You cannot generate a cross-dimension portal or a portal that links to far places. To achieve that you need to use commands to edit the portal.

### Portal Entities
Global portals don't exist as entities in the world, they are global. All other portals, including nether portals, end portals, mirrors, exist as entities in the world.

A portal entity is one-way and one-faced. A normal nether portal consists of 2 portal entities in the overworld and 2 portal entities in the nether. The end portal is one-way and one-faced. An end portal only consists of one portal entity.

### Portal-targeted Commands
These commands can only be invoked by a player. When invoking these commands you should point to a portal entity.
|Command|Functionality|
|-|-|
|`/portal set_portal_nbt <nbt>`|Set a porta's nbt data|
|`/portal set_portal_destination <dimenision> <x> <y> <z>`|Change a portal's destination|
|`/portal set_portal_custom_name <name>`|Set a portal's custom name|
|`/portal view_portal_data`|View a portal's nbt data|
|`/portal delete_portal`|Remove a portal|
|`/portal complete_bi_way_portal`|Create a new portal entity to make the portal two-way|
|`/portal complete_bi_faced_portal`|Create a new portal entity to make the portal two-faced|
|`/portal complete_bi_way_bi_faced_portal`|Create new portal entities to make the portal two-way and two-faced|
|`/portal remove_connected_portals`|Remove portal entities to make the portal one-way and one-faced|

### Portal Nbt Tags
Tags for `immersive_portals:portal` `immersive_portals:nether_portal_new` `immersive_portals:end_portal` `immersive_portals:mirror` `immersive_portals:breakable_mirror` `immersive_portals:global_tracked_portal`  `immersive_portals:border_portal` `immersive_portals:end_floor_portal`
|Tag|Description|
|-|-|
|width,height|The portal area length along axisW and axisH|
|axisWX,axisWY,axisWZ,<br>axisHX,axisHY,axisHZ|axisW and axisH an unit vectors which define the facing of the portal|
|dimensionTo|Raw id of the destination dimension(0 for overworld, -1 for nether, 1 for end)|
|destinationX,<br>destinationY,<br>destinationZ|Portal destination|
|specialShape|Optional. Every 2 numbers represent a 2d point(x axis is axisW and y axis is AxisH). Every 3 points represent a triangle|
|teleportable|If set to false then you cannot teleport through but can still see through|
|cullableXStart,cullableXEnd,<br>cullableYStart,cullableYEnd|For frustum culling|
|loadFewerChunks|(deprecated)|

Tags for `immersive_portals:nether_portal_new`
|Tag|Description|
|-|-|
|unbreakable|If set to true then the portal entity will remain if obsidian frame breaks|
|netherPortalShape|Nether portal shape data for determining whether the portal frame brakes|
|reversePortalId|The UUID of the reverse portal|

Tags for `immersive_portals:breakable_mirror`
|Tag|Description|
|-|-|
|boxXL,boxYL,boxZL,<br>boxXH,boxYH,boxZH|Glass wall area|

### Examples
Make a nether portal entity unbreakable: `/portal set_portal_nbt {unbreakable:1b}`

Change the portal's destination: `/portal set_portal_destination minecraft:the_end 0 70 0`

(NOTE This command cannot be invoked by command blocks. If you want to change a portal's destination using command blocks, you can create some portals with different destinations and use command block to teleport these portals)

Make the portal not able to teleport. Turn it into a video surveillance: `/portal set_portal_nbt {teleportable:0b}`

Change the shape of the portal: `/portal set_portal_nbt {specialShape:[0d,0d,0d,1d,1d,0d]}`

(NOTE After changing shape you should also change width,height,cullableXStart,cullableXEnd,cullableYStart,cullableYEnd.
If you don't change these accordingly some sections may not be rendered due to advanced frustum culling)

Move a portal: `/portal set_portal_custom_name "whatever"` `/tp @e[name="whatever"] @p`

Delete a portal: `/portal delete_portal`

Turn a one-way portal to two-way portal: `/portal complete_bi_way_portal`

Turn a one-way portal to two-way two-faced portal: `/portal complete_bi_way_bi_faced_portal`

Make two-way or two-faced portal become one-way and one-faced: `/portal remove_connected_portals`
