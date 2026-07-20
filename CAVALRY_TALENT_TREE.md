# Cavalry Talent Tree

## Design Goal

The Cavalry class tree is the mobility and pursuit foundation.

It is not the Knight tree.

Knights use heavy mounted forces for shock and prestige. Cavalry uses mounted forces to control distance, roads, pursuit, interception, and escape.

Shared class identity:

- Ranged Cavalry
- Light Cavalry
- Heavy Cavalry

Target structure:

- Class point pool: `31`
- Shared class tree: roughly `55-70` possible ranks
- Specialization point pool: roughly `60`
- Each specialization tree: roughly `120-180` possible ranks
- Each major lane has roughly `16-24` possible ranks

Core rule:

`Cavalry decides where the fight happens and whether anyone escapes.`

Visible stats may include:

- March Speed
- Attack
- Defense
- Charge Damage
- Pursuit Damage
- Ranged Cavalry Attack
- Permanent Casualties
- Scout/Screen Speed

Hidden/internal values may include:

- Interception window
- Disengagement confidence
- Pursuit conversion
- Route control
- Harassment fatigue
- Flank exposure

## Shared Class Tree Lanes

| Lane | Identity | Primary Value |
| --- | --- | --- |
| Light Cavalry | Screening and interception | Road control, flank pressure, quick response |
| Ranged Cavalry | Harassment and kiting | Fatigue, cohesion pressure, distance control |
| Heavy Cavalry | Mobile commitment | Pursuit, decisive catches, late impact |

## Light Cavalry Lane

Sub-branches:

- `Road Control`
- `Screening`
- `Survival`

### Road Control

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Light Cavalry Speed | `3/3` | Light Cavalry March Speed `+1%` per rank | Route control |
| Open Ground Riding | `2/2` | Mounted March Speed `+1%` on open terrain per rank | Terrain handling |
| Screen The Road | `1/1` | Better chance to intercept armies using nearby roads | Interception window |
| Rapid Redeploy | `2/2` | Light Cavalry reposition speed `+1%` per rank | Battle-front shift |
| Flank Finder | `2/2` | Light Cavalry Attack `+1%` against exposed support per rank | Exposure detection |

### Screening

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Scout Riders | `2/2` | Enemy reinforcements are detected earlier near your cavalry | Lead time |
| Cavalry Screen | `2/2` | Allied siege and ranged formations take `-1%` damage from flanks per rank | Screen coverage |
| Counter Screen | `2/2` | Enemy cavalry pursuit damage `-1%` near your Light Cavalry per rank | Pursuit denial |
| Relay Riders | `2/2` | Allied march speed `+1%` along screened roads | Signal confidence |
| Road Wardens | `1/1` | Your cavalry improves warning over controlled roads | Route state |

### Survival

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Loose Formation | `2/2` | Light Cavalry takes `-1%` ranged damage per rank while moving | Skirmish spacing |
| Remount Lines | `2/2` | Mounted fatigue `-1%` per rank | Fatigue curve |
| Break Contact | `2/2` | Light Cavalry permanent casualties `-1%` while disengaging per rank | Disengagement confidence |
| Scout The Exit | `2/2` | Cavalry withdraws better from scouted terrain | Exit path quality |

## Ranged Cavalry Lane

Sub-branches:

- `Mounted Archery`
- `Harassment`
- `Kiting`

### Mounted Archery

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Ranged Cavalry Attack | `3/3` | Ranged Cavalry Attack `+1%` per rank | Harassment pressure |
| Mounted Archery | `2/2` | Ranged Cavalry Accuracy `+1%` per rank while moving | Moving-shot handling |
| Loose Reins | `2/2` | Ranged Cavalry takes `-1%` ranged damage while skirmishing per rank | Skirmish spacing |
| Saddle Quivers | `2/2` | Ranged Cavalry harassment lasts longer | Ammunition/fatigue curve |

