
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