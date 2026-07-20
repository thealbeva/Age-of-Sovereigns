# Man-At-Arms Talent Tree

## Design Goal

The Man-At-Arms class tree is the professional soldier foundation.

It should make players better at disciplined line warfare without making every Man-At-Arms identical.

Shared class identity:

- Heavy Infantry
- Light Infantry
- Pikemen

Target structure:

- Class point pool: `31`
- Shared class tree: roughly `55-70` possible ranks
- Specialization point pool: roughly `60`
- Each specialization tree: roughly `120-180` possible ranks
- Each major lane has roughly `16-24` possible ranks
- Lane investment matters; players cannot jump sideways without connected branches

Core rule:

`The class tree shows familiar infantry stats. The specialization tree carries the deeper discipline, formation, and pressure behavior.`

Visible class-tree stats may include:

- Health
- Attack
- Defense
- Ranged Damage Taken
- Anti-Cavalry Damage
- Permanent Casualties
- Training Cost
- Refit Cost

Hidden/internal values may include:

- Cohesion
- Formation lock
- Brace quality
- Panic resistance
- Line adjacency
- Breach confidence
- Rout delay

## Shared Class Tree Lanes

| Lane | Identity | Primary Value |
| --- | --- | --- |
| Heavy Infantry | Armored professional line | Durable line holders and breach fighters |
| Pike Command | Anti-cavalry discipline | Denial, bracing, and protection of nearby formations |
| Light Infantry | Flexible line troops | Movement, screening, rotation, and cost control |

## Heavy Infantry Lane

Heavy Infantry should have `18-22` possible ranks.

Sub-branches:

- `Armor And Shield`
- `Line Pressure`
- `Casualty Control`

### Armor And Shield

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Heavy Infantry Health | `3/3` | Heavy Infantry Health `+1%` per rank | Cohesion floor |
| Heavy Infantry Defense | `3/3` | Heavy Infantry Defense `+1%` per rank | Formation lock |
| Shield Wall Drill | `2/2` | Heavy Infantry takes `-1%` ranged damage per rank while holding | Suppression resistance |
| Armorers' Routine | `2/2` | Heavy Infantry refit cost `-1%` per rank | Readiness preservation |
| Close Order | `2/2` | Heavy Infantry Defense `+1%` while adjacent to friendly infantry | Line adjacency |

### Line Pressure

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Measured Advance | `2/2` | Heavy Infantry Attack `+1%` while advancing slowly | Cohesion push |
| Push Of Shields | `2/2` | Heavy Infantry Attack `+1%` against weakened lines | Pressure timing |
| Grind Them Down | `2/2` | Heavy Infantry Attack `+1%` in prolonged melee | Fatigue pressure |
| Sergeant's Call | `2/2` | Nearby infantry Defense `+1%` while holding | Command adjacency |
| Iron Center | `1/1` | Heavy Infantry Health `+3%` while anchoring the center line | Rout delay |

### Casualty Control

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Triage Discipline | `2/2` | Heavy Infantry permanent casualties `-1%` per rank | Wounded conversion |
| Rotate The Front | `2/2` | Heavy Infantry takes `-1%` casualties in prolonged melee per rank | Strength smoothing |
| Veteran Sergeants | `2/2` | Heavy Infantry recovers faster after successful defense | Veteran confidence memory |
| Held Formation | `2/2` | Heavy Infantry permanent casualties `-1%` while not routed | Panic-loss reduction |

## Pike Command Lane

Pike Command should have `18-24` possible ranks.

Sub-branches:

- `Brace`
- `Screen`
- `Cavalry Punishment`

### Brace

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Pike Health | `3/3` | Pikemen Health `+1%` per rank | Brace floor |
| Pike Discipline | `3/3` | Pikemen Defense `+1%` while stationary per rank | Formation lock |
| Set Pikes | `1/1` | Unlocks prepared anti-cavalry stance | Brace state |
| Braced Feet | `2/2` | Pikemen take `-1%` charge damage per rank while set | Charge absorption |
| No Gaps | `2/2` | Pikemen Defense `+1%` when adjacent to infantry | Line adjacency |

