# Strategic Map Rules

## Design Goal

The world map should not be a flat grid of disposable tiles.

This game needs a strategic map built around:

- cities;
- territory nodes;
- roads;
- trails;
- bridges;
- passes;
- resource lands;
- watch posts;
- ruins;
- siege perimeters;
- battle-scarred land.

Core rule:

`Land matters because armies physically move through it, fight over it, damage it, and must control routes to keep it.`

## Map Structure

The map should use meaningful nodes instead of thousands of identical squares.

### City Nodes

A city is a fixed stronghold.

It has:

- internal limited resource nodes;
- walls and gates;
- connected approach routes;
- surrounding territory nodes;
- siege perimeter sectors;
- nearby roads, trails, bridges, and resource sites.

### Territory Nodes

Territory nodes are the meaningful land parcels around cities.

Examples:

- farmland;
- pasture;
- forest;
- mine;
- quarry;
- village;
- watch post;
- road junction;
- bridge;
- river crossing;
- ruin approach;
- monster ground;
- siege camp site.

Each territory node should track:

- owner;
- controller;
- terrain;
- resource type;
- production state;
- watch state;
- connected routes;
- garrison or patrol presence;
- current status;
- recent battle history.

## Territory Statuses

Territory should not only be owned or unowned.

| Status | Meaning |
| --- | --- |
| Controlled | Produces normally for controller |
| Contested | Multiple forces or claims are active |
| Occupied | Held by a hostile force physically present or supplied |
| Neutralized | Control collapsed; no one benefits yet |
| Ravaged | Damaged by battle; production disabled or reduced until repaired |
| Rebel / Bandit | Control collapsed into PvE hostile state |
| Shield-Maintenance | Protected territory produces only maintenance plus limited surplus |

## Route-Based Movement

Armies move through routes, not teleporting across the map.

Routes may be:

- roads;
- trails;
- bridges;
- river crossings;
- mountain passes;
- forest paths;
- open plains;
- siege approaches.

Route choice affects:

- march time;
- fatigue;
- scout visibility;
- interception risk;
- ambush risk;
- arrival order;
- withdrawal options.

There are no teleports.

Every formation is always somewhere:

- home;
- garrisoned;
- marching;
- gathering;
- patrolling;
- camping;
- sieging;
- fighting;
- withdrawing;
- scattered;
- destroyed.

## City Encirclement

A city is not fully surrounded just because one army attacks it.

Each city has multiple approach sectors.

Example:

- North road;
- East bridge;
- South farms;
- West forest trail;
- Gate approach;
- river crossing;
- hill road.

Attackers must control enough approach sectors to create a true encirclement.

### Partial Siege

If at least one valid approach remains open:

- allied reinforcements may enter directly through the open approach;
- garrisoned allied formations may withdraw through the open approach;
- supplies may still enter at reduced rate;
- Fighting Withdrawal is not required for a clean exit through that open route;
- attackers must either close the gap or risk relief.

### Full Encirclement

If all valid approaches are controlled, blocked, or under hostile fire:

- direct reinforcement into the city is blocked;
- relief forces must fight through the perimeter;
- garrisoned allied forces must attempt Fighting Withdrawal to escape;
- supplies are cut or severely reduced;
- siege pressure becomes much more dangerous.

Design principle:

`Do not just hit the wall. Control the roads.`

## Siege Perimeters

When a siege begins, the city generates or activates a siege perimeter.

The perimeter is divided into sectors.

Example:

| Sector | Terrain | Strategic Meaning |
| --- | --- | --- |
| North Approach | Forest | Ambush and Ranger value |
| East Approach | Road | Fast relief and interception |
| South Approach | Farmland | Open cavalry fighting |
| West Approach | Hill | Scout and ranged advantage |
| Gate Approach | Fortified Road | Strong watch and defense |
| River Crossing | Bridge | Chokepoint |

Each sector can be:

- open;
- watched;
- contested;
- controlled by attacker;
- controlled by defender;
- blocked;
- ravaged.

## City Sack Rules

A city sack should be severe but not account-ending.

When a city is sacked:

- the capital survives;
- internal limited resource nodes remain;
- external territory control collapses;
- walls, gates, and buildings may be damaged;
- stored resources may be looted up to a cap;
- formations may be wounded, scattered, or permanently damaged by the battle;
- the city enters a recovery state;
- historical titles and records are created.

The attacker does not automatically gain the entire territory network.

Sacking collapses control.

It does not magically transfer an empire.

## Territory Collapse After Sack

When a city is sacked, each external territory node controlled by that city is evaluated.

Possible outcomes:

| Outcome | Condition |
| --- | --- |
| Occupied | Attacker physically controls the node or its route |
| Neutralized | Control collapses and no one holds it |
| Ravaged | Battle occurred there or nearby damage was severe |
| Rebel / Bandit | Control collapses into hostile PvE disorder |
| Contested | Multiple forces are actively nearby |

Default Sack v1:

- all external territory control is removed from defender;
- nodes with attacker armies become `Occupied`;
- nodes where battles occurred become `Ravaged`;
- remaining nodes become `Neutralized`;
- some unstable nodes may become `Rebel / Bandit`;
- defender can reclaim outward from the capital along connected routes;
- allies can help reclaim;
- attacker must physically hold occupied nodes to keep them.

