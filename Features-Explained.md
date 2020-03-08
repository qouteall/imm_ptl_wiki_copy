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
Then you can see end above overworld.
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

immersive_portals:alternate1: Mono-biome Skyland. The biome is randomly selected when the server starts.

immersive_portals:alternate2: Skyland with overworld biome distribution.

immersive_portals:alternate3: Stretched skyland with chaos biome distribution.

immersive_portals:alternate4: Full of crazy world generation errors.

immersive_portals:alternate5: Void.

## Details of alternate4 dimension
Alternate4 dimension is very chaotic. For every 4x4 chunks region in this dimension, the world generation follows a randomly generated math expression. The terrain exists from y=0 to y=128.

Different region types use different ways to turn math expression into terrain.
| Region Type|Trait| Possibility Weight   |
| ----------- | ---------- | ---------|
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

## Portal Editing
