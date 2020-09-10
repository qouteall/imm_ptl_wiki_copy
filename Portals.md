
## Nether Portals
A nether portal can have a non-rectangular shape and can be horizontal.

The max portal area is 400.

After installing this mod, all existing nether portals will not change.

When you use flint and steel to light an obsidian frame, it will load chunks on the other side and then search for an existing obsidian frame with identical shape. If it finds one, it will link with that existing obsidian frame. Otherwise, a new obsidian frame will be generated. The searching range can be configured. The obsidian frame filled with vanilla portal block cannot be linked. It will not link to a vanilla nether portal.

If the obsidian frame is broken, then the nether portal will break.

**NOTE**: Two vanilla nether portals with different size or direction can be linked together. But Immersive Portals requires the obsidian frames to have the same shape and direction to link.

## End Portals
After installing this mod, existing end portals will not be changed.

All end portals will point to (0 120 0) in the end dimension. When a player jumps into an end portal, the player will get slow falling effect for 6 seconds except when wearing elytra.

![](https://i.ibb.co/C08FFJn/2020-05-26-21-55-16.png)

## Mirrors
Use flint and steel to right-click on a glass wall creates a mirror. Currently, mirrors can only be in a rectangular shape. Mirrors can be horizontal. Mirrors can be created on a stained glass wall or glass pane wall. Mirror breaks when the glass wall is broken.

![](https://i.ibb.co/Jr0fdfv/2020-05-26-21-58-45.png)

## Global Portals
Global portals cannot be created in normal survival. They can only be created or removed by commands.

### World Wrapping Portal

There are two types of world wrapping, inward and outward.

The inward world wrapping wraps a finite space and "repeat" it "infinitely". When you cross the right side then you appear on the left side. It is an invisible boundary.

![](https://i.ibb.co/Bnt0Gqc/2020-05-26-22-04-06.png)

![](https://i.ibb.co/jrXPhqV/2020-05-26-22-03-59.png)

Use command `/portal global create_inward_wrapping <x1> <z1> <x2> <z2>` to create an inward wrapping zone.

The outward world wrapping isolates an area out of space. When you want to go into it from left, you will appear on the right.

![](https://i.ibb.co/9g72926/2020-05-26-22-04-50.png)

![](https://i.ibb.co/1RL3wr4/2020-05-26-22-05-05.png)

Use command `/portal global create_outward_wrapping <x1> <z1> <x2> <z2>` to create an outward wrapping zone.

To remove a wrapping zone, using `/portal global remove_wrapping_zone` can remove the wrapping zone that you are in.
If you want to remove an outward wrapping zone that you cannot enter, you can use `/portal global view_wrapping_zones` and know the wrapping zone's id, then you can use `/portal global remove_wrapping_zone <id>`.


After setting up the wrapping portals, you may see z-fighting or missing block faces on the edge.
Use command `/portal global clear_wrapping_border` to clear all blocks in the outer border.
(**NOTE** This operation cannot be undone. You should backup the world before trying this.)

### Vertical Dimension Connecting Portal
The vertical dimension connecting portals connects two dimensions vertically.

Example:
`/portal global connect_floor minecraft:the_end minecraft:overworld`
With this, you will return to the overworld when dropping into the void in end.

![](https://i.ibb.co/kgKw9KG/2019-10-24-22-54-05.png)

This connection is one-way. If you want to make it bi-way, use
`/portal global connect_ceil minecraft:overworld minecraft:the_end`
Then you can see the end above overworld.
Use `/portal global connection_remove_floor <dimension>` `/portal global connection_remove_ceil <dimension>` to remove a connecting portal.

#### Using Vertical Connection to Break Height Limit
By connecting a dimension above the overworld, you increase the overworld's height limit from 256 to 512.

The connection portal does not really connect them. It's just an illusion. 
Cross-portal collision is not perfect but it works in simple cases.
Cross-portal entity rendering has problems.
Redstone or fluid cannot work across the portal.
Entity AI does not work cross-portal.

#### Vertical World Wrapping
For example
`/portal global connect_floor immersive_portals:alternate4 immersive_portals:alternate4`

`/portal global connect_ceil immersive_portals:alternate4 immersive_portals:alternate4`

