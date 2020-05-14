
### Vanilla graphic option
If your FPS is low, turn graphic option from "fancy" to "fast", then it will render fewer sections in portal thus increasing FPS.

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

### Load Fewer Chunks
Load fewer chunks from portals. Reduce server lag.

### Render Dimension Redirect
This option makes it possible to render a dimension using the shader of another dimension.
For example, render end using overworld shader `minecraft:the_end->minecraft:overworld`
![](https://i.ibb.co/c1fWpHx/2020-03-31-15-09-16.png)

Sometimes shader rendering is broken in mod dimensions. Use this option to redirect it to a vanilla dimension, then it will render normally `immersive_portals:alternate4->minecraft:overworld`

If the nether in shaders is too red and too dark, but you want to use shaders for overworld, you can redirect nether rendering to vanilla `minecraft:the_nether->vanilla`
![](https://i.ibb.co/4tFy6w8/2020-03-31-15-07-25.png)

If this option is changed in-game, to apply the changes you need to log out and turn off shader and turn on again.

### Customized Portal Generation
For example, use `miencraft:overworld,1,immersive_portals:alternate4,8,minecraft:lapis_block`
 then you can use flint and steel to light a portal using lapis block as frame pointing to alternate4 dimension in overworld or reverse.
The space ration is 1:8, one block in overworld corresponds to 8 blocks in alternate4 dimension.