
You can see the "Dimension Stack" button when creating a new world.

![](https://i.ibb.co/LPNBZ0v/2020-09-20-21-03-15.png)

![](https://i.ibb.co/QC5L77B/2020-09-20-21-03-21.png)

If the dimension stack is enabled, the bedrock blocks in the world will be replaced by obsidian.
And it will generate vertical connecting portals to connect the dimensions.

![](https://cdn.discordapp.com/attachments/671895772265971712/688997283836067881/stack.png)

If you want to use dimension stack in a server, you need to first create the dimension stack world on the client and then copy the world to the server.

Dimension stack can greatly degrade performance. You can shrink the loading distance when using dimension stack.

### How to disable dimension stack after the world has been created
Disable the ipDimensionStack gamerule so that the bedrock won't be generated as obsidian (but existing generated chunks remain the same).
`/gamerule ipDimensionStack false`

Then use `/portal global remove_connection_ceil <dimension>` `/portal global remove_connection_floor <dimension>` to remove the vertical connecting portals. [See](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portals#vertical-dimension-connecting-portal)

Vice versa for enabling dimension stack after the world has been created.