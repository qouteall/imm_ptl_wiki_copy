These are the attributes that a portal has.

You can edit them by `/portal set_portal_nbt` command.
[Portal Customization](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portal-Customization)

### Body Attributes

#### Orientation Axis
Two unit vectors that are perpendicular to each other. These two vectors define the orientation of the portal.

NBT tags:`axisWX` `axisWY` `axisWZ` `axisHX` `axisHY` `axisHZ`

#### Width, Height
Width is the portal shape's length along the direction of `axisW`. Height is the portal shape's length along the direction of `axisH`.

NBT tags: `width` `height`

#### The Special Shape
Optional. Consists of various 2d triangles.

NBT tag: `specialShape` (It's a number list. Every 2 numbers represent a 2d point(x axis is axisW and y axis is axisH). Every 3 points represent a triangle)

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
If true, the player will be moved up if the player is inside the ground after teleportation.

NBT tag: `adjustPositionAfterTeleport`

#### Whether to Have Cross Portal Collision

If an entity touches a portal, its collision will be specially handled, which includes:
* The outer collision. Things behind the portal cannot collide with that entity.
* The inner collision. Things "inside" the portal can collide with that entity.

This attribute defines whether the inner collision is being handled.

NBT tag: `hasCrossPortalCollision`

#### Commands to Invoke After Teleporting

Optional. You can specify a list of commands to be invoked for entities that teleport through this portal.
The command sender will be the entity that teleported.

The commands will be invoked with level-2 permission.
Using command `/portal set_portal_nbt` command to change this requires level-2 permission.

NBT tag: `commandsOnTeleported`

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

#### Whether to Render Yourself

If false, you cannot see yourself from the portal.

NBT tag: `doRenderPlayer`

#### Cullable Range
For outer frustum culling.

NBT tag: `cullableXStart` `cullableXEnd` `cullableYStart` `cullableYEnd`

### Additional Attributes

#### Motion Affinity
If it's positive, then players colliding with the portal will be accelerated in the portal's facing direction. If it's negative, the player will be decelerated when moving fast.

NBT tag: `motionAffinity`

## Breakable Portal Attributes

Only exists for [breakable portals](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portals#breakable-portals).

#### Unbreakable
If true, the portal won't break if the frame structure is broken.

NBT tag: `unbreakable`

### Overlay Attributes

#### Overlay Block State
Optional. It's the portal overlay block's block state.

NBT tag: `overlayBlockState`

#### Overlay Opacity
Overlay's opacity. Between 0 and 1.

NBT tag: `overlayOpacity`

#### Overlay Offset
The overlay offset along the portal's facing direction.

NBT tag: `overlayOffset`

## Command Examples

* Make a nether portal unbreakable `/portal set_portal_nbt {unbreakable:true}`
* Make a portal that has scaling to not change the crossing entity's scale `/portal set_portal_nbt {teleportChangesScale:false}`
* Make the portal fuse-view `/portal set_portal_nbt {fuseView:true}`
* Adjust the width and height for a square portal: `/portal set_portal_nbt {width:100,height:100,specialShape:[]}`
* Make the portal to damage the entities that cross this portal: `/portal set_portal_nbt {commandsOnTeleported:["/effect give @s minecraft:instant_damage 1"]}`
* Give the portal a diamond block overlay `/portal set_portal_nbt {overlayBlockState:{Name:"minecraft:diamond_block"},overlayOpacity:0.6,overlayOffset:-0.3}`  (Only works for breakable portals such as nether portals, not working for portals created by portal helper)
* Give the portal a triangular shape `/portal set_portal_nbt {width:2,height:2,specialShape:[-1.0d,0.0d,1.0d,0.0d,0d,1.0d],cullableXStart:0,cullableXEnd:0,cullableYStart:0,cullableYEnd:0}`

### About Portal Shape Editing

You can edit the portal shape by editing the NBT tag of `width`, `height`, and `specialShape`.

If the NBT tag `specialShape` is present, the shape will be determined by `specialShape`, otherwise `width` and `height`.

`specialShape` is a number list, every 2 numbers represent a 2D point and every 3 points represent a triangle. After editing the shape, artifacts may appear. Some terrain sections in the portal are not rendered, some terrain sections behind the portal are not rendered. This is due to this mod's frustum culling rendering optimization. To fix the artifact, you need to assure that every triangle in `specialShape` does not exceed the rectangle area defined by `width` and `height`. And the rectangle area defined by `cullableXStart`, `cullableXEnd`, `cullableYStart`, and `cullableYEnd` does not exceed the portal shape.