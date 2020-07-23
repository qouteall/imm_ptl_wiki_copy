
### Max Portal Layer
Specifies the maximum portal-in-portal rendering layer.

When rendering infinite mirror room or world wrapping portals, the FPS may go very low because it renders too many portals in portals.

![](https://i.ibb.co/4FFQdtd/Untitled3.png)

Turning down the max portal layer can save your FPS.

![](https://i.ibb.co/MCLrYZt/Untitled4.png)

### Lag Attack Proof
When FPS drops because of rendering too many portals, it will enter "lag attack proof" mode and only render one layer of portals and only render near portals which helps you recover from the lag. If that's enabled then you will not be lag-attacked by a mirror room.

### Actively Load Remote Chunks
The chunks near the player are directly loaded.
The chunks that are only visible through the portal are remote chunks.
If this is turned off, remote chunks will not be ticked.
Redstone and entities will not move in remote chunks.
This can reduce server lag.

(If this is disabled, nether portal linking may not work normally.)

### Load Fewer Chunks
Load fewer chunks from portals. Reduce server lag.

### ~~Customized Portal Generation~~
This feature is replaced by the new [datapack-based custom portal generation system](https://github.com/qouteall/ImmersivePortalsMod/wiki/Datapack-Based-Custom-Portal-Generation) in 1.16.

For example, use `minecraft:overworld,1,immersive_portals:alternate4,8,minecraft:lapis_block`
 then you can use flint and steel to light a portal using lapis block as frame pointing to alternate4 dimension in overworld or reverse.
The space ration is 1:8, one block in overworld corresponds to 8 blocks in alternate4 dimension.

(If you are on Forge, use `\n` to separate different configs.)