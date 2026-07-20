# Terrain Rules

## Design Goal

Terrain should make geography matter without becoming unreadable.

Players should understand the obvious parts:

- roads are faster;
- swamps are slow;
- forests hide movement;
- hills help scouting and ranged troops;
- rivers and bridges create chokepoints;
- open plains favor cavalry.

The deeper simulation can remain hidden:

- ambush readiness;
- route confidence;
- formation cohesion;
- scout trace;
- pursuit conversion;
- withdrawal difficulty;
- siege perimeter control.

Core rule:

`Terrain changes movement, information, and battle conditions. It should not be a random stat soup.`

## Terrain Categories

Every world-map tile, route segment, resource area, ruin approach, and siege perimeter should have a primary terrain type.

Some locations may also have secondary tags.

Example:

`Forest Road`

- Primary terrain: `Forest`
- Secondary tag: `Road`

Example:

`Hill Fort`

- Primary terrain: `Hill`
- Secondary tag: `Fortified`

## Core Terrain Types

| Terrain | Movement | Scouting | Battle Identity |
| --- | ---: | --- | --- |
| Road | `+3%` march speed | Easier to track | Fast movement, easier interception |
| Plains | baseline | Clear visibility | Cavalry-friendly open fighting |
| Forest | `-5%` march speed | Harder to scout | Ambush, concealment, reduced cavalry value |
| Hill | `-3%` march speed | Better sightlines from high ground | Ranged and scouting advantage |
| Swamp | `-10%` march speed | Poor visibility, strong traces | Fatigue, slow movement, cavalry penalty |
| River Crossing | `-8%` march speed | Predictable crossing points | Chokepoint, ambush, interception |
| Bridge | `-4%` march speed under pressure | Easy to watch | Chokepoint and pursuit trap |
| Mountain Pass | `-12%` march speed | Limited routes | Chokepoint, strong defense, poor cavalry |
| Desert / Wasteland | `-6%` march speed | Long visibility, high fatigue | Supply strain, exposed movement |
| Snow / Frozen Ground | `-8%` march speed | Tracks persist longer | Fatigue, slower recovery, risky pursuit |
| Urban / City Outskirts | `-5%` march speed | Many hiding places | Infantry and ambush advantage |
| Fortified Perimeter | varies | high watch coverage | Siege, counter-siege, controlled approaches |

These values are first-pass defaults.

They should be tuned in simulation.

## Secondary Terrain Tags

Secondary tags modify the primary terrain.

| Tag | Effect |
| --- | --- |
| Road | Adds `+3%` march speed unless terrain blocks it |
| Trail | Adds `+1%` march speed, improves Ranger movement |
| Mud | Adds `-4%` march speed, increases fatigue |
| Rain | Adds `-3%` march speed, worsens ranged accuracy slightly |
| Fog | Slows scouting and increases ambush uncertainty |
| Prepared | Defender has built traps, stakes, works, or marked ranges |
| Fortified | Improves defensive setup and watch state |
| Contested | Increases scout trace, interception risk, and battle escalation chance |
| Controlled Road | Owner or alliance has better warning and interception |
| Ruined | Slower movement, better ambush opportunities, worse formation cohesion |

## Movement Rules

Movement should be route-based, not just straight-line distance.

March time should consider:

- base distance;
- primary terrain;
- secondary terrain tags;
- formation speed;
- commander traits;
- doctrine bonuses;
- fatigue;
- weather;
- whether the route is scouted;
- whether the route is controlled by enemy or allied forces.

Visible examples:

- Road: `+3%` march speed
- Forest: `-5%` march speed
- Swamp: `-10%` march speed
- Mountain Pass: `-12%` march speed

Hidden/internal modifiers:

- scout route confidence;
- ambush exposure;
- formation cohesion during arrival;
- fatigue on arrival;
- chance of delayed arrival;
- chance of being detected before arrival.

## Formation Movement By Terrain

Different formations should care about terrain differently.

| Formation Type | Favored Terrain | Poor Terrain |
| --- | --- | --- |
| Scouts/Rangers | Forest, Hills, Trails, Ruins | Open roads under heavy watch |
| Light Infantry | Forest, Urban, Hills | Swamp, Mountain Pass with heavy gear |
| Heavy Infantry | Urban, Breach, Fortified Perimeter | Swamp, Desert, long open pursuit |
| Pikemen | Bridges, Roads, Passes, Gates | Broken forest, swamp, scattered terrain |
| Ranged Cavalry | Plains, Roads, Wasteland | Forest, Swamp, Urban |
| Light Cavalry | Plains, Roads, Hills | Swamp, Forest, Mountain Pass |
| Heavy Cavalry | Plains, Roads, Open Approaches | Swamp, Forest, Bridges, Urban |
| ShortBow | Forest, Walls, Urban | Open plains without cover |
| LongBow | Hills, Prepared Ground, Walls | Forest density, fog, heavy rain |
| CrossBow | Walls, Urban, Fortified Perimeter | Long pursuit, swamp |
| Siege Engines | Roads, Prepared Siege Lines | Swamp, Forest, Mountain Pass |

