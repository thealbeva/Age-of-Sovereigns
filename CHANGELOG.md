# Changelog

This changelog tracks major design and prototype changes for the game.

## 2026-07-16

### Expanded Class Talent Trees

- Added separate expanded talent-tree design documents for all six classes:
  - `KNIGHT_TALENT_TREE.md`
  - `MAN_AT_ARMS_TALENT_TREE.md`
  - `ENGINEER_TALENT_TREE.md`
  - `RANGER_TALENT_TREE.md`
  - `CAVALRY_TALENT_TREE.md`
  - `SELLSWORD_TALENT_TREE.md`
- Expanded the doctrine model so each class has meaningful specialization choices instead of every player in a class becoming identical.
- Established the talent-tree structure as:
  - shared class tree
  - three specialization trees per class
  - separate class and specialization point pools
  - more available talents than spendable points
- Added the principle that class overlap should create different fighting styles rather than duplicate bonuses.
- Added Cavalry as a sixth class, separate from Knight.
- Clarified class identities:
  - Knight: Heavy Infantry and Heavy Cavalry with honor, shock, and command identity
  - Man-At-Arms: Heavy Infantry, Light Infantry, and Pikemen
  - Engineer: siege, walls, traps, breach, and counter-siege
  - Ranger: Scouts, ShortBow, LongBow, and CrossBow
  - Cavalry: Ranged Cavalry, Light Cavalry, and Heavy Cavalry
  - SellSword: cost control, contracts, ransom, recovery, and practical warfare
- Added the design rule that a Knight focused on Heavy Cavalry should feel different from a Cavalry-class player focused on Heavy Cavalry.
- Added the design rule that a Knight focused on Heavy Infantry should feel different from a Man-At-Arms focused on Heavy Infantry.

### Terrain

- Added `TERRAIN_RULES.md`.
- Added movement and combat effects for roads, plains, forests, hills, swamps, crossings, bridges, passes, wasteland, snow, urban outskirts, and fortified perimeters.
- Added examples such as roads giving `+3%` march speed and swamps giving `-10%` march speed.
- Added terrain effects for scouting, watch states, sieges, withdrawals, and class identity.

### Strategic Map

- Added `STRATEGIC_MAP_RULES.md`.
- Replaced normal city-builder teleport/grid assumptions with a node-and-route strategic map.
- Added fixed city anchors, external territory nodes, routes, approach sectors, and roads.
- Added no-teleport rule.
- Added partial siege vs full encirclement:
  - partial siege leaves open routes for direct reinforcement and withdrawal
  - full encirclement blocks direct access and forces perimeter fighting
- Added city sack rules where the capital survives but external territory collapses.
- Added territory states:
  - Controlled
  - Contested
  - Occupied
  - Neutralized
  - Ravaged
  - Rebel/Bandit
  - Shield-Maintenance
- Added normal territory loss outside of city sacks.

### Ravaged Land

- Added rule that any land plot or territory node where battle occurs can become Ravaged.
- Added examples such as cavalry fighting through farmland or open plains damaging that territory.
- Added ravage severity:
  - Light
  - Moderate
  - Severe
  - Devastated
- Added repair requirements using resources, labor, time, engineers, protected access, and route control.
- Added repeated-battle escalation where repeatedly fought-over land becomes harder to repair.

### Open Balancing Questions

- Final repair costs for ravaged land by terrain and severity.
- Final talent counts, point budgets, and row gates for every class and specialization.
- Final map scale, node density, travel times, and resource output rates.

## 2026-07-15

### Core Direction

- Established the game as a fair-play medieval alliance war game with no pay-to-win power sales.
- Defined monetization around low-cost convenience, premium reminders, and additional shield inventory rather than combat strength.
- Set the design goal that wars should change the world map, not only produce battle reports.

### Shields And Monetization

- Added free daily Peace Shields that can be saved if unused.
- Added premium reminder/scheduling concept for `$0.99/month`.
- Added paid shield packs as additional inventory, separate from free shields:
  - `16 x 2-hour` shields for `$0.99`
  - `8 x 8-hour` shields for `$1.99`
  - `4 x 24-hour` shields for `$2.99`
  - `2 x 72-hour` shields for `$3.99`
  - `1 x 7-day` shield for `$4.99`
  - `1 x 14-day` shield for `$9.99`
- Added Divine Wrath for breaking a shield:
  - shield lockout equal to `150%` of the broken shield duration
  - `-10%` attack
  - `-10%` defense
  - `+5%` permanent-loss share
  - server announcement
