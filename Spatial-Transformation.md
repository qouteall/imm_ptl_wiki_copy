A portal stitches the existent space with a transformed space. It can have translation transformation, rotating transformation, scale transformation, and mirror transformation. Normal nether portals only have translation transformation. Here introduce the other transformations.

This mod's teleportation is eye-based. It means that the teleportation applies the transformation to the player's eye position. This makes the teleportation visually seamless. However, this doesn't guarantee that the player will be in empty space after teleporting.

## Rotation Transformation

![](https://i.ibb.co/LRGr8pK/2020-08-06-12-18-32.png)

### Create a Portal with Rotation Transformation

Using [datapack custom portal generation](https://github.com/qouteall/ImmersivePortalsMod/wiki/Datapack-Based-Custom-Portal-Generation), there is a form `imm_ptl:flipping_floor_square`.

Using commands. Command `/portal set_portal_rotation <axisX> <axisY> <axisZ> <angleDegrees>` can set a portal's rotation transformation. The rotating axis is a vector (axisX, axisY, axisZ). Command `/portal rotate_portal_rotation <axisX> <axisY> <axisZ> <angleDegrees>` will apply a new rotation transformation to the portal's existing rotation transformation.

### Teleportation

After crossing a portal with rotation transformation, the player's camera may be tilted. Then the camera rotation will smoothly turn into a valid state.

## Scale Transformation