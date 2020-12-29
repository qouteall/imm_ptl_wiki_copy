
This mod provides 5 alternate dimensions. Their sky is similar to the overworld.
You can use them to connect with the overworld.
|Dimension id|Description|
|-|-|
|immersive_portals:alternate1| Skyland with overworld biome distribution|
|immersive_portals:alternate2| Same as alternate1|
|immersive_portals:alternate3| Full of crazy world generation errors|
|immersive_portals:alternate4| Same as alternate3|
|immersive_portals:alternate5| Void|

Alternte dimensions can be disabled.

## How to Access Alternate Dimensions
In normal survival there are two ways to access alternate dimensions.
1. [Use dimension stack](https://github.com/qouteall/ImmersivePortalsMod/wiki/Dimension-Stack)
2. [Configure a special portal generation](https://github.com/qouteall/ImmersivePortalsMod/wiki/Datapack-Based-Custom-Portal-Generation)

If you have command access then you can directly create a portal to alternate dimensions or use `/portal tpme` command

## Details of Alternate3/4 Dimension
Alternate4 dimension is very chaotic. For every 4x4 chunks region in this dimension, the world generation follows a randomly generated math expression. The terrain exists from y=0 to y=128.

![](https://i.ibb.co/LzGZMqJ/2020-05-06-22-08-07.png)
![](https://i.ibb.co/sP8rJT7/2020-05-06-22-06-22.png)
![](https://i.ibb.co/Z8rmJjj/2020-05-06-22-10-02.png)

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