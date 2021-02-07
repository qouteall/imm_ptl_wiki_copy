
You can see the "Dimension Stack" button when creating a new world.

![](https://qouteall-1.oss-accelerate-overseas.aliyuncs.com/2020-09-20-21-03-15.png)

![](https://qouteall-1.oss-accelerate-overseas.aliyuncs.com/2020-11-29-10-49-54.png)

If the dimension stack is enabled, the bedrock blocks in the world will be replaced by obsidian.
And it will generate vertical connecting portals to connect the dimensions.

![](https://qouteall-1.oss-accelerate-overseas.aliyuncs.com/2020-10-18-21-55-30.png)

If you want to use dimension stack in a server, you need to first create the dimension stack world on the client and then copy the world to the server.

Dimension stack can greatly degrade performance. You can shrink the loading distance and adjust [Performace Configurations](https://github.com/qouteall/ImmersivePortalsMod/wiki/Config-Options) when using dimension stack.

### Dimension Stack Options
#### Respect Space Ratio
This option is disabled by default. If disabled, the scale between overworld and nether is the same. If enabled, the connection portal between overworld and the nether will have scale transformation.
![](https://qouteall-1.oss-accelerate-overseas.aliyuncs.com/2020-11-29-10-57-12.png)

The space ratio is determined by the dimension type.

Note that dimension stack does not interfere with how nether portals work. With the non-respect-space-ratio dimension stack, the player can travel between overworld and nether with 1 by 1 space ratio but nether portal linking respects the 1 by 8 space ratio. Player could dig down into nether, create nether portal, go to overworld, then dig down to nether, travelling in exponential rate and easily reach the world border.

#### Loop
Connects the bottom dimension with the top dimension, creating a vertical world wrapping.

### How to disable dimension stack after the world has been created
Disable the ipDimensionStack gamerule so that the bedrock won't be generated as obsidian (but existing generated chunks remain the same).
`/gamerule ipDimensionStack false`

Then use `/portal global remove_connection_ceil <dimension>` `/portal global remove_connection_floor <dimension>` to remove the vertical connecting portals. [See](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portals#vertical-dimension-connecting-portal)

Vice versa for enabling dimension stack after the world has been created.

The `ipDimensionStack` game rule only controls the bedrock generation. It does not interfere with global portals.