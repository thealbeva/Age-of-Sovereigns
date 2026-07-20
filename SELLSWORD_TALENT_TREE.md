# SellSword Talent Tree

## Design Goal

The SellSword class tree is the mercenary economy and flexible war-logistics foundation.

It should not create the highest raw combat output.

It should make war cheaper, recovery smoother, contracts more useful, and ransom systems deeper.

Shared class identity:

- Contracts
- Recovery
- Ransom
- Mixed formations

Target structure:

- Class point pool: `31`
- Shared class tree: roughly `55-70` possible ranks
- Specialization point pool: roughly `60`
- Each specialization tree: roughly `120-180` possible ranks
- Each major lane has roughly `16-24` possible ranks

Core rule:

`SellSword wins by staying in the war.`

Visible stats may include:

- Upkeep
- Training Cost
- Refit Cost
- Replacement Cost
- Recovery Speed
- Ransom Cost
- Ransom Income
- Permanent Casualties

Hidden/internal values may include:

- Contract reliability
- Political dirt
- Mercenary morale
- Prisoner classification
- Negotiation leverage
- Green replacement integration
- Honor/title dampening

## Shared Class Tree Lanes

| Lane | Identity | Primary Value |
| --- | --- | --- |
| Contracts | Paid commitments | Flexible alliance and defensive work |
| Recovery | War economy | Cheaper losses and faster return to readiness |
| Ransom | Prisoners and scouts | Captures, negotiations, and dirty money |

## Contracts Lane

Sub-branches:

- `Paid Defense`
- `Flexible Terms`
- `Mixed Company`

### Paid Defense

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Contract Rates | `3/3` | Contract deployment cost `-1%` per rank | Contract friction |
| Contract Guard | `1/1` | Formations defending under contract fight more reliably | Mercenary morale floor |
| Paid Watch | `2/2` | Contracted garrisons recover faster after defense | Contract readiness |
| Guard Clause | `2/2` | Contracted defenders suffer `-1%` permanent casualties per rank | Liability conversion |
| Reliable Hire | `2/2` | Contracted formations arrive with better readiness | Contract fulfillment |

### Flexible Terms

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Flexible Terms | `3/3` | Cost to change contract assignment `-1%` per rank | Reassignment friction |
| Short Notice | `2/2` | Contract response speed `+1%` per rank | Mobilization delay |
| Side Letter | `2/2` | Contract changes create less political backlash | Reputation dampening |
| Paid Exit | `2/2` | Contracted formations withdraw with fewer permanent casualties | Exit condition |
| War As Business | `1/1` | Contracted defensive actions become cheaper and steadier, but less honorable | Honor dampening |

### Mixed Company

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Mixed Company | `3/3` | Mixed formations recover readiness `+1%` per rank | Mixed morale smoothing |
| Practical Kit | `2/2` | Mixed formation upkeep `-1%` per rank | Supply simplification |
| No Questions Asked | `2/2` | Mixed formations suffer fewer penalties from messy politics | Political dirt |
| Useful Veterans | `2/2` | Mixed veteran formations recover faster after failed attacks | Veteran confidence |

## Recovery Lane

Sub-branches:

- `Upkeep`
- `Replacement`
- `Refit`

### Upkeep

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Lean Camps | `3/3` | Formation upkeep `-1%` per rank | Camp efficiency |
| Forage Contracts | `2/2` | Campaign supply cost `-1%` per rank | Supply smoothing |
| Cheap Lodging | `2/2` | Idle formation upkeep `-1%` per rank | Maintenance state |
| Quartermaster Deals | `2/2` | Army upkeep `-1%` during recovery | Recovery supply |
| Still In The War | `1/1` | Formations recover readiness faster after losses | Readiness boost |

### Replacement

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Replacement Brokers | `3/3` | Casualty replacement cost `-1%` per rank | Green integration |
| Fast Muster | `2/2` | Replacement speed `+1%` per rank | Muster delay |
| Paid Recruits | `2/2` | Training cost `-1%` per rank | Recruit quality variance |
| Keep The Names | `2/2` | Reconstituted formations lose less readiness | Legacy continuity |

### Refit

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Spare Kit | `3/3` | Refit cost `-1%` per rank | Equipment stockpile |
| Salvage Rights | `2/2` | Equipment recovery cost `-1%` after battle per rank | Salvage conversion |
| Patch And March | `2/2` | Damaged formations return to field faster | Readiness cap |
| Paid To Survive | `1/1` | Failed attacks cause fewer formation-destroying outcomes | Destruction avoidance |

## Ransom Lane

Sub-branches:

- `Negotiation`
- `Prisoners`
- `Scout Exchange`

### Negotiation

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Hard Bargain | `3/3` | Ransom paid `-1%` per rank | Negotiation leverage |
| Better Terms | `2/2` | Better chance to negotiate partial prisoner return | Deal quality |
| Quiet Brokers | `1/1` | Ransom deals create less public fallout | Political dirt reduction |
| Everyone Has A Price | `1/1` | Ransom systems become cheaper and more flexible | Honor/title dampening |

### Prisoners

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Useful Prisoners | `3/3` | Ransom income `+1%` per rank | Prisoner classification |
| Gentle Chains | `2/2` | Prisoners are less likely to die before ransom | Captive survival |
| Valuable Names | `2/2` | Veteran or titled prisoners are worth more | Legacy valuation |
| Holding Pens | `2/2` | Captured formation upkeep `-1%` per rank | Captive maintenance |

### Scout Exchange

| Talent | Cap | Player-Facing Effect | Hidden/Internal |
| --- | ---: | --- | --- |
| Scout Exchange | `2/2` | Returned scouts recover faster after ransom | Scout morale repair |
| Loose Tongues | `2/2` | Captured scouts provide better ransom value | Intel extraction |
| No Hard Feelings | `2/2` | Ransomed scouts suffer less long-term readiness damage | Trauma dampening |
| Sell The Story | `2/2` | Ransom-heavy behavior creates less reputation damage | Public framing |

## Class Tree Capstones

| Capstone | Lane | Player-Facing Effect | Hidden/Internal |
| --- | --- | --- | --- |
| War As Business | Contracts | Contracted defensive actions become cheaper and steadier, but less honorable | Honor dampening |
| Still In The War | Recovery | Formations recover readiness faster after losses | Readiness boost |
| Everyone Has A Price | Ransom | Ransom systems become cheaper and more flexible | Honor/title dampening |

## Specialization Tree Scale

| Specialization | Possible Ranks | Spendable Points | Build Routes | Design Goal |
| --- | ---: | ---: | ---: | --- |
| Contracts | `120-180` | `60` | `4-5` | Many ways to sell defensive and political military service |
| Recovery | `120-180` | `60` | `4-5` | Many ways to absorb losses and stay active |
| Ransom | `120-180` | `60` | `4-5` | Many ways to profit from captures, exchanges, and prisoners |

## Balance Rules

- SellSword should be economically powerful but not top raw combat.
- Recovery must not erase the emotional value of formation loss.
- Ransom should create politics, not just money.
- Contract defense should be useful but less prestigious than loyal defense.
- SellSword power must never become pay-to-win-like scaling.
