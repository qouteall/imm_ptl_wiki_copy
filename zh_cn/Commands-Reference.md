(即将翻译)

A list of all commands of Immersive Portals mod.

## Global Portal Commands
The global portal commands require OP permission.

#### `/portal global convert_global_portal_to_normal_portal`
Can only be used by a player. Converts the global portal instance that you are pointing to into a normal portal. Requires the player to be near the portal center.

#### `/portal global convert_normal_portal_to_global_portal`
Can only be used by a player. Converts the normal portal entity that you are pointing to into a global portal.

#### `/portal global create_inward_wrapping <x1> <z1> <x2> <z2>`
Create an inward wrapping zone. The created portals are global portals. The two XZ coordinates define the wrapping area. The generated portals go from y level 0 to y level 256.

#### `/portal global create_outward_wrapping <x1> <z1> <x2> <z2>`
Similar to the above but creates an outward wrapping zone.

#### `/portal global remove_wrapping_zone`
Remove the global portal wrapping zone that you are in. This does not work for the wrapping zone constituted by normal portals.

#### `/portal global view_wrapping_zones`
View the wrapping zones in the current dimension and know their ids.

#### `/portal global remove_wrapping_zone <id>`
Remove a global portal wrapping zone by its id.

#### `/portal global connect_floor <dimensionA> <dimensionB>`
Creates a portal that connects `dimensionA` 's floor with `dimensionB` 's top. It only generates one one-way global portal instance.

#### `/portal global connect_ceil <dimensionA> <dimensionB>`
Creates a portal that connects `dimensionA` 's ceiling with `dimensionB` 's bottom. It only generates one one-way global portal instance.

#### `/portal global connection_remove_floor <dimension>`
Remove the floor connection portal in that dimension. This command only removes one portal instance.

#### `/portal global connection_remove_ceil <dimension>`
Remove the floor connection portal in that dimension. This command only removes one portal instance.


## Portal Targeted Commands
Not only the ones with OP permission, but any creative mode players can also use the portal targeted commands.

The portal targeted commands all targets to one portal entity. If the command sender is a player, it targets the portal that the player is looking at. If the command sender is a portal entity, the command will target that portal entity.

These commands don't work with global portals.

### Change the Portal's Destination

#### `/portal set_portal_destination <dimenision> <x> <y> <z>`
Change a portal entity's destination to a specific dimension and a specific position.

#### `/portal set_portal_destination_to <entity>`
Set the portal destination to an entity's position.

#### `/portal move_portal_destination <distance>`
Move the portal's destination along the direction that you are looking at.

### Manage the Portal

#### `/portal set_portal_nbt <nbt>`
Set a portal's NBT data. [Portal NBT Data Format](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portal-Attributes)

#### `/portal view_portal_data`
View a portal's NBT data.

#### `/portal delete_portal`
Remove a portal.

#### `/portal move_portal <distance>`
Move the portal along the direction that you are looking at.

### Portal Clutter Management

