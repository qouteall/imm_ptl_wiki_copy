(即将翻译)

## Portal Helper Block

This mod provides a new block called "Portal Helper".
You can build two frames using that block and use flint and steel to light one. Then a new two-way two-faced portal will be generated. The portal's rotation and scale transformation will adapt to the shape difference.

![](https://i.ibb.co/wRzvJB9/2020-12-14-22-28-18.png)

![](https://i.ibb.co/pP0znwJ/2020-12-14-22-28-39.png)

If no linkable frame is found, it will generate a new frame nearby.

Unlike nether portals, the generated portal won't break when the frame breaks. To remove the portal, you need to use the command `/portal delete_portal` or `/portal eradicate_portal_clutter` (See below).

After generating the portal a block of the portal helper frame will be removed so that other portal helper frames won't link to it.

The portal helper cannot generate a cross-dimension portal or a portal that links to far places using the portal helper. To achieve that you need to use commands to edit the portal.

## Manage Portals Using Commands

[Description of All Commands](https://github.com/qouteall/ImmersivePortalsMod/wiki/Commands-Reference)

### 1 Nether Portal = 4 Portal Entities
Before going further there is a very **IMPORTANT** concept to figure out.

**Every portal entity is one-faced and one-way. A normal nether portal is bi-faced and bi-way, it consists of 2 portal entities in the overworld and 2 portal entities in the nether, 4 portal entities in total.** The two portal entities in the overworld have the same origin position and destination, but these two portal entities are facing opposite directions.

The concept of "portal entity" is different from "portal". But sometimes to express directly "portal entity" is referred to as "portal". Sometimes the 4 portal entities that constitute a portal are called "portal clutter". A single one-way one-faced global portal is sometimes called a "global portal instance".

Command `/portal delete_portal` will only remove one portal entity.

Using the command `/portal remove_connected_portals` to a portal will make the portal one-way and one-faced.
If it's used for a bi-way bi-faced portal, in the 4 portal entities the portal entity that is facing you will remain and the other 3 portal entities will be removed.

Command `/portal complete_bi_way_portal` will create the "reverse" version of the portal entity thus make the portal bi-way. The command `/portal complete_bi_faced_portal` completes the portal to be bi-faced, and the command `/portal complete_bi_way_bi_faced_portal` completes the portal to be bi-way bi-faced.

Command `/portal eradicate_portal_clutter` removes the whole portal. If used to a bi-way bi-faced portal, all 4 portal entities will be removed.

If you want to edit a bi-way bi-faced portal, 4 portal entities need to be edited. It's recommended to firstly use `/portal remove_connected_portals` to make only one portal entity remain. Then you can move the portal or change its space transformation without leaving unwanted portal entities. Then you can make this portal two-way and two-faced by `/portal complete_bi_way_bi_faced_portal`. If you edit the portal before using `/portal remove_connected_portals`, the portal entities on the other side and the other face won't be edited.

### Portal-Targeted Commands

There are some portal-targeted commands for managing portals. You need to point to a portal when using these commands.

**The portal-targeted commands all target only one portal entity that you are pointing to.**


#### Examples

- Change the portal entity's destination: `/portal set_portal_destination minecraft:the_end 0 70 0`

- Delete a portal entity: `/portal delete_portal`

- Make a portal entity have a rotating transformation, rotate the world "inside" the portal: `/portal set_portal_rotation 0 1 0 45` (0 1 0 means the Y-axis. It means rotating around the Y-axis for 45 degrees). It's equivalent to `/portal set_portal_rotation_along y 45`

- Rotate the portal entity itself (does not rotate the world "inside" the portal): `/portal rotate_portal_body 1 0 0 30` (rotates around X-axis for 30 degrees). Equivalent to `/portal rotate_portal_body_along x 30`

- Change the portal entity's scale transformation: `/portal set_portal_scale 5`

- Move the portal entity forward 0.5 blocks: `/portal move_portal 0.5`

- Make the portal entity not able to teleport. Turn it into a "video surveillance": `/portal set_portal_nbt {teleportable:0b}`

- Make the portal round-shaped `/portal make_portal_round`

[See All Portal-Targeted Commands](https://github.com/qouteall/ImmersivePortalsMod/wiki/Commands-Reference#portal-targeted-commands)

[Portal Attributes](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portal-Attributes)

#### Editing Existing Breakable Portals

"Breakable Portals" refers to nether portals and the custom datapack generated portals. These portals will break when the frame breaks. 

You can use `/portal set_portal_nbt {unbreakable:1b}` to make the portal entity unbreakable. To make the whole portal unbreakable, you need to use that command for 4 portal entities.

This mod periodically checks whether a breakable portal is properly linked. If it's not properly linked, the portal will automatically break.

It's recommended to edit the portals generated by the portal helper. If you want to edit a breakable portal, make sure that the portal is unbreakable.

#### Edit Portals Using Command Blocks and Functions
All portal targeted commands can be used by non-player command executors. If the command sender is a portal entity, the command will target that portal entity. For example `/execute as @e[type=immersive_portals:portal] run portal set_portal_destination minecraft:the_end 0 80 0`

## Directly Create Portals

Directly create a new square portal entity: 
- `/portal make_portal 1 1 minecraft:the_end 0 80 0` Create a portal with width 1 height 1 pointing to the end
- `/portal make_portal 1 1 minecraft:overworld shift 5` Create a portal whiches the destination is 5 blocks ahead of the position of the portal

### Create a Small Wrapping Zone
You can create a small wrapping zone by `/portal create_small_inward_wrapping <x1> <y1> <z1> <x2> <y2> <z2>` `/portal create_small_outward_wrapping <x1> <y1> <z1> <x2> <y2> <z2>`
These commands create normal portals instead of global portals. These wrapping portals can be modified by portal-targeted commands. Global portal commands do not affect them.

### Create a Scaled Wrapping Zone
You can create a scaled wrapping by `/portal create_scaled_box_view <x1> <y1> <z1> <x2> <y2> <z2> <scale> <placeTargetEntity> <isBiWay> [teleportChangesScale]`.
The wrapping zone is a box area. It will create 6 portals with scale transformation that points from the box around placeTargetEntity to the wrapping zone box. The argument teleportChangesScale is false by default. If you want to make a small box view of a big area, the scale should be bigger than 1. If `isBiWay` is true, it will generate the reverse portals for every portal. Then it will generate 12 portals totally.

The command sender's dimension is the dimension of the view box. For example, if you want to create a box viewing the end island, use `/execute in minecraft:the_end run portal create_scaled_box_view -100 0 -100 100 128 100 20 @p true`

![](https://i.ibb.co/yhXHYHm/2020-08-26-21-18-54.png)

## Edit the Portal's Shape
Editing the portal shape by editing its NBT is technical.

[Portal Attributes](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portal-Attributes)

You can edit the portal shape by editing the NBT tag of `width`, `height`, and `specialShape`. `specialShape` is a number list, every 2 numbers represent a 2D point and every 3 points represent a triangle. But after editing the shape, artifacts may appear. Some sections in the portal are not rendered, some sections behind the portal are not rendered. This is due to this mod's frustum culling rendering optimization. To fix the artifact, you need to assure that every triangle in `specialShape` does not exceed the rectangle area defined by `width` and `height`. And the rectangle area defined by `cullableXStart`, `cullableXEnd`, `cullableYStart`, and `cullableYEnd` does not exceed the portal shape.


## Create the Portal that Points to Different Destinations for Different Players
By using `/portal set_portal_specific_accessor` command you can make a portal only accessible for one player. By putting two different portal entities that are specific for two different players into the same place, you can create a portal that points to different destinations for different players.

But if two portals overlap then the portal targeted commands cannot select the portal entity accurately. You can manage that using `/portal multidest` command. Managing it using command blocks is also possible.

(Portal targeted commands can still be used on the portal that's not accessible to you)

## Common Questions

### How to connect two portals?
It's not recommended to "connect" two existing portals. The recommended way is to make one portal entity, control its position and destination, then complete bi way portal. Use `/portal remove_connected_portals` first, then edit the portal, then `/portal complete_bi_way_portal`.

## Other Utility Commands

You can use command `/portal tpme <dimension> <x> <y> <z>` to teleport yourself across dimensions without loading screen. If you accidentally go through a one-way portal and want to come back, you can use `/portal goback`