- Added Divine Intervention for shielding during active combat:
  - active combat ends immediately
  - permanent losses from the interrupted engagement convert to wounded for both sides
  - healing is `10%` slower due to hospital overload
  - server announcement
- Added two-step confirmation before shield-breaking actions, including a short delay before final acceptance.

### Formations

- Replaced individual troop stacks with persistent formations such as companies, patrols, lances, and siege crews.
- Added formation identity concepts:
  - name
  - tier
  - experience
  - morale
  - strength
  - casualties
  - battle honors
  - history
- Added persistent veteran progression where formations keep identity and experience through upgrades.
- Added green replacement logic so a damaged veteran formation rebuilt with fresh soldiers is weaker than a fully seasoned formation.
- Added reconstitution concept for formations reduced to `0` soldiers.
- Limited attacking marches and field battles to `5` selected troop types.

### Troops

- Added troop families and Tier `I-X` progression:
  - Scouts/Rangers
  - Militia
  - Light Infantry
  - Heavy Infantry
  - Pikemen
  - Light Cavalry
  - Heavy Cavalry
  - Ranged Cavalry
  - Ranged
  - ShortBow
  - LongBow
  - CrossBow
  - Battering Ram
  - Trebuchet
  - Catapult
- Added formation-size assumptions for each unit type instead of massive anonymous troop counts.
- Added the rule that new formations train at Tier `I` and advance through experience.
- Added PvE experience sources for ruins and monsters, with PvP intended as the main source of serious formation experience.

### Combat

- Established combat as formation-driven rather than simple attack/defense stat comparison.
- Added pre-battle formation setup.
- Added up to two selectable tactics per force.
- Added attacker and defender morale/debuff effects after failed or successful attacks.
- Added alliance-wide offensive debuffs when an alliance member fails an attack.
- Added the principle that fresh Tier `X` formations should not automatically outperform near-promoted veteran Tier `IX` formations.
- Added visible stats and hidden internal stats:
  - visible examples: attack, defense, health, march speed, charge damage
  - hidden examples: cohesion, morale drift, handling, decisiveness

### Siege

- Added siege phase distinction:
  - before breach, walls, gates, towers, ranged troops, scouts, and defensive siege matter most
  - infantry and heavy infantry do not fully engage until breach or sally
- Added sally-forth concept for defenders who choose to open the gates and fight outside.
- Added field reinforcement battles around besieged cities.
- Added Fighting Withdrawal for garrisoned reinforcements.
- Clarified that Fighting Withdrawal is defensive movement, not an offensive redirect.
- Added rule that shielded withdrawing forces receive Divine Intervention if they break free through an interrupted final engagement.

### Player Classes

- Added six player classes:
  - Knight
  - Man-At-Arms
  - Engineer
  - Ranger
  - Cavalry
  - SellSword
- Added monthly class reset concept.
- Added rule that changing class resets research in the new class from zero.
- Clarified that classes change fighting style and specialization rather than hard-locking troop access.

### Knight Talent Prototype

- Added `knight-talent-ui.html` as a playable talent-tree mockup.
- Added separate Knight class points and specialization points.
- Added Shock, Retinue, and Honor specialization tabs.
- Added click-to-inspect behavior.
- Added double-click to spend a point.
- Added right-click to refund a point.
- Added locked row progression.
- Added prerequisite pathing so deeper talents require connected previous talents.
- Reworked connector lines so they attach to actual talent nodes instead of floating decoratively.
- Adjusted visible talent text to show familiar stats while keeping unusual simulation values hidden.

### Scouting

- Added quick scout and infiltration scout concepts.
- Added scout tier as the driver of report quality.
- Added Ranger misdirection when defending scouts are already present.
- Added Watch State concept.
- Added heightened alert state for players in alliances at war.
- Added capture/ransom possibility for some discovered scouts.
- Added class differences for scout treatment:
  - Rangers mislead reports
  - SellSwords reduce ransom costs
  - Knights and Man-At-Arms are more likely to kill captured scouts

### Simulator

- Added or continued the combat simulator prototype under `combat-simulator`.
- Added troop stat and combat model files.
- Added simulator UI files for inspecting and tuning combat behavior.

### Open Balancing Questions

- Final XP curve for Tier `I-X` formation advancement.
- Exact PvE XP values for ruins, monsters, and events.
- Final formulas for morale, cohesion, handling, fatigue, and replacement quality.