## Battle Terrain Effects

Terrain should affect the kind of battle being fought.

### Plains

Visible:

- Cavalry performs better in open-field charges.
- Ranged Cavalry has more room to kite.

Hidden:

- higher pursuit conversion;
- cleaner charge handling;
- fewer ambush opportunities.

### Forest

Visible:

- March speed reduced.
- Cavalry charge damage reduced.
- Rangers and ambushes perform better.

Hidden:

- scout report uncertainty increases;
- ambush readiness increases;
- formation cohesion may suffer for large heavy formations.

### Hills

Visible:

- Ranged formations perform better from prepared high ground.
- Scouts gain better sightlines.

Hidden:

- better incoming march detection;
- improved range confidence;
- cavalry charge effectiveness depends on slope direction.

### Swamps

Visible:

- March speed heavily reduced.
- Cavalry performs worse.
- Fatigue rises faster.

Hidden:

- disengagement difficulty increases;
- pursuit becomes unreliable;
- formation cohesion suffers over time.

### River Crossings And Bridges

Visible:

- Movement is slower.
- Chokepoint defense improves.
- Ambush and interception are easier.

Hidden:

- withdrawal failure risk increases;
- cavalry charge lanes are limited;
- pike and infantry discipline matter more.

### Mountain Passes

Visible:

- Movement is slow.
- Defensive formations perform better.
- Cavalry performs worse.

Hidden:

- battle width narrows;
- reinforcements arrive in constrained order;
- escape and pursuit routes become predictable.

### Urban / City Outskirts

Visible:

- Infantry and short-range formations perform better.
- Cavalry performs worse.
- Ambush and scouting complexity increase.

Hidden:

- line of sight breaks;
- small formations matter more;
- ranged cavalry loses kiting space.

## Terrain And Scouting

Terrain should shape scout missions.

Quick Scout:

- Faster on roads and plains.
- Less reliable in forests, swamps, fog, ruins, and urban outskirts.
- More likely to leave traces on roads, snow, mud, and controlled territory.

Infiltration:

- Stronger in forests, ruins, urban outskirts, fog, and hills.
- Riskier in controlled roads, fortified perimeters, bridges, and active siege zones.
- Slower in swamps, mountains, snow, and heavy rain.

Scout report examples:

- `Tracks suggest a mounted force used the north road.`
- `Forest cover prevents exact formation count.`
- `High ground confirms siege engines are present.`
- `Mud trails indicate heavy formations passed recently.`
- `Bridge watch detected banners before contact.`

## Terrain And Watch States

Terrain can raise or lower watch effectiveness.

| Terrain | Watch Effect |
| --- | --- |
| Road | Easier to detect movement, easier to track |
| Forest | Harder to detect, easier to hide |
| Hill | Better early warning |
| Swamp | Movement leaves traces, but visibility is poor |
| Bridge | Easy to watch, hard to bypass |
| Mountain Pass | Easy to monitor if controlled |
| Urban | Many hiding places, hard to fully lock down |
| Fortified Perimeter | Strong watch coverage |

Alliance at war still sets minimum watch state as designed elsewhere.

Terrain modifies effectiveness, not the minimum state itself.

## Terrain And Sieges

Siege terrain should matter before the first wall is hit.

Important siege terrain factors:

- approach roads;
- nearby hills;
- forests near siege camp;
- rivers and bridges around the city;
- swampy or muddy approaches;
- city outskirts;
- prepared defensive works;
- controlled fields;
- siege perimeter lines.

Examples:

- A city with hill approaches is easier to scout but may give attackers strong siege placement.
- A city surrounded by forests is harder to scout and easier to ambush around.
- A city behind bridges creates strong chokepoints for relief and withdrawal.
- A city in swamp terrain is hard to siege quickly but also hard to reinforce.
- A city on open plains is easier for cavalry screens to control.

## Siege Perimeter Terrain

An active siege creates a temporary `Siege Perimeter` around the city.

The perimeter should be divided into approach sectors:

- North approach
- East approach
- South approach
- West approach
- Gate approach
- Breach approach
- Siege camp
- Relief corridor
- Withdrawal corridor

Each sector has terrain.

Example:

| Sector | Terrain | Meaning |
| --- | --- | --- |
| North Approach | Forest | Good for Ranger ambushes |
| East Approach | Road | Fast relief and interception |
| South Approach | Swamp | Slow siege movement |
| West Approach | Hill | Good counter-siege sightlines |
| Gate Approach | Fortified Road | Strong watch and defense |

