### Dynamically Adding and Removing Dimensions

The latest version of this mod has the functionality of dynamically adding and removing dimensions when the game is running.

**This feature is still experimental.**

Example: command `/dims clone_dimension minecraft:overworld "aaa:bbb"` dynamically adds new dimension `aaa:bbb` that has the same world generation as the overworld. Command `/dims remove_dimension aaa:bbb` can remove it.

[See Also](https://github.com/qouteall/ImmersivePortalsMod/wiki/Commands-Reference#dimension-management-commands)

### Alternate Dimensions

This mod provides 5 alternate dimensions for dimension stack:

|Name|Dimension id|Description|
|-|-|-|
|Skyland1|immersive_portals:alternate1| Skyland with overworld biome distribution|
|Skyland2|immersive_portals:alternate2| Same as alternate1, but with a different seed |
|Chaos1|immersive_portals:alternate3| Full of crazy world generation errors|
|Chaos2|immersive_portals:alternate4| Same as alternate3|
|Void|immersive_portals:alternate5| Void|

Alternate dimensions can be disabled via config.
