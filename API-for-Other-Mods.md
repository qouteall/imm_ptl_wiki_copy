
### Creating a Portal Entity

Check [this](https://github.com/qouteall/ImmersivePortalsMod/wiki/Portal-Customization) to have an idea about how this mod's portal is stored and organized.

You can create a [Portal](https://github.com/qouteall/ImmersivePortalsMod/blob/1.15/src/main/java/com/qouteall/immersive_portals/portal/Portal.java)
entity, initialize its data and then add it into the world.
`axisW` and `axisH` should be perpendicular. These two vectors defines the facing of the portal.

If `specialShape` is null then the portal is rectangular. [GeometryPortalShape](https://github.com/qouteall/ImmersivePortalsMod/blob/1.15/src/main/java/com/qouteall/immersive_portals/portal/GeometryPortalShape.java) is a set of 2D triangles. This 2D coordinate's x axis is `axisW`, y axis is `axisH`.

If you created one portal entity, you can add a new portal to complete the bi-way portal or bi-faced portal.[PortalManipulation](https://github.com/qouteall/ImmersivePortalsMod/blob/1.15/src/main/java/com/qouteall/immersive_portals/portal/PortalManipulation.java)

You can also create breakable portals using [BlockPortalShape](https://github.com/qouteall/ImmersivePortalsMod/blob/1.15/src/main/java/com/qouteall/immersive_portals/portal/nether_portal/BlockPortalShape.java) by `NetherPortalGeneration#generateBreakablePortalEntities`. It's needed to create a new subclass of BreakablePortalEntity. Check [NetherPortalEntity](https://github.com/qouteall/ImmersivePortalsMod/blob/1.15/src/main/java/com/qouteall/immersive_portals/portal/nether_portal/NetherPortalEntity.java). Breakable portal has placeholder blocks to fill the portal area. If the placeholder block updates, nearby breakable portals will be notified to check portal integrity.