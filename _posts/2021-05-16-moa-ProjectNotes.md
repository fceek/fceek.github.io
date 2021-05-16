---
layout: post
title: "Master of Arms - Project notes"
---

# Project Notes

> For speed looking up things while writing the doc.

<!-- @import "[TOC]" {cmd="toc" depthFrom=2 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [In Planning Document](#in-planning-document)
  - [Enemies](#enemies)
  - [Bosses](#bosses)
  - [NPC](#npc)
  - [Mechanics](#mechanics)
    - [Player Control](#player-control)
    - [RougeLite](#rougelite)
    - [Elements](#elements)
    - [Shop / 'Choose one' Room](#shop-choose-one-room)
  - [Weapons](#weapons)
    - [Attributes](#attributes)
    - [Components / Accessories](#components-accessories)
- [From the Tutorials](#from-the-tutorials)
  - [Gun Stats](#gun-stats)
  - [Numerical Setup](#numerical-setup)
    - [Combat](#combat)
    - [Progression](#progression)
      - [Levelling up and Exp curve](#levelling-up-and-exp-curve)
      - [Class / Play style](#class-play-style)
    - [Economy](#economy)
- [In Group Discussion](#in-group-discussion)
  - [Style-based perk system](#style-based-perk-system)
- [Random thoughts along the way](#random-thoughts-along-the-way)

<!-- /code_chunk_output -->

---

## In Planning Document

### Enemies

Random spawning, variants

### Bosses

Red light hinted weak spot
Respective Elemental

- **Fire** Ninja Swordsman
  - Robotic
  - Melee
  - Fast
  - High DPS
  - Low HP
- **Earth** Gunslinger
  - Stony Cowboy / Ancient Mech
  - Flint Lock Pistol / Sandstorm limiting player sight
  - Slow
  - High DPH but Low Fire rate -> Low DPS
  - Normal HP (?)
- **Ice** Shaman
  - Robotic Monk
  - Close Combat / Healing totem, destroyed on weak spot hit

### NPC

- Shopkeeper
- Trial Master as tutorial guy and storyteller

### Mechanics

#### Player Control

- Doom style permanent run
- Jump
- Blink to dodge
- Aim and shoot

#### RougeLite

- Levelling up give only perk points
- Perk points give permanent buffs and can re-spec
- Can choose to keep / bring one gun after every run
- Limited gun storage in hub

#### Elements

Have damage multiplier between non-physical elements

- **Fire** Ignites nearby enemies
- **Ice** Slows enemies
- **Earth** Splash damage
- **Physical** Chance to do crits

#### Shop / 'Choose one' Room

Select only one from the guns or restore HP

### Weapons

#### Attributes

- Primary
  - Damage
  - Fire rate
  - Accuracy
  - Handling
  - Magazine size
  - Reload time
- Secondary
  - Crit specs
  - Elemental specs
  - Fire mode
  - Other

#### Components / Accessories

- Body
  - Type and Rarity -> All base specs
  - Available attachments
- Grip / Element
  - Elemental specs
- Barrel
  - Range -> Damage Curve
- Magazine
  - Size
  - Reload time
- Sight *optional*
  - Aim sight
- Stock *optional*
  - Handling
- Muzzle *optional*
  - Accuracy
- Other Attachment *optional*
  - Special effects

Exotic guns are based on this model but not restricted to it

---

## From the Tutorials

### Gun Stats

- Damage
  - Damage-Distance Curve
    - Constant
    - Linear Decrease
    - Segment
  - Hit Point Damage Multiplier
  - DOT / Debuff
  
- Bullet
  - Per shot
    - Burst Fire / Shotgun
  - Fire rate / Fire interval
  - Ammo
  - Reload Time
    - One by One / Mag
  - Reload Finish Time
  - Mode Switching
  - Bullet Speed
  - Bullet Drop
  - Bullet Type

- Feel
  - Recoil
    - Reset Speed
    - Distribution
    - Stand / Crouch / Prone
  - Crosshair
    - Min / Max Spread
    - Reset Speed
    - Stand / Crouch / Prone
  - Sight
    - Aim Speed
    - Scope Multiplier
  - Breath Shaking
  - Switching Guns
  - Affect Movement Speed

- Accessories

- Cost
  - Resource
  - Possibility

### Numerical Setup

#### Combat

- Battle
- Class
- Ability
- Level

Combat experience is built around a certain model

- **Subtraction Model**
  - marginal effect
  - Upper and Lower bound
  - 'Armour break' point
- **Multiplication Model**
  - Accumulation of stats
  - stable payback from stat increase
  - no 'Armour break' point

#### Progression

##### Levelling up and Exp curve

Max level -> Time need to max level -> Approx. segment time -> Curve fitting

$ Time\_for\_Level = K \times Level^3 + B $

-> Pace of Battle -> Figure out factors influencing levelling up speed
-> Nail down game experience upon the curve

##### Class / Play style

Tags by different aspects, endgame builds -> mix and combine

#### Economy

---

## In Group Discussion

### Style-based perk system

Each style has some levels, when maxed out gain a special perk

- Sentry
  - Armour
  - Assault Rifle and LMG Efficiency
  - **Restore Armour after Kill**

- Rouge
  - Movement Speed
  - Charge of Blinks
  - Shotgun and SMG Efficiency
  - **Blink and Jump share charges with a larger count, kill reduces CD**

- Gunslinger
  - All mighty Efficiency
  - *Especially* Pistol and Sniper Efficiency
  - **Gain the ability of slow motion, kill reduce CD**

---

## Random thoughts along the way

- Exp Curve need to be flat
  - Referring to *Hades*

- A pistol *Last Wish* with magazine size of 1 (aways +50% damage with the perk)
- A gun *I can't stop* take it out it'll keep firing