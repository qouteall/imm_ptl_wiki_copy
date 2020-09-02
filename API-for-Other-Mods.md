### Mod Structure
This mod (Fabric version)'s mod id is `immersive_portals`. It has 3 mods jar-in-jar.
* Immersive Portals Core (modid:`imm_ptl_core`)
* Cloth Config
* Mod Menu

The Immersive Portals Core contains the core portal functionality:
* Recursive portal rendering (Rendering context management, transformation management, OpenGL state management)
* Client multi-world loading and ticking
* Remote chunk loading
* Remote chunk/entity networking synchronization
* Dimension transition without loading screen and multidimensional player position mutual synchronization
* Global portal management
* Cross portal block interaction
* Datapack-based custom portal generation (and general breakable portal)
* Integration with OptiFine, Sodium (my fork), Pehkui, (Requiem)
The Core registers portal entity types and portal placeholder block.
The Core (hopefully) does not change existing vanilla behavior.

The mod Immersive Portals has:
* Enhanced nether portals
* Enhanced end portal
* Alternate dimensions
* Dimension Stack

Cloth Config and Mod Menu are used for providing the config GUI.

### Configure Dependency
#### If you want to use Immersive Portals Core and have it as a jar-in-jar

Add this into `repositories`
```
	maven { url 'https://jitpack.io' }
```
Add this into `dependencies`

```
	modImplementation  'com.github.qouteall.ImmersivePortalsMod:imm_ptl_core:1.16-SNAPSHOT'
        include 'com.github.qouteall.ImmersivePortalsMod:imm_ptl_core:1.16-SNAPSHOT'
```
See https://jitpack.io/#qouteall/ImmersivePortalsMod
(You can change `1.16-SNAPSHOT` to a release tag. If Jitpack doesn't work, try to fork this repo and use your own repo)

#### If you want to have an optional dependency of Immersive Portals (some functionality only enables with IP installed)
```
	modCompileOnly 'com.github.qouteall.ImmersivePortalsMod:imm_ptl_core:1.16-SNAPSHOT'
```



#### Use CurseMaven for Dependency (If Jitpack really doesn't work)

**Note for Gradle 6 users: CurseMaven doesn't support Gradle 6**

Use [CurseMaven](https://github.com/Wyn-Price/CurseMaven) to automatically get the mod from [CurseForge](https://www.curseforge.com/minecraft/mc-mods/immersive-portals-mod).

1. In your `plugins` block at the top of build.gradle add this at the end:

   ```
   	id "com.wynprice.cursemaven" version "2.1.1"
   ```

   This will add CurseMaven as a plugin and allow you to use curse.maven in your dependencies.

2. Go to the [files tab on CurseForge](https://www.curseforge.com/minecraft/mc-mods/immersive-portals-mod/files) and pick the version you want. Click the purple download button. Look in your address bar and you will see something like:

   `https://www.curseforge.com/minecraft/mc-mods/immersive-portals-mod/files/2936532`

   The long number at the end is the version you want. In this case it's `2936532`. You can close the tab now because you don't need to download the file to your computer, CurseMaven will do it for you. But remember to copy the number and put it somewhere.

3. In your `dependencies` block in build.gradle put:

   ```
   	modImplementation "curse.maven:immersive-portals-mod:2936532"
   ```

   `curse.maven` tells it to use the CurseMaven plugin, `immersive-portals-mod` is the mod id on Curse, and `2936532` is the file id. You can use `modCompileOnly` for optional dependency.

4. Rerun gradle sync from your IDE and you should be able to access `Portal` class from `com.qouteall.immersive_portals.portal`. Or any other class in this mod.


