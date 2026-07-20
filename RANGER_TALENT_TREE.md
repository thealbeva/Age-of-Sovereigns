# Ranger Talent Tree

## Design Goal

The Ranger class tree is the information and ranged fieldcraft foundation.

It should make players better at knowing, hiding, warning, and preparing, without turning them into brute-force attackers.

Shared class identity:

- Scouts/Rangers
- ShortBow
- LongBow
- CrossBow

Target structure:

- Class point pool: `31`
- Shared class tree: roughly `55-70` possible ranks
- Specialization point pool: roughly `60`
- Each specialization tree: roughly `120-180` possible ranks
- Each major lane has roughly `16-24` possible ranks

Core rule:

`Rangers should make enemies uncertain before they make enemies dead.`

Visible stats may include:

- Scout Speed
- Scout Survival
- Report Detail
- Ranged Attack
- Ranged Accuracy
- Ranged Damage Taken
- Ambush Damage

Hidden/internal values may include:

- Report confidence
- False certainty
- Deception strength
- Watch-state pressure
- Ambush readiness
- Trail visibility
- Scout capture quality

## Shared Class Tree Lanes

| Lane | Identity | Primary Value |
| --- | --- | --- |
| Scouts | Recon and warning | Better reports and safer missions |
| Fieldcraft | Terrain, ambush, concealment | Hidden movement and prepared fights |
| Archery | Foot ranged troops | Prepared ranged pressure |

## Scouts Lane

Sub-branches:

- `Quick Scout`
- `Infiltration`
- `Counter-Scout`

### Quick Scout

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Scout Speed | `3/3` | Scout mission speed `+1%` per rank | Travel/report delay |
| Sharp Eyes | `3/3` | Scout report detail `+1%` per rank | Report confidence |
| Light Packs | `2/2` | Scout march fatigue `-1%` per rank | Return reliability |
| Fast Sketches | `2/2` | Quick Scout reports return faster | Report generation delay |
| Road Watch | `2/2` | Better warning of armies using roads | Route detection |

### Infiltration

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Quiet Movement | `2/2` | Scout survival `+1%` during infiltration per rank | Capture chance |
| Deep Look | `2/2` | Infiltration report detail `+1%` per rank | Tier mastery reveal |
| Hidden Entry | `2/2` | Scout capture chance `-1%` per rank | Watch-state bypass |
| Patient Eyes | `2/2` | Infiltration can reveal more readiness details | Readiness confidence |
| Ghost Patrol | `1/1` | Infiltration is harder to trace back to owner | Trace reduction |

### Counter-Scout

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Watch Rotation | `3/3` | Counter-scout detection `+1%` per rank | Watch-state lift |
| Trail Breakers | `2/2` | Enemy scout survival `-1%` in your territory per rank | Scout intercept |
| Interrogators | `2/2` | Captured scout ransom value `+1%` per rank | Intel extraction |
| Silent Watch | `1/1` | Earlier warning of reinforcements, sally attempts, and withdrawals | Event lead time |
| Hunter Net | `2/2` | Enemy infiltration takes longer in your territory | Infiltration delay |

## Fieldcraft Lane

Sub-branches:

- `Concealment`
- `Ambush`
- `Terrain`

### Concealment

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| False Trails | `3/3` | Enemy scout report accuracy `-1%` per rank | False certainty |
| Hidden Camps | `2/2` | Reserve formations are harder to detect | Reserve concealment |
| Masked Readiness | `2/2` | Enemy scouts see less readiness detail | Readiness distortion |
| Quiet Fires | `2/2` | Camp size is harder to estimate | Soldier count fuzz |
| False Camp | `1/1` | Enemy quick scouts may receive misleading ranges | Deception event |

### Ambush

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Ambush Damage | `3/3` | Ambush Damage `+1%` per rank | First-volley pressure |
| Prepared Ambush | `1/1` | Unlocks prepared ambush bonus in suitable terrain | Ambush state |
| Kill Lanes | `2/2` | Ranged Attack `+1%` from prepared positions per rank | Terrain firing lane |
| Snare Paths | `2/2` | Enemy march speed reduced in prepared ambush zones | Movement disruption |
| Vanish Routes | `2/2` | Ranger formations withdraw better after ambush | Disengagement route |

### Terrain

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Woodsmen | `2/2` | Forest movement penalty `-1%` per rank | Terrain handling |
| Hill Watch | `2/2` | Scout detail `+1%` from hills per rank | View angle |
| Swamp Paths | `2/2` | Swamp movement penalty `-1%` per rank | Fatigue reduction |
| Trail Maps | `2/2` | Allied march speed `+1%` through scouted routes | Shared map confidence |
| Master Of Ground | `1/1` | Prepared Ranger forces gain stronger terrain bonuses | Terrain state amplifier |

## Archery Lane

Sub-branches:

- `ShortBow`
- `LongBow`
- `CrossBow`

### ShortBow

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| ShortBow Attack | `3/3` | ShortBow Attack `+1%` per rank | Volley timing |
| Quick Volley | `2/2` | ShortBow attack speed `+1%` per rank | Suppression frequency |
| Close Cover | `2/2` | ShortBow takes `-1%` ranged damage per rank | Skirmish cover |
| Wall Peppering | `2/2` | ShortBow Attack `+1%` while defending walls | Wall angle |

### LongBow

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| LongBow Attack | `3/3` | LongBow Attack `+1%` per rank | Range pressure |
| Range Markers | `2/2` | LongBow Accuracy `+1%` from prepared terrain per rank | Range confidence |
| Arrow Storm | `2/2` | Exposed attackers take `+1%` ranged damage per rank | Suppression |
| High Arc | `2/2` | LongBow performs better over friendly lines | Arc safety |

### CrossBow

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| CrossBow Attack | `3/3` | CrossBow Attack `+1%` per rank | Armor pressure |
| Steel Bolts | `2/2` | CrossBow Damage `+1%` against armored formations per rank | Armor penetration |
| Brace And Fire | `2/2` | CrossBow Defense `+1%` while stationary | Reload discipline |
| Killing Ground | `1/1` | Prepared ranged formations hit harder against poorly scouted enemies | Information advantage |

## Class Tree Capstones

| Capstone | Lane | Player-Facing Effect | Hidden/Internal |
| --- | --- | --- | --- |
| Ghost Patrol | Scouts | Infiltration is harder to trace back to owner | Trace reduction |
| Master Of Ground | Fieldcraft | Prepared Ranger forces gain stronger terrain bonuses | Terrain state amplifier |
| Killing Ground | Archery | Prepared ranged formations hit harder against poorly scouted enemies | Information advantage |

## Specialization Tree Scale

| Specialization | Possible Ranks | Spendable Points | Build Routes | Design Goal |
| --- | ---: | ---: | ---: | --- |
| Scouting | `120-180` | `60` | `4-5` | Many ways to gather and share reliable intelligence |
| Deception | `120-180` | `60` | `4-5` | Many ways to mislead scouts and hide intent |
| Archery | `120-180` | `60` | `4-5` | Many ways to use foot ranged formations in prepared fights |

## Balance Rules

- Ranger should win before combat by knowing more or hiding more.
- Ranger should lose direct melee if caught unsupported.
- Archer power should depend heavily on preparation and protection.
- Deception must mislead, not create impossible lies.
- Scouting should reveal probabilities and confidence, not perfect truth.
