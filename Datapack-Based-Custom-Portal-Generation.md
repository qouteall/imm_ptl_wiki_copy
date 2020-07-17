(this feature hasn't been released. working in progress)

This feature is 1.16 only.

Configure custom portal generations using json files in a datapack.

[What are datapacks and how to install them](https://minecraft.gamepedia.com/Data_Pack)

## Example

[Download the example datapack](https://github.com/qouteall/ImmersivePortalsMod/raw/1.16/example_custom_portal_gen.zip)

#### The glowstone portal that's activated using a water bucket from overworld to alternate2 dimension
Similar to aether portal.
```
{
  "schema_version": "imm_ptl:v1",
  "from": [
    "minecraft:overworld"
  ],
  "to": "immersive_portals:alternate2",
  "form": {
    "type": "imm_ptl:classical",
    "from_frame_block": "minecraft:glowstone",
    "area_block": "minecraft:air",
    "to_frame_block": "minecraft:glowstone",
    "generate_frame_if_not_found": true
  },
  "trigger": {
    "type": "imm_ptl:use_item",
    "item": "minecraft:water_bucket"
  }
}
```
#### A floor 2x2 flipping portal to alternate1. The frame is dirt and should have flowers on it. The content should be water.
Similar to twilight forest portal.
```
{
  "schema_version": "imm_ptl:v1",
  "from": [
    "minecraft:overworld"
  ],
  "to": "immersive_portals:alternate1",
  "form": {
    "type": "imm_ptl:flipping_floor_square",
    "length": 2,
    "frame_block": "minecraft:bamboo_plantable_on",
    "area_block": "minecraft:water",
    "up_frame_block": "minecraft:small_flowers",
    "bottom_block": "minecraft:bamboo_plantable_on"
  },
  "trigger": {
    "type": "imm_ptl:throw_item",
    "item": "minecraft:diamond"
  },
  "post_invoke_commands": [
    "/summon minecraft:lightning_bolt ~ ~ ~"
  ]
}
```
#### From overworld to alternate4. The overworld side frame is lapis block, but the other side's frame is redstone block
```
{
  "schema_version": "imm_ptl:v1",
  "from": [
    "minecraft:overworld"
  ],
  "to": "immersive_portals:alternate4",
  "space_ratio_from": 1,
  "space_ratio_to": 8,
  "form": {
    "type": "imm_ptl:classical",
    "from_frame_block": "minecraft:lapis_block",
    "area_block": "minecraft:air",
    "to_frame_block": "minecraft:redstone_block",
    "generate_frame_if_not_found": true
  },
  "trigger": {
    "type": "imm_ptl:use_item",
    "item": "minecraft:flint_and_steel"
  }
}
```
#### Similar to portal helper but using diamond block as frame and breakable
```
{
  "schema_version": "imm_ptl:v1",
  "from": [
    "minecraft:overworld",
    "minecraft:the_nether",
    "minecraft:the_end"
  ],
  "to": "imm_ptl:the_same_dimension",
  "reversible": false,
  "form": {
    "type": "imm_ptl:classical",
    "from_frame_block": "minecraft:diamond_block",
    "area_block": "minecraft:air",
    "to_frame_block": "minecraft:diamond_block",
    "generate_frame_if_not_found": false
  },
  "trigger": {
    "type": "imm_ptl:use_item",
    "item": "minecraft:flint_and_steel"
  }
}
```
#### From overworld to alternate5. The frame can be in any type of wood planks
```
{
  "schema_version": "imm_ptl:v1",
  "from": [
    "minecraft:overworld"
  ],
  "to": "immersive_portals:alternate5",
  "form": {
    "type": "imm_ptl:heterogeneous",
    "frame_block": "minecraft:planks",
    "area_block": "minecraft:air",
    "generate_frame_if_not_found": true
  },
  "trigger": {
    "type": "imm_ptl:use_item",
    "item": "minecraft:compass"
  }
}
```
#### A new type of nether portal. Throw an netherite into a 3x3 lava pool surrounded by soul soil blocks. Can only be created in overworld
```
{
  "schema_version": "imm_ptl:v1",
  "from": [
    "minecraft:overworld"
  ],
  "to": "minecraft:the_nether",
  "reversible": false,
  "form": {
    "type": "imm_ptl:flipping_floor_square",
    "length": 3,
    "frame_block": "minecraft:soul_soil",
    "area_block": "minecraft:lava"
  },
  "trigger": {
    "type": "imm_ptl:throw_item",
    "item": "minecraft:netherite_ingot"
  }
}
```

## w

This mod provides commands to customize portals, but it's creative-mode only. This mod also provides a new way of customizing custom type using datapacks.

The datapack-based custom portal generation is intended to be used in survival mode. All the generated portals will break if the frame is broken.
