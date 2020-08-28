This mod provides a new block called "Portal Helper".
You can build two identical frames using that block and use flint and steel to light one. Then a new two-way two-faced portal will be generated.
![](https://i.ibb.co/FXfD6Fq/2020-06-11-16-58-26.png)

The portal helper cannot generate a cross-dimension portal or a portal that links to far places using the portal helper. To achieve that you need to use commands to edit the portal.

### Command Examples
Make a new (square) portal without having to build a frame: `/portal make_portal 1 1 minecraft:overworld shift 5` (shift 5 means that the destination is 5 blocks ahead of the position of the portal)

Change the portal entity's destination: `/portal set_portal_destination minecraft:the_end 0 70 0`

Move the portal entity forward 0.5 blocks: `/portal move_portal 0.5`

Delete a portal entity: `/portal delete_portal`

Make two-way or two-faced portal become one-way and one-faced: `/portal remove_connected_portals` (**It's recommended to use this before changing portal position, destination or rotation**)

Turn a one-way portal to two-way portal: `/portal complete_bi_way_portal`

Turn a one-way portal to two-way two-faced portal: `/portal complete_bi_way_bi_faced_portal`

Make a portal entity have a rotating transformation, rotate the world "inside" the portal: `/portal set_portal_rotation 0 1 0 45` (0 1 0 means the Y-axis. It means rotating around the Y-axis for 45 degrees)

Rotate the portal entity itself (does not rotate the world "inside" the portal): `/portal rotate_portal_body 1 0 0 30` (rotates around X-axis for 30 degrees)

Change the shape of the portal entity: `/portal set_portal_nbt {specialShape:[0d,0d,0d,1d,1d,0d]}`

Make the portal entity not able to teleport. Turn it into a video surveillance: `/portal set_portal_nbt {teleportable:0b}`

Make a nether portal entity unbreakable: `/portal set_portal_nbt {unbreakable:1b}`

### Portal Entities
Global portals don't exist as entities in the world, they are global. All other portals, including nether portals, end portals, mirrors, exist as entities in the world.

A portal entity is one-way and one-faced. A normal nether portal consists of 2 portal entities in the overworld and 2 portal entities in the nether. The end portal is one-way and one-faced. An end portal only consists of one portal entity.

Normally if you want to edit a portal, it's recommended to firstly use `/portal remove_connected_portals` then the four portal entities become one portal entity. Then this portal is one way now, you can edit its destination, rotation without messing up. Then you can make this portal two-way and two-faced by `/portal complete_bi_way_bi_faced_portal`. If you edit the portal before using `/portal remove_connected_portals`, the portal entities on the other side and the other face won't be edited.

### Portal-targeted Commands
For the portal-targeted commands, if the command invoker is a player, it targets on the portal that the player is looking at. If the command invoker is a portal entity, it will apply to itself.
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
|`/portal set_portal_rotation <axisX> <axisY> <axisZ> <angleDegrees>`|Set the portal's rotation transformation.<br>The rotation transformation is defined by a rotating axis vector and the angle in degrees.<br>When the axis is pointing on you positive angle corresponds rotating counterclockwise|
|`/portal set_portal_rotation_along <axis> <angleDegrees>`|Similar to the above but use `x` `y` `z` to represent the axis vector|
|`/portal rotate_portal_body <axisX> <axisY> <axisZ> <angleDegrees>`|Rotate the portal.<br>This command does not change the portal's rotating transformation|
|`/portal rotate_portal_body_along <axis> <angleDegrees>`|...|
|`/portal rotate_portal_rotation  <axisX> <axisY> <axisZ> <angleDegrees>`|Change the portal's rotation transformation by applying an additional rotation to the original rotation|
|`/portal rotate_portal_rotation_along <axis> <angleDegrees>`|...|
|`/portal move_portal <distance>`|Move the portal along the direcction that you are looking at|
|`/portal move_portal_destination <distance>`|Move the portal's destination along the direction that you are looking at|
|`/portal set_portal_specific_accessor <player>`|Make the portal entity only accessible by one player|
|`/portal set_portal_specific_accessor `|Make the portal entity accessible to all players|
|`/portal multidest <player> <dimension> <x> <y> <z> <isBiFaced> <isBiWay>`|Set the portal destination for only one player (see below)|
|`/portal multidest <player>`|Remove the player-specific portal from the portal clutter (see below)|
|`/portal set_portal_scale <scale>`|Set the portal's scale transformation.|
|`/portal eradicate_portal_clutter`|Completely remove a bi-way portal (4 portal entities). Equivalent to `/portal remove_connected_portals` and then `/portal delete_portal`|

NOTE: Before using command `/portal set_portal_rotation`, `/portal move_portal` or `/portal set_portal_rotation` you should use `/portal remove_connected_portals` first or there will be unwanted portals remain.

Portal-targeted commands don't work with global portals.

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
|rotationA,rotationB,<br>rotationC,rotationD|A quaternion that defines the portal's rotating transformation. Optional|
|motionAffinity|If it's positive, then players colliding with portal will be accelerated in the portal's facing direction. If it's negative, the player will be decellerated when moving fast|
|specificPlayerId|The UUID of the specific player that can access this portal. Optional|
|scale|The scale transformation|
|teleportChangesScale|Whether the teleportation changes entity scale if the portal has a scale transformation|

Tags for `immersive_portals:nether_portal_new`
|Tag|Description|
|-|-|
|unbreakable|If set to true then the portal entity will remain if obsidian frame breaks|
|netherPortalShape|Nether portal shape data for determining whether the portal frame brakes|
|reversePortalId|The UUID of the reverse portal|

Tags for `immersive_portals:breakable_mirror`
|Tag|Description|
|-|-|
|unbreakable|If set to true then the mirror will remain if the glass wall is destroied|
|boxXL,boxYL,boxZL,<br>boxXH,boxYH,boxZH|Glass wall area|

After editing the portal shape you should also change width,height,cullableXStart,cullableXEnd,cullableYStart,cullableYEnd.
If you don't change these accordingly some sections may not be rendered due to advanced frustum culling.

### Commands for Command Blocks
`/portal cb_make_portal <width> <height> <fromEntity> <toEntity>` creates a portal entity goes from fromEntity to toEntity. The orientation is determined by fromEntity's orientation.

These commands are deprecated.
`/portal cb_set_portal_destination <portal> <dimension> <x> <y> <z>` `/portal cb_complete_bi_way_portal <portal>` `/portal cb_complete_bi_faced_portal <portal>` `/portal cb_complete_bi_way_bi_faced_portal <portal>` `/portal cb_remove_connected_portals <portal>` `/portal cb_set_portal_specific_accessor <portal> [player]` 

### Creating the Portal that Points to Different Destinations for Different Players
By using `/portal set_portal_specific_accessor` command you can make a portal only accessible for one player. By putting two different portal entities that are specific for two different players into the same place, you can create a portal that points to different destinations for different players.

But if two portals overlap then the portal targeted commands cannot select the portal entity accurately. You can manage that using `/portal multidest` command. Managing it using command blocks is also possible.

(Portal targeted commands can still be used on the portal that's invisible to you)

### Common Questions

#### How to connect two portals?
It's not recommended to "connect" two existing portals. The recommended way is to make one portal entity, control its position and destination, then complete bi way portal. Use `/portal remove_connected_portals` first, then edit the portal, then `/portal complete_bi_way_portal`.

### Helper Commands for Creating Portals

#### Straightly Create a Portal
You can aim at a block and use `/portal make_portal <width> <height> <dim> <toX> <toY> <toZ>` or `/portal make_portal <width> <height> <dim> shift <dist>`.

The first one creates a new portal coming off of the side of the block you're pointing at. The specified height is always pointing away from the surface and the width is always the other way, and the portal will point towards you. The dim and x,y,z arguments act just like set_portal_destination.

The second one does the same with creation but sets the destination (in the specified dimension) to be <dist> blocks in front of the portal. This is useful if you don't have coordinates in mind immediately. And once you're able to shift around the portal destination, it could be a useful visual tool.

The two variants are:
- `/portal make_portal <width> <height> <dim> <toX> <toY> <toZ>`
- `/portal make_portal <width> <height> <dim> shift <dist>`

#### Create a Small Wrapping Zone
You can create a small wrapping zone by `/portal create_small_inward_wrapping <x1> <y1> <z1> <x2> <y2> <z2>` `/portal create_small_outward_wrapping <x1> <y1> <z1> <x2> <y2> <z2>`
These commands create normal portals instead of global portals. These wrapping portals can be modified by portal-targeted commands. Global portal commands do not affect them.

#### Create a Scaled Wrapping Zone
You can create a scaled wrapping by `/portal create_scaled_box_view <x1> <y1> <z1> <x2> <y2> <z2> <scale> <placeTargetEntity> <isBiWay>`.
The wrapping zone is a box area. It will create 6 portals with scale transformation that points from the box around placeTargetEntity to the wrapping zone box. The generated portal won't change the entity scale upon teleportation. If you want to make a small box view of a big area, the scale should be bigger than 1. If isBiWay is true, it will generate the reverse portals for every portal. Then it will totally generate 12 portals totally.

The command invoker dimension is the dimension of the view box. For example, if you want to create a box viewing the end island, use `/execute in minecraft:the_end run portal create_scaled_box_view -100 0 -100 100 128 100 20 @p true`

![](https://i.ibb.co/yhXHYHm/2020-08-26-21-18-54.png)