---
layout: wiki
title: BLAST
slug: blast
curse_project: 349938
modrinth: true
---

BLAST is a Minecraft fabric mod adding multiple explosives for use in survival or for messing around in creative.

# Features

BLAST mainly focuses on various types of bombs with some common attributes:

- BLAST bombs **drop all lootable blocks** they destroy

- **Items are not destroyed** by explosions but **can be knocked back** by the blasts

- Bombs make **stacks of 16** and have a **1 second cooldown** outside of creative mode

  

## Bombs

### Basic Bombs
<style>
table {border-radius: 18px; background-color: #8B8B8B}
th, td {color: black}
</style>
<table>
<tr><th></th><th style="width:32%"><img src="blast/item_iron_ingot.png" alt="Iron Ingot" /> Iron Tier</th><th style="width:32%"><img src="blast/item_gold_ingot.png" alt="Gold Ingot" /> Gold Tier</th><th style="width:32%"><img src="blast/item_diamond.png" alt="Diamond" /> Diamond Tier</th></tr>
<tr><th rowspan=2 style="transform:rotate(270deg)">Timer</th><td>
<h4>Bomb</h4>

<p style="color: black; padding:6px">A simple bomb with an explosion power of 1 and a fuse time of 2 seconds.</p>

<p style="color: black; padding:6px">Is defused and drops when coming into contact with water.</p>
</td><td>
<h4>Golden Bomb</h4>

<p style="color: black; padding:6px">Works like the normal bomb, but applies Fortune III to all blown up blocks.</p>

<p style="color: black; padding:6px">Like other gold items, Piglins love this bomb!</p>
</td><td>
<h4>Diamond Bomb</h4>

<p style="color: black; padding:6px">Ignores explosion resistance, and therefore can destroy blocks like obsidian.</p>

<p style="color: black; padding:6px">Exceptions are bedrock, barriers, end portal frames, and other admin-exclusive blocks.</p>
</td></tr>
<tr>
<td><img src="/wiki/blast/recipe_bomb.png" alt="Bomb Recipe" /></td>
<td><img src="/wiki/blast/recipe_gold_bomb.png" alt="Gold Bomb Recipe" /></td>
<td><img src="/wiki/blast/recipe_diamond_bomb.png" alt="Diamond Bomb Recipe" /></td>
</tr>
<tr><th rowspan=2 style="transform:rotate(270deg)">Trigger</th><td>
<h4>Trigger Bomb</h4>

<p style="color: black; padding:6px">A simple bomb with an explosion power of 1 on impact instead of after a certain amount of time.</p>

<p style="color: black; padding:6px">Explodes underwater, but will not destroy any blocks.</p>
</td><td>
<h4>Golden Trigger Bomb</h4>

<p style="color: black; padding:6px">A version of the golden bomb with a trigger instead of a fuse.</p>

<p style="color: black; padding:6px">It also explodes underwater without causing block destruction.</p>
</td><td>
<h4>Diamond Trigger Bomb</h4>

<p style="color: black; padding:6px">A version of the diamond bomb with a trigger instead of a fuse.</p>

<p style="color: black; padding:6px">It also explodes underwater without causing block destruction.</p>
</td></tr>
<tr>
<td><img src="/wiki/blast/recipe_trigger_bomb.png" alt="Recipe" /></td>
<td><img src="/wiki/blast/recipe_gold_trigger_bomb.png" alt="Recipe" /></td>
<td><img src="/wiki/blast/recipe_diamond_trigger_bomb.png" alt="Recipe" /></td>
</tr>
</table>

### Dirt Bombs

Dirt Bombs can be crafted by surrounding normal bombs with 8 Dirt Blocks. Instead of destroying blocks however, they will **create a dirt pile wherever they explode.** As such, they are a great counter to creeper holes!

![Dirt Bomb](blast/showcase_dirt_bomb.png){: .wiki}

### Pearl Bombs

Crafted like normal bombs with an Enderpearl as base material, this bomb has a **silk touch effect on all blocks in the explosion** radius. As a side effect, it will also **randomly teleport entities** that get caught in the explosion.

![Pearl Bomb](blast/showcase_pearl_bomb.png){: .wiki}

### Confetti Bombs

Confetti Bombs come, as most other bombs, in 2 variants: As a trigger bomb and as a timed bomb. Instead of blowing your world up however, Confetti bombs make it prettier: **They will spread confetti particles upon exploding!** Those particles come in multiple different colours and **remain on the ground for 1 minute** after the explosion. Confetti Bombs are crafted shapelessly with 7 Paper, 1 Gunpowder and either 1 String (timed) or 1 Redstone Dust (trigger).

![Confetti Bombs](blast/showcase_confetti.png){: .wiki}

### Slime Bombs

Slime Bombs can be crafted using **1 gunpowder, 1 Slimeball and 1 String/Redstone Dust**. Slime Bombs do **not deal any damage** to entities but have **increased knockback!**

![Slime Bomb](blast/showcase_slime_bomb.png){: .wiki}

### Amethyst Bombs

Crafted like any other bomb with an **Amethyst Block as base material**, the Amethyst Bomb **adds 70 amethyst shards to your explosion**, at the **cost of the normal explosion damage**. These shards will spread in all directions and **deal 8 damage (4 hearts) per shard**.

![Amethyst Bomb](blast/showcase_amethyst_bomb.png){: .wiki}

### Frost Bombs

Being an alternative to Amethyst Bombs, Frost Bombs are crafted by adding **Packed Ice as base material** and **replace the amethyst shards with icicles.** These icicles deal only **0.01 damage** but **apply freezing effects** to their targets, bypassing armor without damaging it.

![Frost Bomb](blast/showcase_frost_bomb.png){: .wiki}

### Naval Mines

Naval Mines are bombs that trigger on impact and **can destroy blocks underwater**. In comparison to standard bombs the naval mine has an explosion power of 4 and **only** exists as a **trigger bomb** variant.

![Naval Mine Recipe](blast/recipe_naval_mine.png){: .wiki}



## Blocks

### Remote Detonator

The Remote Detonator is a technical device with the power to activate adjacent explosives instantaneously when triggered. To trigger it, simply look into its direction and throw an Ender Eye. The Ender Eye will teleport into the Remote Detonator, triggering it, and can be retrieved by placing a hopper beneath it. This also works through walls and on large distances.

![Remote Detonator](blast/remote_detonator.png){: .wiki}

### Gunpowder Block

The Gunpowder Block is a compact way of storing gunpowder. When placed it is **highly sensitive to explosions and fire** and will explode almost instantly when in contact with them. The explosion it creates is fiery and has a power of 4.

![Gunpowder Block](blast/showcase_gunpowder_block.png){: .wiki}

### Stripminer

The Stripminer is **triggered similarly to TNT** and **focuses its explosion power in one direction.** It creates a 3x3+ wide tunnel and usually points the way the player is looking upon placing it down, this, however, is inverted while sneaking.
When the Stripminer is set off by other explosives the direction can get misaligned and the fuse time varies slightly.

![Stripminer](blast/showcase_stripminer.png){: .wiki}

### Cold Digger

The Cold Digger is an upgrade to the Stripminer that keeps the functionality of creating a 3x3 wide tunnel but **replaces additional blocks around it with Dry Ice and, in the case of lava, Basalt.** It is crafted by surrounding the Stripminer with 4 Packed Ice Blocks.

#### Dry Ice

Dry Ice is a kind of ice that **does not melt or create water** upon breaking. It emits particles and can be mined using silk touch.

![Cold Digger](blast/showcase_cold_digger.png){: .wiki}


### Bonesburrier

The Bonesburrier is an explosive specifically developed for the [destruction of Bonesburrow](https://www.youtube.com/watch?v=RJwjw8IHMG4). It knocks around blocks upon exploding and spreads Folly Red Paint around the blast area.

![Bonesburrier](blast/showcase_bonesburrier.png){: .wiki}

#### Folly Red Paint

Folly Red Paint spawns only in the occasion of a Bonesburrier explosion, is similarly sticky to honey blocks and dries into Dried Folly Red Paint.

Both the normal and dried variant can be converted to Fresh Folly Red Paint, which will not dry out at all, using honey bottles either directly on the block or in crafting.

Both the normal and fresh variant can be converted to Dried Folly Red Paint, which is the only non-sticky variant, by heating them up in a furnace.

![Folly Red Paint Crafting](blast/diagram_folly_paint.png){: .wiki}

## Claim / Protection Mod Support

Blast version 1.12 and above has support for Patbox's [Common Protection API](https://github.com/Patbox/common-protection-api).
This means BLAST items and blocks respect claim protections for any mod that implements this common API.
This currently includes but is not limited to:

- [Cadmus](https://github.com/Patbox/get-off-my-lawn-reserved) 
- [Flan's Landclaiming Mod](https://modrinth.com/mod/flan)
- [GOML Reserved](https://modrinth.com/mod/goml-reserved)
- [FTB Chunks](https://github.com/FTBTeam/FTB-Chunks)

`List last updated: 22/10/23`

Here is that feature in action:

<iframe width="560" height="315" src="https://www.youtube.com/embed/6LrdmD8crsg?si=IyAzMyKRtvkXdLEA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

# FAQ
#### Can I include this mod in a modpack?

**Yes**, you can. Go ahead, don't bother asking. Please  however provide credit and a link to both the [GitHub repository](https://github.com/Ladysnake/BLAST) and [Curse Forge](https://www.curseforge.com/minecraft/mc-mods/blast) or [Modrinth](https://modrinth.com/mod/blast) project page.

#### Can you port to Forge please? Backport to version X?

Sorry, we **don't** port our mods to forge or backport them for various reasons.



# Gallery

![Mining Tunnel](blast/gallery_mine.png){: .wiki}

![Naval Mines](blast/gallery_naval_mine.png){: .wiki}

![Confetti Rain](blast/gallery_confetti_rain.png){: .wiki}