[See](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portal-Customization#1-nether-portal--4-portal-entities)

#### `/portal complete_bi_way_portal`
Create a new portal entity to make the portal bi-way. Removes duplicated portals.

#### `/portal complete_bi_faced_portal`
Create a new portal entity to make the portal bi-faced. Removes duplicated portals.

#### `/portal complete_bi_way_bi_faced_portal`
Create new portal entities to make the portal bi-way and bi-faced. Removes duplicated portals.

#### `/portal remove_connected_portals`
Remove portal entities to make the portal one-way and one-faced.

#### `/portal eradicate_portal_clutter`
Completely remove a bi-way portal (4 portal entities). Equivalent to `/portal remove_connected_portals` and then `/portal delete_portal`

### Rotation

#### `/portal set_portal_rotation <axisX> <axisY> <axisZ> <angleDegrees>`
Set the portal's rotation transformation.
The rotation transformation is defined by a rotating axis vector and the angle in degrees.
When the axis is pointing on you, a positive angle corresponds to rotating counterclockwise.

#### `/portal set_portal_rotation_along <axis> <angleDegrees>`
Similar to the above but use `x`, `y` or `z` to represent the axis vector

#### `/portal rotate_portal_body <axisX> <axisY> <axisZ> <angleDegrees>`
Rotate the portal. This command does not change the portal's rotating transformation.

#### `/portal rotate_portal_body_along <axis> <angleDegrees>`
Similar to the above.

#### `/portal rotate_portal_rotation <axisX> <axisY> <axisZ> <angleDegrees>`
Change the portal's rotation transformation by applying an additional rotation to the original rotation.

#### `/portal rotate_portal_rotation_along <axis> <angleDegrees>`
Similar to the above.

### Scale

#### `/portal set_portal_scale <scale>`
Set the portal's scale transformation.

### Player-specific Property

#### `/portal set_portal_specific_accessor <player>`
Make the portal entity only accessible by one player.

#### `/portal set_portal_specific_accessor`
Make the portal entity accessible to all players.

#### `/portal multidest <player> <dimension> <x> <y> <z> <isBiFaced> <isBiWay>`
Set the portal destination for only one player.

#### `/portal multidest <player>`
Remove the player-specific portal from the portal clutter.

### Other

#### `/portal set_portal_custom_name <name>`
Set a portal's custom name.

#### `/portal make_portal_round`
Make the portal shape to be round.

## Direct Portal Creation Commands
Can be used by OPs and creative mode players.

#### `/portal make_portal <width> <height> <dim> <toX> <toY> <toZ>`
Create a new portal coming off of the side of the block you're pointing at. The specified height is always pointing away from the surface and the width is always the other way, and the portal will point towards you.

#### `/portal make_portal <width> <height> <dim> shift <distance>`
Create a portal whiches destination is `distance` blocks in front of the portal.

#### `/portal create_small_inward_wrapping <x1> <y1> <z1> <x2> <y2> <z2>`
Create a small inward wrapping zone. The generated portals are normal portals.

#### `/portal create_small_outward_wrapping <x1> <y1> <z1> <x2> <y2> <z2>`
Similar to the above but the wrapping zone is outward.

#### `/portal create_scaled_box_view <x1> <y1> <z1> <x2> <y2> <z2> <scale> <placeTargetEntity> <isBiWay> [teleportChangesScale]`
Create a scaled box wrapping zone. It will create 6 portals with scale transformation that points from the box around `placeTargetEntity` to the wrapping zone box. If you want to make a small box view of a big area, the scale should be bigger than 1. If `isBiWay` is true, it will generate the reverse portals for every portal. `teleportChangesScale` determines whether the generated portal changes the teleporting entity's scale.

The command sender dimension is the dimension of the view box. For example, if you want to create a box viewing the end island, use `/execute in minecraft:the_end run portal create_scaled_box_view -100 0 -100 100 128 100 20 @p true`

![](https://i.ibb.co/yhXHYHm/2020-08-26-21-18-54.png)

## Miscellaneous Commands

#### `/portal cb_make_portal <width> <height> <fromEntity> <toEntity>`
Create a portal entity that goes from `fromEntity` to `toEntity`. The orientation is determined by `fromEntity` 's orientation.

#### `/portal tpme <dimension> <x> <y> <z>`
Teleport you across dimensions without any loading screen. Can only be invoked by players.

#### `/portal tp <entity> <dimension> <x> <y> <z>`
Teleport entities across dimensions.

#### `/portal goback`
Sometimes you went into a one-way portal and want to come back, but you forgot the coordinate where you come in. Use this command to come back.

## Deprecated Commands
These commands are deprecated. They will be removed in 1.17.

`/portal cb_set_portal_destination <portal> <dimension> <x> <y> <z>` `/portal cb_complete_bi_way_portal <portal>` `/portal cb_complete_bi_faced_portal <portal>` `/portal cb_complete_bi_way_bi_faced_portal <portal>` `/portal cb_remove_connected_portals <portal>` `/portal cb_set_portal_specific_accessor <portal> [player]` 
