These are the attributes that a portal has.

### Shape Attributes

#### Orientation Axis
Two unit vectors that are perpendicular to each other. These two vectors define the orientation of the portal.

NBT tags:`axisWX` `axisWY` `axisWZ` `axisHX` `axisHY` `axisHZ`

#### Width, Height
Width is the portal shape's length along the direction of `axisW`. Height is the portal shape's length along the direction of `axisH`.

NBT tags: `width` `height`

#### The Special Shape
Optional. Consists of various 2d triangles.

NBT tag: `specialShape` (It's a number list. Every 2 numbers represent a 2d point(x axis is axisW and y axis is AxisH). Every 3 points represent a triangle)

### Transformation Attributes

#### Destination Dimension
The dimension id of the portal's destination dimension.

NBT tag: `dimensionTo`

#### Destination
The destination position.

NBT tag: `destinationX` `destinationY` `destinationZ`

#### Rotation Transformation
Optional. A quaternion that defines the portal's rotation transformation.

NBT tag: `rotationA` `rotationB` `rotationC` `rotationD`

#### Scale Transformation
A number that defines the portal's scale transformation.

NBT tag: `scale`

### Teleportation Attributes

#### Whether Teleportation Changes Scale
Whether the teleportation changes entity scale if the portal has a scale transformation.

NBT tag: `teleportChangesScale`

#### Whether to Adjust The Entity's Position After Teleporting
If true, the player will be moved up if the player is inside the ground after teleportation

NBT tag: `adjustPositionAfterTeleport`

### Accessibility Attributes

#### Teleportable
If set to false then you cannot teleport through but can still see through.

NBT tag: `teleportable`

#### Interactable
Whether the player can place or break blocks through the portal.

NBT tag: `interactable`

#### Specific Accessor
Optional. The UUID of the specific player that can access this portal. If it's present but the value is null, the portal cannot be accessed by any player but can be accessed by non-player entities.

NBT tag: `specificPlayerId`

### Rendering Attributes

#### Fuse View
If true, the portal rendering will not render the sky background and maintain the depth value in the portal view area. This results in the things inside the portal and the things outside the portal being fused together.

![](https://i.ibb.co/NCfsyrp/2020-12-19-14-06-20.png)

NBT tag: `fuseView`

#### Rendering Mergable
If true, when the portal touches another portal that has the same spacial transformation, these portals will be "grouped" and the rendering performance will be improved which result in higher FPS. But the front clipping functionality does not work normally when rendering the grouped portal.

NBT tag: `renderingMergable`

#### Cullable Range
For outer frustum culling.

NBT tag: `cullableXStart` `cullableXEnd` `cullableYStart` `cullableYEnd`

### Additional Attributes

#### Motion Affinity
If it's positive, then players colliding with the portal will be accelerated in the portal's facing direction. If it's negative, the player will be decelerated when moving fast.

NBT tag: `motionAffinity`

### Breakable Portal Attributes

Only exists for [breakable portals](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portals#breakable-portals).

#### unbreakable
If true, the portal won't break if the frame structure is broken.

NBT tag: `unbreakable`
