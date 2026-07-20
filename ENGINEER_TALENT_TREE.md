# Engineer Talent Tree

## Design Goal

The Engineer class tree is the siege and fortification foundation.

It should decide whether walls fall, hold, or become expensive to attack.

Shared class identity:

- Siege engines
- Fortifications
- Counter-siege systems

Target structure:

- Class point pool: `31`
- Shared class tree: roughly `55-70` possible ranks
- Specialization point pool: roughly `60`
- Each specialization tree: roughly `120-180` possible ranks
- Each major lane has roughly `16-24` possible ranks

Core rule:

`Engineers change the physical battle: walls, gates, traps, engines, and repair windows.`

Visible stats may include:

- Wall Damage
- Breach Damage
- Gate Damage
- Siege Defense
- Repair Speed
- Trap Damage
- Counter-Siege Damage
- Setup Speed

Hidden/internal values may include:

- Breach score weighting
- Section targeting
- Siege disruption
- Repair timing windows
- Trap reveal chance
- Counter-battery confidence

## Shared Class Tree Lanes

| Lane | Identity | Primary Value |
| --- | --- | --- |
| Siege Engines | Battering Ram, Trebuchet, Catapult | Creating breaches |
| Fortification | Walls, gates, traps, repairs | Preventing breaches |
| Counter-Siege | Defensive siege and targeting | Destroying or suppressing enemy engines |

## Siege Engines Lane

Sub-branches:

- `Setup`
- `Wall Breaking`
- `Crew Survival`

### Setup

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Siege Crew Health | `3/3` | Siege crews Health `+1%` per rank | Crew stability |
| Rigging Crews | `2/2` | Siege setup speed `+1%` per rank | Deployment delay |
| Worksite Discipline | `2/2` | Siege engines take `-1%` disruption per rank while escorted | Disruption resistance |
| Road Haulers | `2/2` | Siege march penalty `-1%` per rank | Logistics drag |
| Prepared Timber | `2/2` | Siege replacement cost `-1%` per rank | Rebuild readiness |

### Wall Breaking

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Siege Math | `3/3` | Wall Damage `+1%` per rank | Breach score weighting |
| Ram Crews | `2/2` | Battering Ram Gate Damage `+1%` per rank | Gate pressure |
| Stone Calibration | `2/2` | Trebuchet Wall Damage `+1%` per rank | Section accuracy |
| Catapult Crews | `2/2` | Catapult Damage `+1%` against wall defenders | Suppression mix |
| Breach Engineer | `1/1` | Siege engines deal more breach damage while protected by allied screens | Protected worksite check |

### Crew Survival

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Shielded Worksite | `2/2` | Siege crews take `-1%` ranged damage per rank | Worksite cover |
| Spare Parts | `2/2` | Siege engine permanent losses `-1%` per rank | Salvage conversion |
| Crew Rotation | `2/2` | Siege crews recover faster after bombardment | Fatigue smoothing |
| Smoke Screens | `2/2` | Siege crews take `-1%` damage from defensive ranged attacks | Visibility disruption |

## Fortification Lane

Sub-branches:

- `Walls And Gates`
- `Repairs`
- `Traps`

### Walls And Gates

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Masonry Survey | `3/3` | Wall Health `+1%` per rank | Section durability |
| Gate Bracing | `3/3` | Gate Health `+1%` per rank | Gate-collapse delay |
| Wall Walks | `2/2` | Wall defenders take `-1%` ranged damage per rank | Defender cover |
| Murder Holes | `2/2` | Defenders deal `+1%` damage near gates per rank | Gate kill zone |
| Hold The Wall | `1/1` | Walls resist sudden collapse longer after critical damage | Critical threshold buffer |

### Repairs

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Emergency Crews | `2/2` | Repair Speed `+1%` per rank during active siege | Repair window |
| Rapid Bracing | `1/1` | Unlocks emergency bracing action | Temporary breach delay |
| Stone Stores | `2/2` | Repair cost `-1%` per rank | Supply smoothing |
| Night Repairs | `2/2` | Repair Speed `+1%` when not under direct bombardment | Bombardment state check |
| Stabilize Breach | `2/2` | Breach growth slowed while repairs are active | Breach-rate damping |

### Traps

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Trap Lines | `3/3` | Trap Damage `+1%` per rank | Trigger quality |
| Concealed Works | `2/2` | Enemy scouts are less likely to reveal traps | Trap concealment |
| Caltrop Fields | `2/2` | Enemy cavalry takes `+1%` damage near prepared approaches | Movement snare |
| Fire Pots | `2/2` | Enemy siege crews take `+1%` damage near walls | Siege disruption |
| Prepared Killing Ground | `1/1` | Traps and wall defenders perform better in selected approach lanes | Prepared lane state |

## Counter-Siege Lane

Sub-branches:

- `Targeting`
- `Engine Killing`
- `Suppression`

### Targeting

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Range Tables | `3/3` | Counter-Siege Accuracy `+1%` per rank | Target confidence |
| Spotter Signals | `2/2` | Counter-Siege Damage `+1%` against siege crews | Spotter accuracy |
| Survey Angles | `2/2` | Counter-Siege setup speed `+1%` | Firing lane prep |
| Engineer's Eye | `2/2` | Better chance to identify high-threat enemy siege | Threat weighting |
| Counter-Battery Survey | `1/1` | Unlocks improved counter-battery targeting | Target priority |

### Engine Killing

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Shatter Frames | `3/3` | Damage to enemy siege engines `+1%` per rank | Structural damage |
| Fire Discipline | `2/2` | Counter-siege fatigue `-1%` per rank | Ammunition waste reduction |
| Wheel Shots | `2/2` | Enemy siege setup speed slowed after hits | Mobility damage |
| Crew Panic | `2/2` | Enemy siege crews take `+1%` permanent casualties after direct hits | Crew rout pressure |

### Suppression

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Suppressing Arcs | `2/2` | Enemy Wall Damage `-1%` while under counter-siege fire | Bombardment disruption |
| Silence The Guns | `1/1` | Strong counter-battery hits temporarily reduce enemy breach pressure | Suppression event |
| Smoke And Splinters | `2/2` | Enemy siege accuracy reduced after engine damage | Accuracy penalty |
| Defensive Batteries | `2/2` | Defensive siege survives longer while inside prepared works | Protected battery |

## Class Tree Capstones

| Capstone | Lane | Player-Facing Effect | Hidden/Internal |
| --- | --- | --- | --- |
| Breach Engineer | Siege Engines | Protected siege engines deal more breach damage | Protected worksite check |
| Hold The Wall | Fortification | Walls resist sudden collapse longer after critical damage | Critical threshold buffer |
| Silence The Guns | Counter-Siege | Counter-battery hits temporarily reduce enemy breach pressure | Suppression event |

## Specialization Tree Scale

| Specialization | Possible Ranks | Spendable Points | Build Routes | Design Goal |
| --- | ---: | ---: | ---: | --- |
| Siegecraft | `120-180` | `60` | `4-5` | Many ways to break walls and gates |
| Fortification | `120-180` | `60` | `4-5` | Many ways to keep cities alive |
| Counter-Siege | `120-180` | `60` | `4-5` | Many ways to kill or suppress enemy engines |

## Balance Rules

- Engineer owns breach math, but cannot protect siege alone.
- Siege Engines need screens.
- Fortification buys time, not invulnerability.
- Counter-Siege can disrupt breach pressure but should require positioning and vision.
- Engineer should be strategically essential without being a solo war answer.
