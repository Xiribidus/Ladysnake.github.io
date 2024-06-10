---
layout: wiki
title: Rat's Mischief
slug: rats-mischief
curse_project: 431787
modrinth: true
---
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

**Rat's Mischief** is a Quilt mod introducing rats, a new mob that can be tamed and interacted with in various different ways!

***This page is for the 2.0 update of Rat's Mischief, the previous version is documented [here](/wiki/rats-mischief/pre-2.0).***

## Video Showcases

First release:
<div>
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/CVZfsPM8Mm4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

Introduction of the ([now removed](/wiki/rats-mischief/pre-2.0)) elytrats:

<div>
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/QNQkrJz0cnM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

Release of update 2.0:

<div>
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/O5e930bA4yg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
  
## Wiki

### Rats
Rats are small, fast and **tamable** overworld creatures found spawning in groups of up to 5 **around empty villages**.
They can be **fed with any food**, the better the food, the higher the chance of taming them.
Spawned in naturally, they will be of one of the [natural types](#natural-types).

*They do **not** spawn around [Abandoned/Zombie Village structures](https://minecraft.wiki/w/Village#Abandoned_villages), but around [once normal villages](https://minecraft.wiki/w/Village) whose population has disappeared.
Note that for the game to still recognize a village as such it needs to **contain beds**.*

Rats have **4 hearts of health** (8hp) and deal **half a heart of damage** (1hp).
In order to make them survivable, the light critters **do not take fall damage** or damage from **berry bushes and cacti** and, much like their real counterparts, can **hold their breath** for impressive **5 times longer** than the player.

Both wild and tamed rats will **pick up any items** lying around,
**consuming food** items to **regenerate health** when damaged according to the saturation of the food
and **drinking potions** out of pure curiosity and **without regards for negative** or even deadly **outcomes**.

TODO: Clip of rats salvaging items

#### Rats as Companions
Tamed rats behave very similarly to **tamed wolves**, following around their owner and attacking enemies.
They will also pick up and **retrieve any items lying around**. </br>
*This can be toggled with the [ocarina](#ocarina).*

Rats **can be clicked** in order to **make them sit**, stopping them from following you around or moving in general.

In combat, rats deal **comparatively little damage**, which they counter in numbers: Unlike most other entities, rats ignore invulnerability ticks on enemies, meaning **they can attack very quickly** if deployed in large numbers.

TODO: Clip of rats mischief hunting [insert mob]

#### Breeding and Plague Rats
Tamed rats can be bred using any sort of food, producing [pet rat types](#pet-types) as offspring.

If two **rats with the same potion effect** are bred there is a chance their **offspring is a plague rat**.
Plague rats themselves are **immune to any potion effects** and **pass on their associated effect** to any **target they attack**.
If two plague rats are bred their offspring will also be a plague rat of the same type.

TODO: Clip of glowing plague rats attacking entities

#### Mobile Rattapults
Tamed rats can be **picked up** by shift-clicking on them. They then **exist in your inventory** as an item which can be used to **turn them into** [spy rats](#spy-rat) or transport them.

Alternatively, picked up rats **can be thrown** with left-click and subsequently **latch onto entities** they hit, attacking them.
Should they not hit anything they will roam around following you again or come back to you, jumping into your inventory returning to the same slot they were thrown from. </br>
*This behavior can be toggled by right-clicking on individual rats when they are in your inventory.*

TODO: Clip of throwing and returning rats

### Equipment

Rat's Mischief adds a number of equipment items related to rats.
Most of them are accessed via the **Clothed Ingot**, found in [Ancient Cities](https://minecraft.wiki/w/Ancient_City).

TODO: Image of Clothed Ingot in Ancient City Chest

#### Pouches

One of the few exceptions to the requirement of Clothed Ingots are the various **rat pouches**.
These are, as the name suggests, used for **transporting tamed rats** in inventories more easily and in bulk:

In order to **pick up a singular rat**, simply **right-click** on it. It will go into the pouch and be stored there safely.</br>
You can also **shift-right-click** to **pick up all available rats** within a 16 blocks distance.</br>
Do the same **without any rats around** or a **full pouch** to **release the whole mischief** at once!

There are currently **4 tiers** available, with **each increasing** the carrying capacity **by 5, starting at 5**.

TODO video showcase of the rat pouch concept, different rat pouches and their recipe

{% capture summary %}<h5 id="pouch-recipes">Recipes</h2>{% endcapture %}
{% capture content %}

<figure class="recipes">
{% recipe "ratsmischief:leather_rat_pouch" %}
{% recipe "ratsmischief:twisted_rat_pouch" %}
{% recipe "ratsmischief:purpur_rat_pouch" %}
{% recipe "ratsmischief:rat_master_pouch" %}
</figure>

{% endcapture %}
{% include details.liquid summary=summary content=content%}

#### Rat Master Ocarina

The Rat Master Ocarina is the **essential tool to advanced control** of your mischief:
You can **select** one of the **following commands** by **left-clicking** while holding the Ocarina.
By **right-clicking** you can subsequently order your rats to **execute the selected command**.</br>
*The Ocarina can also be right-clicked in your inventory to stop your rats from bringing you random items.*

##### Commands

{% capture summary %}<p id="harvest">Harvest</h2>{% endcapture %}
{% capture content %}

Order your rats to harvest and replant any plants they can get their hands on!
They can of course also bring those crops right back to you.

TODO video showcase of harvest command

{% endcapture %}
{% include details.liquid summary=summary content=content%}

{% capture summary %}<p id="collect">Collect</h2>{% endcapture %}
{% capture content %}

Your rats will try collecting the type of block you are facing while activating the Ocarina.
Note however that they can only mine soft materials and blocks.

TODO video showcase of collect command

{% endcapture %}
{% include details.liquid summary=summary content=content%}

{% capture summary %}<p id="skirmish">Skirmish</h2>{% endcapture %}
{% capture content %}

Skirmish orders your rats to engage any hostile entities in the vicinity:

TODO video showcase of skirmish command

{% endcapture %}
{% include details.liquid summary=summary content=content%}

{% capture summary %}<p id="love">Love</h2>{% endcapture %}
{% capture content %}

Your rats will feed any animal they can in their surrounding given the correct food.
This also allows rats to increase their own numbers very quickly if necessary.

TODO video showcase of love command

{% endcapture %}
{% include details.liquid summary=summary content=content%}

#### Spyrat and Rat Master Mirror
#### Rat Master Armor
#### Rat Master Mask
#### Curse of the Rat Enchantment
#### Pouches

### Special Events

Bday rat
bday mischief
international rat day

### Gallery
#### Natural types
#### Pet types
#### Special types
