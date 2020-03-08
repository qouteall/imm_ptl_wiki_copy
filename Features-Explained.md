This wiki describes Immersive Portals Mod for 1.15.

# Nether Portals
A nether portal can have a non-rectangular shape and can be horizontal.

The max portal area is 400.

When you use flint and steel to light an obsidian frame, it will load chunks on the other side and then search for an existing obsidian frame with identical shape. The searching range can be configured.

If the obsidian frame is broken, then the nether portal will break.

# End Portals
All end portals will point to (0 120 0) in the end dimension. When a player jumps into an end portal, the player will get slow falling effect for 6 seconds except when wearing elytra.

# Mirrors
Use flint and steel to right-click on a glass wall creates a mirror. Currently, mirrors can only be in a rectangular shape. Mirrors can be horizontal. Mirror breaks when the glass wall is broken.

# Global Portals
Global portals cannot be created in normal survival. They can only be created or removed by commands.

## World Wrapping Portal

The world wrapping portal wraps finite space and "repeat" it "infinitely". When you go to the right side then you appear on the left side. It is an invisible boundary.

Use command `/portal border_set <x1> <z1> <x2> <z2>` to set world wrapping portal.

Use command `/portal border_remove` to remove the world wrapping portal.

The world wrapping portal works normally in very large areas.

## Vertical Dimension Connecting Portal
The vertical dimension connecting portals connects two dimensions vertically.

Example:
`/portal connect_floor minecraft:the_end minecraft:overworld`
With this, you will return to the overworld when dropping into the void in end.
This connection is one-way. If you want to make it bi-way, use
`/portal connect_ceil minecraft:overworld minecraft:the_end`
Then you can see the end above overworld.
Use `/portal connection_remove_floor <dimension>` `/portal connection_remove_ceil <dimension>` to remove a connecting portal.

### Using Vertical Connection to Break Height Limit
By connecting a dimension above the overworld, you increase the overworld's height limit from 256 to 512.

The connection portal does not really connect them. It's just an illusion. 
Cross-portal collision is not perfect but it works in simple cases.
Cross-portal entity rendering has problems.
Redstone or fluid cannot work across the portal.

### Vertical World Wrapping
For example
`/portal connect_floor immersive_portals:alternate4 immersive_portals:alternate4`

`/portal connect_ceil immersive_portals:alternate4 immersive_portals:alternate4`

# Alternate Dimensions
This mod provides 5 alternate dimensions. Their sky is similar to the overworld.
You can use them to connect with the overworld.
|Dimension id|Description|
|-|-|
|immersive_portals:alternate1| Mono-biome Skyland. The biome is randomly selected when the server starts|
|immersive_portals:alternate2| Skyland with overworld biome distribution|
|immersive_portals:alternate3| Stretched skyland with chaos biome distribution|
|immersive_portals:alternate4| Full of crazy world generation errors|
|immersive_portals:alternate5| Void|

## Details of alternate4 dimension
Alternate4 dimension is very chaotic. For every 4x4 chunks region in this dimension, the world generation follows a randomly generated math expression. The terrain exists from y=0 to y=128.

Different region types use different ways to turn math expression into terrain.
| Region Type|Trait| Possibility Weight   |
| ----------- | ---------- | ---------- |
| mountain| Stone usually fill in corners|25|
| classicalSolid| Similar to mountain but the shape is closer to skyland|40|
| classicalHollow| The terrain is hollow|50|
| classicalWatery|The terrain has water pockets inside stone|10|
| newSolid|Similar to mountain but the shape is closer to skyland|10|
| floatingSea|Below y=64 is solid, above y=64 is water|30|
| treasured|Random blocks floating|3|
| layeredHollow|Sometimes looks layered, sometimes looks eroded|15|

The biome distribution of alternate4 is also chaos. Every biome has the same distribution proportion including nether biomes and end biomes.

Vanilla structures generate more frequently in alternate4.

There are some "sponge dungeons" in alternate4. Sponge dungeons generate more frequently in lower places.
A sponge dungeon consists of a sponge platform, a spawner and a shulker box containing treasure.
The spawner is usually shielded by obsidian.
The spawner spawns randomly stacked vanilla mobs including oversized slime.
The treasure is unique. You may get a full box of useless items. You may also get some rare things that cannot be acquired in normal survival such as a level 5 protection enchantment book.
This is my attempt of making alternate4 an adventurous dimension.

## Portal Customization
This mod provides a new block called "Portal Helper". Use this block to create two identical frames, light it using flint and steel, then portals will be generated. You cannot generate a cross-dimension portal or a portal that links to far places. To achieve that you need to use commands to edit the portal.

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
Tags for `immersive_portals:portal` `immersive_portals:nether_portal_new` `immersive_portals:end_portal` `immersive_portals:mirror` `immersive_portals:breakable_mirror` `immersive_portals:global_tracked_portal` `immersive_portals:` `immersive_portals:border_portal` `immersive_portals:end_floor_portal`
|Tag|Description|
|-|---|
|width,height|The portal area length along axisW and axisH|
|axisWX,axisWY,axisWZ,axisHX,axisHY,axisHZ|axisW and axisH an unit vectors which define the facing of the portal|
|dimensionTo|Raw id of the destination dimension(0 for overworld, -1 for nether, 1 for end)|
|destinationX,destinationY,destinationZ|Portal destination|
|specialShape|Optional. Every 2 numbers represent a 2d point(x axis is axisW and y axis is AxisH). Every 3 points represent a triangle|
|teleportable|If set to false then you cannot teleport through but can still see through|
|cullableXStart,cullableXEnd,cullableYStart,cullableYEnd|For frustum culling|
|loadFewerChunks|(deprecated)|
|||
|||
|||
|||






