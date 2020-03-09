
# Nether Portals
A nether portal can have a non-rectangular shape and can be horizontal.

The max portal area is 400.

When you use flint and steel to light an obsidian frame, it will load chunks on the other side and then search for an existing obsidian frame with identical shape. If it finds one, it will link with that existing obsidian frame. Otherwise, a new obsidian frame will be generated. The searching range can be configured.

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

After setting up the border portals, some artifacts may manifest.
Use command `/portal fill_border_with_barrier` to fill the outer border layer with barrier blocks. Then the artifacts will vanish.
(NOTE This operation cannot be undone. You should backup the world before trying this.)

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

# The Portal that Changes Direction

Currently, this mod does not support the portal that changes the player's direction after going through. But I am considering adding this feature.