### Harassment

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Harassing Circle | `1/1` | Unlocks harassment tactic against slow formations | Cohesion pressure |
| Draw Them Out | `2/2` | Enemies chasing your cavalry suffer more fatigue | Bait state |
| Constant Pressure | `2/2` | Ranged Cavalry Attack `+1%` against tired formations per rank | Fatigue exploitation |
| Pick At The Line | `2/2` | Enemy infantry takes `+1%` ranged damage while advancing slowly | Slow-target pressure |
| Death By Distance | `1/1` | Ranged Cavalry becomes stronger the longer it avoids direct contact | Sustained harassment event |

### Kiting

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Feigned Retreat | `2/2` | Enemy formations are more likely to overextend chasing your cavalry | Discipline bait |
| Keep Distance | `2/2` | Ranged Cavalry takes `-1%` melee damage when disengaging per rank | Contact avoidance |
| Circle Back | `2/2` | Ranged Cavalry returns to harassment faster after disengaging | Reset window |
| Dust And Arrows | `2/2` | Enemy scout reports are less accurate during cavalry harassment | Visibility disruption |

## Heavy Cavalry Lane

Sub-branches:

- `Mobile Impact`
- `Pursuit`
- `Capture`

### Mobile Impact

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Heavy Cavalry Health | `3/3` | Heavy Cavalry Health `+1%` per rank | Stability |
| Heavy Cavalry Attack | `3/3` | Heavy Cavalry Attack `+1%` per rank | Commitment pressure |
| Timed Impact | `2/2` | Heavy Cavalry Charge Damage `+1%` when attacking exposed formations | Timing window |
| Flank Charge | `2/2` | Heavy Cavalry Attack `+1%` from flank or rear | Flank exposure |
| Hammer From Afar | `1/1` | Heavy Cavalry hits harder after long maneuver rather than direct frontal commit | Operational timing |

### Pursuit

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Pursuit Damage | `3/3` | Pursuit Damage `+1%` per rank | Rout conversion |
| Cut Off Retreat | `1/1` | Unlocks stronger pursuit tactic against routed formations | Escape denial |
| No Escape | `2/2` | Routed enemies suffer `+1%` permanent casualties per rank | Capture/death split |
| Run Them Down | `2/2` | Heavy Cavalry Attack `+1%` during pursuit | Pursuit pressure |
| The Chase Decides | `1/1` | Cavalry gains decisive pursuit bonuses after enemy morale collapse | Collapse conversion |

### Capture

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Encircle The Broken | `2/2` | Routed enemies are more likely to be captured | Capture weighting |
| Spare The Valuable | `2/2` | Captured enemy formations yield better ransom value | Ransom classification |
| Broken Banners | `2/2` | Enemy formations fleeing from your cavalry recover slower after battle | Shame memory |
| Herd The Routed | `2/2` | Pursuit creates fewer accidental permanent losses but more captures | Capture/death conversion |

## Class Tree Capstones

| Capstone | Lane | Player-Facing Effect | Hidden/Internal |
| --- | --- | --- | --- |
| Road Wardens | Light Cavalry | Your cavalry improves warning over controlled roads | Route state |
| Death By Distance | Ranged Cavalry | Ranged Cavalry grows stronger while avoiding direct contact | Sustained harassment event |
| The Chase Decides | Heavy Cavalry | Cavalry gains decisive pursuit bonuses after enemy morale collapse | Collapse conversion |

## Specialization Tree Scale

| Specialization | Possible Ranks | Spendable Points | Build Routes | Design Goal |
| --- | ---: | ---: | ---: | --- |
| Mobility | `120-180` | `60` | `4-5` | Many ways to control roads, timing, and interception |
| Harassment | `120-180` | `60` | `4-5` | Many ways to exhaust and disrupt enemies without direct contact |
| Pursuit | `120-180` | `60` | `4-5` | Many ways to convert enemy failure into losses, captures, or routs |

## Balance Rules

- Cavalry controls space, not walls.
- Cavalry should fear prepared pikes and bad terrain.
- Ranged Cavalry should require distance and protection.
- Pursuit should be strongest after enemy collapse, not before.
- Cavalry should punish poor scouting and exposed support.
