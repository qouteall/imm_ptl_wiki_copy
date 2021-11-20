Use [vertical connecting portals](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portals#vertical-dimension-connecting-portal) to "stack" the dimensions.



![image.png](https://i.loli.net/2021/11/20/aui8vcNer9hAmgJ.png)

![image.png](https://i.loli.net/2021/11/20/r7sUyN6Azm4qiaF.png)





You can see the "Dimension Stack" button when creating a new world.

![image.png](https://i.loli.net/2021/11/20/helqg7vkcdML5n3.png)



![image.png](https://i.loli.net/2021/11/20/REKhZgzprG15XqB.png)



### Dimension Stack Options

By clicking "Edit" you can edit the selected dimension entry's options:

#### Scale

This controls the generated portals' scale transformation. The generated connecting portal won't change the crossing entity's scale.

If you want that one block in nether corresponds to 8 blocks in overworld, set the overworld's scale to 8.

![image.png](https://i.loli.net/2021/11/20/ywnkEq6F4pQS7Ha.png)

It's recommended to either **(1)** set the scale between overworld and nether to be 8 or **(2)** set the nether portal mode to be `disabled`. Because dimension stack does not interfere with how nether portals work, if dimension stack allows player to travel between overworld and nether with 1 by 1 space ratio, and nether portal allows travelling with 1 by 8 space ratio, then the player can easily reach the world border by using two travel methods alternately.

#### Flipped

Controls the portals' rotating transformation. If enabled, makes the dimension looks "flipped". Does not change the gravity direction in that dimension. If a flipped dimension connects to a non-flipped dimension, the connecting portal will have a 180 degrees rotation transformation along X axis.

![image.png](https://i.loli.net/2021/11/20/pXxmBnrQd2CbVIE.png)

#### Horizontal Rotation

Controls the portals' rotating transformation. Make the dimension looks rotated along Y axis.

![image.png](https://i.loli.net/2021/11/20/Fnv4GOCW8A3wiJM.png)

---

#### Loop

If enabled, the bottom dimension will connect to the top dimension, creating a vertical world wrapping.



### Common Questions

#### How to enable dimension stack on server?

Firstly create the world on client and then copy the world to the server.

Dimension stack could greatly degrade performance. You can shrink the loading distance and adjust [Performace Configurations](https://github.com/qouteall/ImmersivePortalsMod/wiki/Config-Options) when using dimension stack.

#### How to disable dimension stack after the world has been created

There is the game rule `ipDimensionStack` that controls whether bedrock is replaced by obsidian. If you want to disable the bedrock replacement,  use command`/gamerule ipDimensionStack false` . Existing generated chunks remain the same.

The game rule only controls the bedrock generation. It does not interfere with global portals. To remove the global portals, use `/portal global remove_connection_ceil <dimension>` `/portal global remove_connection_floor <dimension>`. [See also](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portals#vertical-dimension-connecting-portal)

Vice versa for enabling dimension stack after the world has been created.

