
### Vanilla graphic option
If your FPS is low, turn graphic option from "fancy" to "fast", then it will render fewer sections in portal thus increasing FPS.

### Max Portal Layer
Specifies the maximum portal-in-portal rendering layer.

When rendering infinite mirror room or world wrapping portals, the FPS may go very low because it renders too many portals in portals.

![](https://i.ibb.co/4FFQdtd/Untitled3.png)

Turning down the max portal layer can save your FPS.

![](https://i.ibb.co/MCLrYZt/Untitled4.png)

### Active Load Remote Chunks
The chunks near the player are directly loaded.
The chunks that are only visible through the portal are remote chunks.
If this is turned off, remote chunks will not be ticked.
Redstone and entities will not move in remote chunks.
This can reduce server lag.

### Load Fewer Chunks
Load fewer chunks from portals. Reduce server lag.

### Render Dimension Redirect
This option make it possible to render a dimension using the shader of another dimension.
For example, render end using overworld shader `minecraft:the_end->minecraft:overworld`
![](https://i.ibb.co/c1fWpHx/2020-03-31-15-09-16.png)

Sometimes shader rendering is broken in mod dimensions. Use this option to redirect it to a vanilla dimension, then it will render normally `immersive_portals:alternate4->minecraft:overworld`

If the nether in shaders is too red and too dark, but you want to use shaders for overworld, you can redirect nether rendering to vanilla `minecraft:the_nether->vanilla`
![](https://i.ibb.co/4tFy6w8/2020-03-31-15-07-25.png)