This lets relief, interception, sally, and Fighting Withdrawal use terrain instead of abstract success rolls.

## Fighting Withdrawal And Terrain

Terrain strongly affects Fighting Withdrawal.

Helpful to withdrawal:

- forest cover;
- hills with hidden trails;
- controlled roads;
- allied screened corridors;
- fog or night conditions;
- Ranger concealment;
- Cavalry road screening.

Harmful to withdrawal:

- bridges controlled by enemy;
- swamp;
- mountain passes;
- open plains under enemy cavalry control;
- fortified enemy perimeter;
- poor scout coverage;
- heavy siege encirclement.

Visible player report examples:

- `The withdrawal route crosses enemy-held bridges. Escape risk is high.`
- `Forest cover improves the chance of partial escape.`
- `Enemy cavalry controls the open plain. Pursuit risk is severe.`
- `Rangers found a hidden trail through the western hills.`

## Terrain And Class Identity

### Knight

Favored:

- plains;
- open roads;
- city breach;
- fortified lines when using Heavy Infantry;
- banner positions behind or beside allied formations.

Poor:

- swamps;
- dense forest;
- tight bridges for cavalry;
- mountain passes for mounted shock.

### Man-At-Arms

Favored:

- bridges;
- gates;
- breaches;
- fortified perimeters;
- roads when holding formation;
- city streets.

Poor:

- open pursuit;
- scattered forests;
- swampy extended fights.

### Engineer

Favored:

- roads for moving siege;
- hills for sightlines;
- prepared siege lines;
- fortified works.

Poor:

- swamps;
- dense forests;
- mountain passes;
- exposed open plains without screens.

### Ranger

Favored:

- forests;
- hills;
- ruins;
- trails;
- fog;
- urban outskirts.

Poor:

- open roads under heavy watch;
- plains with enemy cavalry control.

### Cavalry

Favored:

- plains;
- roads;
- open approaches;
- controlled route networks.

Poor:

- swamps;
- dense forests;
- bridges;
- city interiors;
- mountain passes.

### SellSword

Favored:

- roads;
- towns;
- contract routes;
- defensible camps;
- ransom-safe controlled territory.

Poor:

- terrain that increases recovery cost;
- isolated routes with no contract support;
- swamps and mountains that increase supply strain.

## Terrain And Resources

Territory resources should connect to terrain.

Examples:

- Forest: timber, game, herbs
- Hills: stone, ore, watch sites
- Plains: grain, horses, open camps
- Swamp: herbs, peat, rare resources, poor movement
- River: fish, trade, crossings
- Mountain: ore, stone, passes
- Urban outskirts: trade, labor, salvage

This supports the design goal that city interiors have limited production while territory matters.

## Player-Facing Terrain UI

The player should see clear terrain summaries.

Example tile panel:

`Forest Road`

- March Speed: `-2%`
- Scout Difficulty: High
- Ambush Risk: High
- Cavalry: Poor
- Rangers: Strong

The UI should avoid exposing every hidden value.

Good visible terms:

- Fast
- Slow
- High Ambush Risk
- Strong Cavalry Ground
- Poor Siege Ground
- Good Scout Cover
- Chokepoint
- Controlled Road

Hidden terms:

- cohesion;
- morale;
- report confidence;
- pursuit conversion;
- panic-loss conversion;
- hidden adjacency graph;
- exact ambush formula.

## First-Pass Terrain Table

| Terrain | March | Scout Difficulty | Ambush Risk | Cavalry | Infantry | Ranged | Siege |
| --- | ---: | --- | --- | --- | --- | --- | --- |
| Road | `+3%` | Low | Low | Good | Normal | Normal | Good |
| Plains | `0%` | Low | Low | Strong | Normal | Normal | Normal |
| Forest | `-5%` | High | High | Poor | Good | Mixed | Poor |
| Hill | `-3%` | Medium | Medium | Mixed | Good | Strong | Mixed |
| Swamp | `-10%` | High | Medium | Very Poor | Poor | Poor | Very Poor |
| River Crossing | `-8%` | Medium | High | Poor | Strong | Good | Poor |
| Bridge | `-4%` | Low | High | Poor | Strong | Good | Poor |
| Mountain Pass | `-12%` | Medium | High | Very Poor | Strong | Mixed | Very Poor |
| Desert / Wasteland | `-6%` | Low | Low | Good | Poor | Mixed | Poor |
| Snow / Frozen | `-8%` | Medium | Medium | Poor | Poor | Mixed | Poor |
| Urban Outskirts | `-5%` | High | High | Poor | Strong | Good | Very Poor |
| Fortified Perimeter | varies | High | Medium | Mixed | Strong | Strong | Strong if prepared |

These are baseline values.

Doctrine, formation tier, commander, weather, scouting, and preparation can modify them.