## Battle-Ravaged Land

Any territory node where a battle occurs can become `Ravaged`.

This includes:

- cavalry fights in farmland;
- infantry clashes on roads;
- siege camps bombarded by defenders;
- relief battles in open plains;
- ambushes in forests;
- bridge battles;
- Fighting Withdrawal engagements;
- repeated monster or PvE event damage if severe enough.

Ravaged land represents:

- burned crops;
- trampled fields;
- broken roads;
- dead livestock;
- damaged irrigation;
- abandoned workers;
- ruined camps;
- collapsed bridges;
- scattered tools;
- unsafe roads.

### Ravaged Effects

While Ravaged, a node may suffer:

- `0%` production if severely ravaged;
- reduced production if lightly ravaged;
- higher march fatigue;
- worse supply value;
- lower watch effectiveness;
- increased bandit/monster activity;
- increased repair cost if repeatedly fought over.

Example:

`Farmland - Ravaged`

- Food production disabled.
- Repair requires wood, labor, and time.
- Repeated battles increase repair cost.

Example:

`Road Junction - Ravaged`

- March speed bonus disabled.
- Repair requires stone, wood, and labor.
- Interception remains possible, but movement is slower.

## Ravage Severity

Ravage severity should depend on battle intensity.

| Severity | Trigger Example | Effect |
| --- | --- | --- |
| Light | small skirmish | reduced output |
| Moderate | meaningful battle | major output loss |
| Severe | large battle, siege engines, repeated fighting | production disabled |
| Devastated | repeated major battles or sack aftermath | production disabled, repair expensive |

Factors:

- number of formations involved;
- battle duration;
- cavalry presence in farmland or plains;
- siege engine use;
- fire/trap effects;
- routs and pursuit;
- repeated battles within a short time;
- whether defenders used scorched-earth actions.

## Repairing Ravaged Land

Ravaged nodes require resources and time to repair.

Repair may require:

- wood;
- stone;
- food;
- labor;
- tools;
- engineers;
- protected access to the node;
- route control from city to node.

Repair rules:

- cannot fully repair while node is actively contested;
- repair is faster if connected to controlled roads;
- Engineer talents can improve repair speed;
- SellSword recovery/logistics can reduce repair cost;
- alliance members can contribute resources or labor;
- repeated ravaging increases repair cost temporarily.

Player-facing example:

`Repair Farmland`

- Cost: wood, food, labor
- Time: 6 hours
- Requires controlled route to city
- Output restored from `0%` to `100%`

## Reclaiming Territory

After a sack or normal territory loss, land must be reclaimed through routes.

A player can reclaim from:

- capital;
- controlled territory node;
- allied-controlled connected node;
- active army camp;
- watch post.

Reclaiming may require:

- clearing hostile forces;
- defeating rebels or bandits;
- repairing damage;
- reestablishing watch;
- reconnecting the route network.

Reclaiming should not be tedious whack-a-mole.

Better reclaim actions:

- reclaim route;
- reclaim cluster;
- restore village;
- repair road;
- clear bandit control;
- reestablish watch post.

## Normal Territory Loss

Territory can also be lost outside of city sacks.

Ways to lose territory:

- enemy occupation;
- failed defense;
- isolated node cut off from city;
- rebellion/bandit event;
- abandoned upkeep;
- shield maintenance reducing active control;
- alliance war objective;
- resource site overrun.

City sacks are the dramatic collapse case.

Normal wars can still chip away at territory.

## Occupation Rules

Occupation requires physical presence or supply.

An attacker can occupy territory if:

- they have an army on the node;
- they control the route to it;
- they maintain a camp or watch post;
- defender control has been broken.

Occupation should not equal instant ownership.

Occupied land:

- may produce reduced resources for occupier;
- may require garrison upkeep;
- may be vulnerable to counterattack;
- may become contested if defender returns;
- may decay if occupier cannot maintain route control.

## Shield Interaction

When shielded:

- internal city nodes continue at limited output;
- external territory production drops to maintenance plus limited surplus;
- active gathering stops;
- shielded players cannot use territory as protected power projection;
- shielded territory should not be used to launch offensive actions.

If a shielded city is later sacked after the shield is gone or broken, external territory can still collapse under normal sack rules.

## Player-Facing Reports

Battle reports should explain land consequences clearly.

Examples:

- `The battle ravaged East Farmland. Food production has stopped until repaired.`
- `Your cavalry pursuit damaged the South Road. March speed bonus is disabled.`
- `Blackvale was sacked. External territory control has collapsed.`
- `North Forest became neutralized after the city fell.`
- `East Bridge is occupied by House Veyr because their army controls the crossing.`
- `West Pasture is ravaged after repeated cavalry fighting.`
- `Allied labor restored South Farmland to full production.`

## Why This Works

This map model supports the rest of the game:

- no teleports;
- meaningful sieges;
- route-based reinforcement;
- real encirclement;
- alliance relief operations;
- territory-first economy;
- terrain rules;
- battle aftermath;
- recovery wars after sacks.

Most city builders end with a battle report.

This game should often create a changed map.