### Screen

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Spear Screen | `2/2` | Friendly ranged formations behind pikes take `-1%` cavalry damage per rank | Screen coverage |
| Pike Rotation | `2/2` | Pikemen reposition faster after setting pikes | Rebrace delay |
| Protect The Bowline | `2/2` | Allied archers behind pikes gain Defense `+1%` | Support adjacency |
| Narrow The Approach | `2/2` | Enemy cavalry charge damage `-1%` near gates and bridges per rank | Terrain denial |
| Drill Square | `1/1` | Pikemen resist flank pressure better while stationary | Flank brace |

### Cavalry Punishment

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Pike Attack | `3/3` | Pikemen Anti-Cavalry Damage `+1%` per rank | Counter-impact |
| Punish The Charge | `2/2` | Cavalry charging prepared pikes suffers `+1%` permanent casualties per rank | Bad-charge memory |
| Horses Break First | `2/2` | Cavalry charge damage `-1%` against prepared pikes per rank | Mount panic |
| Bloody Stakes | `2/2` | Pikemen Anti-Cavalry Damage `+1%` in prepared terrain | Terrain preparation |
| Wall Of Points | `1/1` | Prepared pikes greatly blunt elite cavalry charges | Strong brace event |

## Light Infantry Lane

Light Infantry should have `16-22` possible ranks.

Sub-branches:

- `Mobility`
- `Screening`
- `Economy`

### Mobility

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Light Infantry Health | `3/3` | Light Infantry Health `+1%` per rank | Rally stability |
| Marching Kit | `2/2` | Light Infantry March Speed `+1%` per rank | Fatigue curve |
| Fast Rotation | `2/2` | Light Infantry recovers faster after repositioning | Rotation delay |
| Field Steps | `2/2` | Light Infantry takes `-1%` terrain movement penalty per rank | Terrain handling |

### Screening

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Screen The Line | `2/2` | Adjacent Heavy Infantry takes `-1%` ranged damage per rank | Support screen |
| Flank Guards | `2/2` | Light Infantry Defense `+1%` against flanking attacks | Flank warning |
| Skirmish Pressure | `2/2` | Light Infantry Attack `+1%` against exposed ranged troops | Target priority |
| Cover Withdrawal | `2/2` | Allied formations suffer `-1%` permanent casualties while withdrawing nearby | Disengagement cover |

### Economy

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Simple Kit | `2/2` | Light Infantry training cost `-1%` per rank | Replacement readiness |
| Camp Routine | `2/2` | Light Infantry upkeep `-1%` per rank | Maintenance smoothing |
| Ready Replacements | `2/2` | Light Infantry replacement cost `-1%` per rank | Green-rank integration |
| Field Company | `1/1` | Light Infantry recovers faster after defensive victories | Unit confidence |

## Class Tree Capstones

| Capstone | Lane | Player-Facing Effect | Hidden/Internal |
| --- | --- | --- | --- |
| Iron Center | Heavy Infantry | Heavy Infantry Health `+3%` while anchoring the center line | Rout delay |
| Wall Of Points | Pike Command | Prepared pikes greatly blunt elite cavalry charges | Strong brace event |
| Field Company | Light Infantry | Light Infantry recovers faster after defensive victories | Unit confidence |

## Specialization Tree Scale

Each Man-At-Arms specialization should have `120-180` possible ranks and `60` spendable specialization points.

| Specialization | Possible Ranks | Spendable Points | Build Routes | Design Goal |
| --- | ---: | ---: | ---: | --- |
| Line | `120-180` | `60` | `4-5` | Many ways to hold, advance, and grind |
| Pike | `120-180` | `60` | `4-5` | Many ways to deny cavalry and protect the line |
| Breach Defense | `120-180` | `60` | `4-5` | Many ways to hold gates, breaches, and city interiors |

## Balance Rules

- Heavy Infantry should beat Light Infantry in a stand-up line fight.
- Light Infantry should reposition and screen better.
- Pike Command should punish cavalry but struggle if outmaneuvered or bombarded.
- Man-At-Arms should not chase well.
- Man-At-Arms should be strongest when prepared and positioned.
