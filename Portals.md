
## Nether Portals
After installing this mod, all existing nether portals will not change.

A nether portal can have a non-rectangular shape and can be horizontal.



When you use flint and steel to light an obsidian frame, it will load chunks on the other side and then search for an existing obsidian frame that it can link to. If it finds one, it will link with that existing obsidian frame. Otherwise, a new obsidian frame will be generated.

It will not link to a vanilla nether portal.

In the `normal` mode it can only link to the obsidian shape with the exact shape and orientation. In `adaptive` mode it can link to the scaled and rotated obsidian frame.

The maximum nether portal side length is 20.

This mod has 3 nether portal modes: `normal`, `adaptive` and `vanilla`. The nether portal mode controls the new portal generation.

### Mode : `normal`
It can only link to the obsidian frame that has the exact same shape and orientation.

### Mode : `adaptive`
It can link to the obsidian frame that has a compatible shape. This does not require the linked shape to be exactly the same. It can link to the rotated and scaled obsidian frame. And the generated portal will have the corresponding rotation and scale transformations.

### Mode : `vanilla`
Does not change vanilla nether portal functionality.

## End Portals
After installing this mod, existing end portals will not be changed.

This mod has 4 end portal types: `normal`, `toObsidianPlatform`, `scaledView`, `vanilla`.

### Mode : `normal`

The normal type of end portal points to (0 120 0) in the end dimension. When a player jumps into an end portal, the player will get slow falling effect for 6 seconds except when wearing elytra.

![](https://i.ibb.co/C08FFJn/2020-05-26-21-55-16.png)

### Mode : `toObsidianPlatform`

Points to the obsidian platform.

### Mode : `scaledView`

The `scaledView` type end portal shows an overlook of the entire end island. It consists of 6 portals with scale transformation (and another 6 client-only portals on the end dimension).

![](https://i.ibb.co/hmRS3KH/2020-09-15-21-13-34.png)

This type of end portal is laggier.

### Mode : `vanilla`
Does not change vanilla end portal functionality.

## Mirrors
Use flint and steel to right-click on a glass wall creates a mirror. Currently, mirrors can only be in a rectangular shape. Mirrors can be horizontal. Mirrors can be created on a stained glass wall or glass pane wall. Mirror breaks when the glass wall is broken.

![](https://i.ibb.co/Jr0fdfv/2020-05-26-21-58-45.png)

## Global Portals
Global portals can be very big.

### World Wrapping Portal

There are two types of world wrapping, inward and outward.

The inward world wrapping wraps a finite space and "repeat" it "infinitely". When you cross the right side then you appear on the left side. It is an invisible boundary.

![](https://i.ibb.co/Bnt0Gqc/2020-05-26-22-04-06.png)

![](https://i.ibb.co/jrXPhqV/2020-05-26-22-03-59.png)

Use command `/portal global create_inward_wrapping <x1> <z1> <x2> <z2>` to create an inward wrapping zone.

The outward world wrapping isolates an area out of space. When you want to go into it from the left, you will appear on the right.

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

![](https://i.ibb.co/JvDMZtj/2020-10-18-22-15-38.png)

This connection is one-way. If you want to make it bi-way, use
`/portal global connect_ceil minecraft:overworld minecraft:the_end`
Then you can see the end above overworld.
Use `/portal global connection_remove_floor <dimension>` `/portal global connection_remove_ceil <dimension>` to remove a connecting portal.

#### Using Vertical Connection to Break the Height Limit
By connecting a dimension above the overworld, you increase the overworld's height limit from 256 to 512. It does not really increase the height limit. It just uses portals to "connect" the dimensions. It won't be as perfect as cubic chunks. (Redstone, fluid, lighting, and entity AI does not work through portals)

#### Vertical World Wrapping
For example
`/portal global connect_floor immersive_portals:alternate4 immersive_portals:alternate4`

`/portal global connect_ceil immersive_portals:alternate4 immersive_portals:alternate4`

