# Core Design

## Pillars

- No pay-to-win. Money never buys combat power, speed, resources, troops, recovery, march strength, alliance advantage, or event ranking.
- Armies are persistent formations, not disposable soldier counts.
- Wars are alliance operations. A single player can damage a city, but breaking a defended city requires coordinated armies, siege, field control, and timing.
- Losses matter, but should not erase months of play from one missed login.
- Timers pace decisions rather than create pressure to spend money.
- Players are allowed to take risky, inconvenient, or dishonorable actions. The world records what happened, and other players decide what those actions mean.

Core principle:

`The game should rarely prevent political choices. It should make those choices visible, costly, and memorable.`

## Monetization

The only planned paid feature is a low-cost premium reminder service.

- Price: `$0.99/month`
- Paid users are reminded on app close to use an available Peace Shield or enter Vacation Mode.
- Free users can use the same shields, but are not prompted on close.
- Paid users do not receive stronger shields, extra shields, faster renewal, combat buffs, resources, speedups, VIP bonuses, or recovery advantages.

## Shields

Peace Shields are primarily an absence and protection system, not a source of combat power.

All players receive access to the same baseline Peace Shield:

- Same protection
- Same duration
- Same renewal rules
- Same restrictions
- Same consequences for breaking it

Premium users do not receive stronger baseline shields. Premium provides convenience:

- App-close reminder when an available shield can be used
- Optional scheduled shield activation while offline
- Player-selected preferred activation time
- Randomized activation within roughly `+/-15 minutes` of that preferred time

Example: if a player schedules their Peace Shield for `9:00 PM`, and an eligible shield is available, the server may activate it between roughly `8:45 PM` and `9:15 PM`.

Scheduled activation does not create a shield if none is available. If the player has no eligible shield, scheduled activation fails and the player is notified.

### Peace Shield

- Duration: `8 hours`
- Renewal: once every `24 hours`
- Free and premium users both receive access.
- If the free daily shield is not used, it does not disappear. It is saved in the player's shield inventory.
- Free shields can accumulate over time.
- Purchased shields are additional inventory on top of free/earned shields.
- If a shield expires naturally, the next free shield arrives on the normal renewal.
- If broken early, the remaining time is lost and the next daily shield is forfeited.
- Breaking actions include scouting, attacking, joining attacks, reinforcing hostile field actions, or other aggressive war actions.

### Purchasable Shield Packs

Additional Peace Shields may be sold in low-cost packs, roughly `$0.99-$9.99`.

Planned packs:

- `16 x 2-hour Peace Shields` for `$0.99`
- `8 x 8-hour Peace Shields` for `$1.99`
- `4 x 24-hour Peace Shields` for `$2.99`
- `2 x 72-hour Peace Shields` for `$3.99`
- `1 x 7-day Peace Shield` for `$4.99`
- `1 x 14-day Peace Shield` for `$9.99`

The intended pricing target is roughly `$0.030/hour` of protection, with small rounding differences by pack size.

Purchased shields provide additional absence protection, but do not provide:

- Combat bonuses
- Increased attack or defense
- Stronger walls
- Additional troops
- Faster training
- Faster formation recovery
- Faster healing
- Faster construction
- Faster research
- Resources
- Increased gathering output
- Better scouting
- Improved battle results
- Offensive advantages

All shields follow the same restrictions whether earned, free, or purchased.

Longer shields are not automatically better. Protection limits active participation and pauses gathering, so players should use the shortest shield that covers the real-world absence.

### Shield Restrictions

While protected by a Peace Shield, a player cannot actively project military or economic power into contested space.

Shielded players cannot:

- Scout hostile players, armies, or cities
- Attack
- Join attacks
- Begin or join offensive rallies
- Conduct offensive sieges
- Send new reinforcements into an active field battle
- Send new reinforcements through an active siege
- Intervene in an ongoing contested engagement
- Attack or claim contested resource nodes
- Attack or claim contested goods
- Participate in hostile field actions
- Capture hostile territory

Guiding rule:

`Protection is allowed. Protected power projection is not.`

### Gathering While Shielded

When a Peace Shield activates, the player's deployed gathering formations also become protected.

However:

- Gathering immediately stops
- No additional resources are collected while protected
- Formations retain resources already gathered before shield activation
- Protected formations cannot continue extracting resources while immune to attack
- The player must leave protection before resuming active gathering

Shielding affects external territory production, not the city's limited internal economy.

Internal city resource nodes continue functioning while shielded, but internal production is intentionally limited. A city may have at most roughly `3` of each internal resource node type, and those internal nodes cap around Tier `V` or Tier `VII`. This provides baseline survival and slow recovery, not a full war economy.

External territory, owned land, and map-based resource production drop from full production to a protected maintenance mode while shielded:

- Enough production to maintain current troops and obligations
- Plus roughly `30%` additional surplus over maintenance
- No full territorial surplus
- No protected high-output economic growth
- No active gathering or contested extraction

Design principle:

`The city can sustain a kingdom. The land grows it.`

### Breaking A Shield: Divine Wrath

A player may voluntarily break an active Peace Shield to perform an offensive or contested action.

Breaking a shield through offensive action triggers `Divine Wrath`.

The player called for sanctuary, then broke it to spill blood.

Divine Wrath creates:

- No-shield lockout equal to `150%` of the shield's full listed duration, not its remaining duration
- `-10%` attack during the lockout
- `-10%` defense during the lockout
- `+5%` permanent-loss share for the shield breaker during the lockout

Examples:

- Break a `2-hour shield` -> Divine Wrath for `3 hours`
- Break an `8-hour shield` -> Divine Wrath for `12 hours`
- Break a `24-hour shield` -> Divine Wrath for `36 hours`
- Break a `3-day shield` -> Divine Wrath for `108 hours` / `4.5 days`
- Break a `7-day shield` -> Divine Wrath for `10.5 days`
- Break a `14-day shield` -> Divine Wrath for `21 days`

The lockout uses the shield's original listed duration even if the shield was almost finished. This prevents cycling between protected and offensive states.

Divine Wrath also creates a server announcement.

Example:

`DIVINE WRATH: [Kingdom Name] has broken sanctuary to spill blood. Their armies suffer Divine Wrath for [duration].`

### Shield Break Confirmation

Players must pass two confirmations before taking an action that breaks an active Peace Shield.

First confirmation:

- Warns that the selected action will break the Peace Shield
- States that Divine Wrath will apply
- Lists Divine Wrath penalties:
  - No-shield lockout for `150%` of the shield's listed duration
  - `-10%` attack
  - `-10%` defense
  - `+5%` permanent-loss share
- Acceptance button is disabled for `3-5 seconds`

Second confirmation:

- Requires the player to confirm they understand they will be unable to shield again for the exact calculated duration
- Displays the duration explicitly, such as `12 hours`, `36 hours`, or `10.5 days`
- Acceptance button is disabled for `3-5 seconds`

This confirmation flow applies to offensive or contested actions that would break sanctuary. It is meant to prevent accidental Divine Wrath from a misclick.

### Shield Activation During Combat

A Peace Shield may activate while a battle or siege involving the protected kingdom is already underway.

When this occurs:

- Combat immediately concludes at its current state
- Completed combat ticks remain final
- Casualties, wounded troops, wall damage, gate damage, destroyed defenses, breach progress, morale changes, formation XP, formation history, and tactical outcomes remain
- Permanent losses from the active engagement are converted to wounded for both attacker and defender
- No previous damage or consequences are reversed
- No additional combat occurs after shield activation
- Attacking forces disengage from the newly protected kingdom
- Healing speed is reduced by `10%` after intervention because hospitals and recovery systems are overloaded by the sudden mass of wounded

The Peace Shield prevents future combat. Divine Intervention does not reverse that the battle happened; it removes permanent death from the interrupted engagement and leaves the rest of the consequences intact. The gods are not biased, so attacker and defender permanent losses from that engagement are both converted to wounded.

In-world conclusion reason:

`Peace Shield - Divine Intervention`

Both sides receive the same conclusion reason and access to the final battle report. The report should make clear that combat ended because of a shield rather than a server error, disconnection, retreat, or rollback.

Divine Intervention also creates a server announcement.

Example:

`DIVINE INTERVENTION: A divine veil has descended over [Kingdom Name]. The active battle has ended by sanctuary. Permanent losses from the interrupted engagement have been converted to wounded.`

### Vacation Mode

- Duration: `14 days`
- Renewal: once every `6 months`
- Free and premium users both receive access.
- While active, the player cannot scout, attack, reinforce, gather, or participate in field actions.
- If canceled early, the remaining time is lost and the player waits until the next 6-month renewal.

## Timers

- Building timers cap at roughly `32 hours`.
- Research timers cap at roughly `48 hours`.
- Troop/formation training should usually complete in `6-9 hours`.
- Healing should generally be faster than training replacements.
- No paid speedups exist.

March time and battle duration are separate systems.

Detailed terrain and route rules live in `TERRAIN_RULES.md`.

Detailed strategic map, territory, encirclement, sack, and ravaged-land rules live in `STRATEGIC_MAP_RULES.md`.

- March time is travel to the target.
- Battle duration is the engagement itself.
- A battle may continue over a real chunk of time after armies make contact.
- Mid-fight arrivals are visible events unless concealed by scouting, Ranger deception, terrain, or ambush conditions.
- Reinforcements should usually be spotted before contact through dust, banners, scouts, watch reports, or field observation.

This keeps battles from feeling like instant spreadsheet comparisons while still avoiding real-time micromanagement.

## Research And Doctrine Trees

Detailed class identity notes live in `PLAYER_CLASSES.md`.

Research is not intended to become a universal checklist where every player eventually owns every bonus. Each player chooses one doctrine tree:

- Knight
- Cavalry
- SellSword
- Man-At-Arms
- Ranger
- Engineer

Once a tree is chosen, the player is locked into that tree. The player may reset their chosen tree once per month. Resetting allows choosing a different tree, but research progress in the new tree starts from zero.

The goal is role identity:

- Knight players specialize in heavy cavalry, heavy infantry, honor, morale shock, decisive charges, and post-breach offensive pressure.
- Cavalry players specialize in ranged cavalry, light cavalry, heavy cavalry, mounted mobility, harassment, kiting, pursuit, route control, and rout conversion.
- SellSword players specialize in reduced upkeep, reduced training/refit costs, cheaper recovery, contracts, ransom, dirty tricks, and adaptable war logistics.
- Man-At-Arms players specialize in infantry discipline, pikes, breach fighting, garrisons, and holding lines.
- Ranger players specialize in scouts, ShortBow, LongBow, CrossBow, archery, ambushes, ruins exploration, movement, and map control.
- Engineer players specialize in siege engines, walls, counter-siege, repairs, traps, and breach math.

Doctrine affects performance, not access. No troop class is doctrine-locked. A Knight player can still field light cavalry, scouts, archers, infantry, or siege; they simply do not receive the same doctrine bonuses another specialist would.

Doctrine should also define which battle phase a player is best at winning:

- Knight: decisive shock, charge timing, and post-breach offensive pressure.
- Cavalry: the chase, harassment, pursuit, interception, and control of open ground.
- SellSword: flexible contracts, mixed-force adaptation, ransom, recovery, and dirty logistics.
- Man-At-Arms: line discipline, pikes, holding actions, breach defense, and garrison reliability.
- Ranger: intelligence, detection, deception, ambushes, scout uncertainty, and ranged support.
- Engineer: siege engines, walls, traps, repairs, counter-siege, and breach math.

Doctrine boundaries:

- Cavalry is its own doctrine/class identity, not a replacement for SellSword.
- Knight uses heavy cavalry and heavy infantry for shock, honor, and decisive commitment.
- Cavalry uses ranged cavalry, light cavalry, and heavy cavalry for speed, pursuit, harassment, interception, and field control.
- Ranger uses scouts and foot archers for detection, deception, ambushes, ruins, and ranged field pressure.
- Man-At-Arms uses heavy infantry, light infantry, and pikemen for disciplined line fighting, holding actions, and breach defense.
- Engineer uses battering rams, trebuchets, catapults, walls, traps, repairs, and counter-siege systems.
- SellSword keeps the mercenary identity: reduced costs, recovery, ransom, opportunism, flexible contracts, and lower cost of changing battlefield commitments.
- Heavy infantry overlap between Knight and Man-At-Arms is contextual. Knight uses heavy infantry for offensive shock after breach, while Man-At-Arms uses heavy infantry for holding, defense, and disciplined line work.

Research nodes can include small granular bonuses as well as larger tactical unlocks. Small bonuses should usually be modest, often around `1%`, so research matters over time without letting raw stats overwhelm formation composition and alliance coordination.

Example granular nodes:

- `+1%` wall damage reduction
- `+1%` counter-siege accuracy
- `+1%` ranged accuracy
- `+1%` breach resistance
- `+1%` cavalry charge impact
- `+1%` infantry cohesion
- `+1%` scout detection
- `+1%` formation recovery speed
- `+1%` field movement
- `+1%` siege setup speed

Example tactical unlocks:

- Knight: heavy cavalry lances gain a first-contact charge bonus in field battles.
- Cavalry: ranged cavalry and light cavalry gain stronger pursuit, interception, harassment, and disengagement options on open ground.
- SellSword: formations receive lower upkeep, cheaper refit/replacement costs, lower ransom costs, and reduced morale penalties after a failed attack.
- Man-At-Arms: heavy infantry and pikemen reduce casualties during breach defense.
- Ranger: scouts and foot archers improve detection, deception resistance, sally preparation warnings, and hidden field reinforcement detection.
- Engineer: trebuchets and catapults generate more breach score against walls.

Research should support alliance roles. A strong alliance wants multiple doctrines represented rather than every player pursuing the same universal build.

### Doctrine Matrix V1

Doctrine should change how a player uses formations, not simply make their numbers bigger.

The same formation class can appear in more than one doctrine, but doctrine changes the fighting style.

Example:

- Knight Heavy Cavalry wins through shock, morale pressure, and decisive commitment.
- Cavalry Heavy Cavalry wins through timing, mobility, pursuit, interception, and control of escape routes.
- Knight Heavy Infantry pushes through a breach and breaks enemy will.
- Man-At-Arms Heavy Infantry holds formation, absorbs pressure, and wins through discipline.

Doctrine bonuses should usually be conditional. The best bonuses apply when the player is using the doctrine in its intended role.

#### Knight

Core identity:

- Noble shock force
- Heavy cavalry
- Heavy infantry
- Honor, morale pressure, and decisive commitment
- Best at breaking wavering enemies or exploiting a breach

Primary formation focus:

- Heavy Cavalry
- Heavy Infantry

Battle phases:

- Field charge
- Breach follow-through
- Decisive counterattack
- Morale collapse exploitation

Strengths:

- High first-contact impact
- Strong morale damage
- Better performance when committing to a decisive engagement
- Better post-breach offensive pressure
- Better prestige/title interactions from honorable or decisive victories

Weaknesses:

- Expensive to maintain and refit
- Poor at prolonged harassment
- Poor at cheap recovery
- Vulnerable to disciplined pikes and prepared defensive lines
- Suffers more if forced into repeated low-value skirmishes

Example granular nodes:

- `+1%` heavy cavalry charge impact
- `+1%` heavy infantry shock attack after breach
- `+1%` morale damage on first contact
- `+1%` cohesion while attacking through a breach
- `-1%` morale loss after honorable victory

Example tactical unlocks:

- `Lance Break`: Heavy Cavalry gains increased first-contact morale damage, but suffers higher losses if countered by prepared pikes.
- `Noble Retinue`: Heavy Infantry gains offensive pressure after a wall or gate breach.
- `Oath Charge`: A committed charge cannot be easily canceled, but deals higher morale damage if it lands cleanly.

#### Cavalry

Core identity:

- Mobility doctrine
- Ranged cavalry
- Light cavalry
- Heavy cavalry used as mobile force rather than noble shock alone
- Best at controlling space, pursuit, interception, and escape routes

Primary formation focus:

- Ranged Cavalry
- Light Cavalry
- Heavy Cavalry

Battle phases:

- Open field
- Harassment
- Pursuit
- Interception
- Fighting Withdrawal pressure
- Siege perimeter control

Strengths:

- Fastest operational movement
- Better pursuit and rout conversion
- Better disengagement and repositioning
- Stronger harassment against slow formations
- Stronger interception against reinforcements, scouts, and exposed siege support

Weaknesses:

- Poor wall pressure
- Weaker in dense breach fighting
- Vulnerable to pikes, terrain traps, and prepared spear screens
- Less effective in swamps, forests, tight passes, and urban fighting
- Harassment creates fatigue if overused

Example granular nodes:

- `+1%` march speed on open terrain
- `+1%` pursuit effectiveness
- `+1%` disengagement success
- `+1%` ranged cavalry harassment accuracy
- `-1%` fatigue from long mounted operations

Example tactical unlocks:

- `Harassing Circle`: Ranged Cavalry reduces enemy cohesion over time, but deals low direct casualties.
- `Cut Off Retreat`: Cavalry increases enemy permanent-loss and capture risk during routs.
- `Screen The Road`: Cavalry improves interception chances against reinforcements moving through nearby terrain.

#### Man-At-Arms

Core identity:

- Professional line doctrine
- Heavy infantry
- Light infantry
- Pikemen
- Discipline, cohesion, and holding ground
- Best at surviving pressure and controlling the line

Primary formation focus:

- Heavy Infantry
- Light Infantry
- Pikemen

Battle phases:

- Defensive field line
- Breach defense
- Gate holding
- Anti-cavalry preparation
- Attrition fighting

Strengths:

- High cohesion under pressure
- Strong anti-cavalry defense through pikes
- Better casualty control while holding
- Better defensive morale stability
- Strongest infantry doctrine for breach defense

Weaknesses:

- Lower pursuit
- Lower operational speed
- Less explosive than Knight
- Needs positioning and preparation to shine
- Can be worn down by ranged pressure and siege if unsupported

Example granular nodes:

- `+1%` infantry cohesion
- `+1%` pike anti-cavalry impact
- `+1%` breach defense
- `-1%` morale loss while holding position
- `-1%` permanent-loss share while defending a breach

Example tactical unlocks:

- `Set Pikes`: Pikemen greatly reduce cavalry charge impact while stationary, but reposition more slowly.
- `Hold The Line`: Infantry gains cohesion and morale resistance while not pursuing.
- `Shielded Advance`: Light and Heavy Infantry reduce ranged losses while advancing slowly.

#### Ranger

Core identity:

- Intelligence and ranged fieldcraft doctrine
- Scouts
- ShortBow
- LongBow
- CrossBow
- Ambush, deception, detection, ruins, and terrain control

Primary formation focus:

- Scouts/Rangers
- ShortBow
- LongBow
- CrossBow

Battle phases:

- Scouting
- Counter-scouting
- Ambush
- Defensive warning
- Pre-battle information
- Ranged field support

Strengths:

- Better scout detail and reliability
- Better deception and false reporting
- Better ambush setup
- Better detection of sally preparations and hidden reinforcements
- Better ranged performance from prepared positions

Weaknesses:

- Lower direct wall pressure
- Weaker in prolonged melee
- Vulnerable if cavalry reaches exposed ranged formations
- Requires information advantage to reach full value
- Poor at brute-force assaults

Example granular nodes:

- `+1%` scout detection
- `+1%` scout stealth
- `+1%` deception strength
- `+1%` ranged accuracy from prepared terrain
- `-1%` scout capture chance during infiltration

Example tactical unlocks:

- `False Camp`: Ranger counter-scouts can distort enemy quick-scout reports.
- `Prepared Ambush`: Ranged formations gain first-volley impact if the enemy enters poorly scouted terrain.
- `Silent Watch`: Scouts provide earlier warning of incoming reinforcements, sally preparations, or Fighting Withdrawal attempts.

#### Engineer

Core identity:

- Siege and fortification doctrine
- Battering rams
- Trebuchets
- Catapults
- Walls, traps, repairs, breach math, and counter-siege

Primary formation focus:

- Battering Ram
- Trebuchet
- Catapult
- Wall systems
- Traps
- Repairs
- Defensive siege

Battle phases:

- Pre-breach siege
- Counter-siege
- Wall defense
- Trap preparation
- Gate pressure
- Repair windows

Strengths:

- Only doctrine that directly improves breach math
- Better wall damage
- Better counter-siege accuracy
- Better defensive repairs
- Better traps and obstacle systems
- Strongest doctrine for making or preventing breaches

Weaknesses:

- Siege engines are slow
- Siege requires protection
- Poor in open field without escort
- Vulnerable to cavalry and ranger disruption
- Expensive losses if siege crews are caught exposed

Example granular nodes:

- `+1%` wall damage
- `+1%` breach score generation
- `+1%` counter-siege accuracy
- `+1%` trap effectiveness
- `+1%` emergency repair rate

Example tactical unlocks:

- `Focused Bombardment`: Siege engines gain breach pressure against one wall section, but are easier to disrupt.
- `Counter-Battery Survey`: Defensive siege improves accuracy against enemy siege engines.
- `Rapid Bracing`: Engineers temporarily slow breach progress through emergency repairs.

#### SellSword

Core identity:

- Mercenary economy doctrine
- Reduced costs
- Contracts
- Ransom
- Recovery
- Flexible war logistics
- Best at staying solvent and useful through repeated conflict

Primary formation focus:

- No exclusive combat formation focus
- Mixed formations
- Replacements
- Recovery systems
- Contract and ransom systems

Battle phases:

- Campaign sustainment
- Recovery after losses
- Opportunistic fighting
- Contract defense
- Ransom and prisoner systems
- Flexible reinforcement

Strengths:

- Lower upkeep
- Cheaper training and refits
- Cheaper replacement of casualties
- Better ransom prices
- Better recovery from failed attacks
- Better use of mixed formations without strict doctrine purity

Weaknesses:

- Weaker peak combat bonuses
- Less specialized than other doctrines
- May struggle against elite specialists in their favored phase
- Reputation may be politically mixed
- Economic advantages must not become pay-to-win-like power scaling

Example granular nodes:

- `-1%` formation upkeep
- `-1%` refit cost
- `-1%` casualty replacement cost
- `-1%` ransom paid for captured scouts or formations
- `+1%` mixed-formation morale recovery

Example tactical unlocks:

- `Contract Guard`: Formations defending under a contract suffer reduced morale loss.
- `Hard Bargain`: Captured scouts and prisoners cost less to ransom back.
- `Paid To Survive`: Formations are slightly better at avoiding destruction after a failed attack, but gain less honor/title weight from heroic stands.

### Doctrine Balance Rules

Doctrine should create identity without creating mandatory choices.

Rules:

- No doctrine can do everything.
- No troop class is fully locked behind doctrine.
- Overlapping troop classes must feel different by doctrine.
- Combat doctrines gain power in their favored phase, not everywhere.
- SellSword saves cost and improves recovery, but should not produce the strongest raw combat output.
- Engineer owns breach math, but cannot protect siege alone.
- Ranger owns information, but cannot brute-force cities.
- Cavalry owns movement, pursuit, and interception, but cannot ignore terrain or pikes.
- Man-At-Arms owns disciplined holding, but should not chase well.
- Knight owns decisive shock, but pays for failed commitment.

Alliance design goal:

`A healthy alliance wants every doctrine represented.`

## Scouting And Counter-Scouting

Scouting is a core war system. Players should not only ask "how many troops are there?" They should ask how reliable the report is.

Scout tier influences how much information can be discovered. Higher-tier scouts are better at identifying formation quality, current-tier mastery, veteran-rank percentage, morale, tactics, and deception.

There are two baseline scout mission types:

- Quick Scout: fast and safer. Returns rough ranges of individual soldier counts, not exact formation counts. It may show "1,000-1,500 heavy infantry soldiers" rather than "14 Heavy Infantry Companies." It gives limited readiness detail.
- Infiltration: slower and riskier. Scouts attempt to enter deeper watch zones and gather detailed information such as tier mastery, veteran-rank percentage, unit readiness, morale, defensive tactics, recent refits, and wall condition. Infiltration has a chance to lose scouts to enemy scouts/rangers.

A scout report can reveal, depending on scout quality:

- Formation types
- Formation names
- Strength
- Tier
- Current-tier mastery
- Veteran-rank percentage
- Morale
- Recently refit status
- Wall condition
- Defensive tactics
- Nearby field reinforcements
- Sally readiness
- Siege/counter-siege readiness

Low-quality scouting may only show paper information, such as troop type and tier. High-quality scouting reveals readiness, quality, and vulnerabilities.

Ranger doctrine enables counter-scouting and deception. If a Ranger player's scouts are stationed in their own city or an allied city before an enemy scout arrives, they can interfere with the incoming scout report based on Ranger skill-tree investment.

Possible Ranger deception effects:

- Hide exact current-tier mastery.
- Hide veteran-rank percentage.
- Overstate or understate formation readiness.
- Mask recently refit formations.
- Conceal a sally-ready force.
- Conceal or exaggerate wall condition.
- Hide selected defensive tactics.
- Create false confidence by showing paper tier without readiness warnings.

Counter-scouting should not be absolute by default. It should compare:

- Attacker scout quality
- Attacker scout tier
- Scout mission type
- Defender Ranger doctrine
- Defender scout/ranger formations present
- City or allied-city preparation time
- Watchtower or signal structure level
- Recent scout activity and fatigue

A strong scout report should clearly label uncertainty. Example:

`Tier IX Heavy Infantry Company detected. Tier mastery unknown. Veteran ranks may be masked. Report reliability: contested.`

This creates a real role for Rangers. They do not merely gather information; they can shape what the enemy thinks they know.

### Watch States

Cities and important field positions have a watch state. The watch state represents how alert the guards, scouts, patrols, signal posts, and allied observers are.

Baseline watch states:

- Unaware: normal peacetime watch. Quick scouts are easy, infiltration is least risky.
- Suspicious: recent activity has raised concern. Infiltration takes longer and has higher detection risk.
- Alert: active watch rotations, tighter gate control, more patrols, and prepared counter-scouts.
- Locked Down: wartime security. Infiltration is slow, dangerous, and likely contested. Good reports are still possible, but expensive.

Watch state affects:

- Quick scout on-site time
- Infiltration on-site time
- Scout report reliability
- Ranger deception effectiveness
- Scout capture or death chance
- Whether defensive tactics and recent refits can be identified

Suggested timing after scouts arrive:

| Watch State | Quick Scout | Infiltration |
| --- | ---: | ---: |
| Unaware | 10-20 seconds | 45-75 minutes |
| Suspicious | 15-30 seconds | 60-100 minutes |
| Alert | 20-45 seconds | 90-150 minutes |
| Locked Down | 30-60 seconds | 2-4 hours |

Watch state can rise from:

- Repeated scouting
- Failed or detected infiltration
- Nearby hostile marches
- Recent attacks
- Alliance war declarations
- Being in an alliance that is currently at war
- Ranger or Man-At-Arms security orders
- Watchtower/signal upgrades

If a player is in an alliance that is currently at war, their city should have a minimum heightened watch state. Suggested floor:

- Not at war: can decay to `Unaware`
- Alliance at war: minimum `Suspicious`
- Directly targeted recently or near hostile marches: minimum `Alert`
- Under active siege or repeated infiltration attempts: can reach `Locked Down`

Watch state should decay over time if no further suspicious activity happens. This creates a scouting tradeoff: repeated quick scouts keep information fresh but make deeper infiltration harder.

Watch state can change while a scout mission is already underway. If the target shifts upward mid-scout cycle, the mission should be affected at the point the shift occurs.

Examples:

- A city moves from `Suspicious` to `Alert` because a hostile march is spotted while infiltration is underway.
- A target enters `Locked Down` because another scout was captured before the current infiltration completes.
- Alliance war state begins while scouts are already traveling.

Mid-mission watch shifts can:

- Increase remaining on-site time
- Reduce final report reliability
- Increase detection/capture risk
- Cause the report to be marked `Changed During Mission`
- Make some details stale or contradictory
- Force a partial report if scouts abort early

The scout report should preserve both the starting watch state and final watch state so players understand why the result changed.

### Report Freshness

Scout reports should include a timestamp and freshness state. Intelligence is not permanent truth.

Suggested report freshness:

- Quick Scout: accurate for fast-changing troop presence for roughly `5-15 minutes`.
- Infiltration: structure, wall, doctrine, and readiness details may remain useful for `30-120 minutes`, but troop positions and field reinforcements can stale faster.
- Reports should be labeled `Fresh`, `Aging`, `Stale`, or `Obsolete`.

Freshness matters because a detailed infiltration report may arrive after the target has moved formations, changed tactics, raised watch state, or refit units.

### Scout Trails

Scouting should leave traces depending on scout tier, mission type, watch state, and counter-scouting.

Possible defender notifications:

- No trace found.
- Unidentified tracks found near the road.
- Scout sighted near outer watch.
- Infiltration attempt detected.
- Scout captured.
- Scout identified as belonging to a kingdom or alliance.

This lets defenders know they are being watched without always knowing by whom.

### Captured Scouts, Ransom, And Morale

Infiltration can lead to partial or full scout capture.

Possible outcomes:

- Clean Success: full report, scouts return.
- Partial Success: useful report, some uncertainty.
- Detected, Escaped: limited report, minor losses or morale damage.
- Partial Capture: some scouts captured, formation returns weakened.
- Full Capture: scout formation does not return until ransomed, exchanged, rescued, released, or otherwise resolved.
- Wiped Out: scout formation is destroyed.

Captured scouts can be ransomed back to the original kingdom or alliance.

Capture affects the scout formation:

- Strength loss
- Morale damage
- Temporary `Shaken` or `Ransomed Survivors` status
- Infiltration cooldown
- Potential veteran-rank loss if replacements are used
- History entry such as `Captured at Blackvale`

Ransomed scouts may restore strength but should not instantly restore morale. They survived, but the formation remembers the capture.

Doctrine influence:

- Ranger: more likely to detect, mislead, and capture scouts alive.
- SellSword: more likely to ransom, broker exchanges, and reduce ransom costs through talents.
- Knight: more likely to execute or publicly punish spies, creating intimidation and diplomatic consequences.
- Man-At-Arms: more likely to kill scouts during disciplined security sweeps.
- Engineer: more likely to trap, injure, delay, or capture scouts through alarms, locked passages, false corridors, and mechanical defenses.

### Decoys And False Signals

Rangers and Engineers can create false or misleading signals.

Possible decoys:

- Dummy siege engines
- Covered troop yards
- False campfires
- Fake road tracks
- Hidden veteran formations
- Inflated wall activity
- Concealed recent refits
- Decoy supply wagons

Scout reports should indicate uncertainty when decoys may be present, especially under contested reports.

### Alliance Intelligence Sharing

Scout reports can be shared with alliance members.

Shared reports should preserve:

- Timestamp
- Scout mission type
- Report reliability
- Watch state at time of report
- Whether Ranger interference was detected
- Freshness state
- Known uncertainty

Alliance leaders may pin or annotate reports during wars. This supports coordinated siege planning and avoids everyone repeatedly scouting the same target into a higher watch state.

### Scout Formation Stats

Scout/Ranger formations should eventually have specialized stats beyond normal combat stats:

- Stealth: chance to avoid detection.
- Detection: chance to find enemy scouts, decoys, hidden formations, and sally preparations.
- Escape: chance to avoid capture after detection.
- Deception: ability to mislead enemy reports when defending.
- Interrogation Resistance: reduces information leaked if captured.
- Mapcraft: improves travel, route reading, and report freshness.
- Signal Discipline: reduces scout trails and defender notifications.

These stats can be affected by tier, current-tier mastery, veteran-rank percentage, morale, Ranger doctrine, watch state, and mission type.

## Formations

Players do not train huge anonymous troop numbers. They train formations.

Examples:

- `8 Heavy Infantry Companies`
- `3 Heavy Cavalry Lances`
- `2 Trebuchet Crews`
- `1 Scout Patrol`

Each formation should eventually have:

- Name
- Type
- Tier
- Experience
- Veterancy
- Veteran-rank percentage
- Morale
- Strength
- Casualties
- Battle history
- Honors
- Optional commander

New formations are always trained at `Tier I`. Higher tiers are earned by experience, research unlocks, resources, and refit time. A formation keeps its name, history, and veterancy when refit to a higher tier.

Tier is the formation's equipment and doctrine level, not its full battlefield quality. A formation also tracks how many of its current soldiers are veterans versus green replacements. A near-Tier-II formation with intact veteran ranks can outperform a newly refit Tier II formation that has been rebuilt mostly with green replacements.

Formations also track progress inside their current tier. A fresh Tier II formation is not as strong as a Tier II formation that is almost ready to refit into Tier III. The near-Tier-III formation has learned to use its current equipment, drills, and battlefield role more effectively.

Replacement quality affects actual battle values:

- Attack
- Defense
- Health / staying power
- Permanent-loss resistance
- Morale stability

Current-tier mastery affects actual battle values:

- Attack
- Defense
- Health / cohesion
- Siege handling
- Ranged accuracy
- Formation reliability

This means replenishing casualties restores strength, but does not instantly restore battlefield quality. A battered veteran formation may be full again on paper while still fighting worse until its replacement soldiers are seasoned.

## Formation Scale

Current baseline formation sizes:

- Scouts/Rangers: `Patrol of 25`
- Militia: `Company of 100`
- Light Infantry: `Company of 100`
- Heavy Infantry: `Company of 80`
- Pikemen: `Company of 100`
- Ranged Cavalry: `Lance of 35`
- Light Cavalry: `Lance of 40`
- Heavy Cavalry: `Lance of 30`
- Ranged: `Company of 100`
- ShortBow: `Company of 100`
- LongBow: `Company of 80`
- CrossBow: `Company of 60`
- Battering Ram: `Crew of 20`
- Trebuchet: `Crew of 25`
- Catapult: `Crew of 15`

## Troop Classes

Current roster:

- Scouts/Rangers
- Militia
- Light Infantry
- Heavy Infantry
- Pikemen
- Ranged Cavalry
- Light Cavalry
- Heavy Cavalry
- Ranged
- ShortBow
- LongBow
- CrossBow
- Battering Ram
- Trebuchet
- Catapult

All classes support tiers `I-X`.

## March Limits

Attackers can send up to `5 troop types` in a march.

Defensive rules depend on battle type:

- City defense uses what is stationed in the city.
- Open field battles limit both sides to up to `5 troop types`.
- Resource battles limit both sides to up to `5 troop types`.
- If a defender sallies from a city, that sally force is treated as a field army and is limited to up to `5 troop types`.

## Tactical Orders

Combat is not intended to be real-time tactical micro. Players make meaningful decisions before the march launches or before a defense triggers.

Each side can select up to `2 tactics` at the same time. Tactics should create intent and tradeoffs rather than covering every weakness.

Before launching a march, players choose:

- Formations
- Formation composition
- Up to `2` tactics
- Commander
- Doctrine
- Route
- Objective

After commitment, the battle resolves continuously over time rather than as a single instant power comparison. Players do not click abilities every few seconds. Their chosen tactics are the battle plan being executed against changing conditions.

Example attack tactics:

- Shield Wall: infantry protects ranged and siege, reducing losses to protected formations but slowing pressure.
- Spear Screen: pikemen reduce incoming cavalry impact.
- Fast Strike: cavalry attempts to reach exposed ranged or siege formations.
- Bombard Walls: siege prioritizes breach damage over field casualties.
- Suppress Defenders: ranged formations target wall defenders and exposed ranged units.
- Fighting Withdrawal: reduce permanent losses if casualties pass a threshold, but lowers chance to win.

Example defense tactics:

- Hold Walls: wall defenders avoid unnecessary exposure and improve pre-breach defense.
- Counter-Battery: defensive siege targets enemy siege engines.
- Arrow Storm: ranged formations focus exposed attackers before breach.
- Sally Against Siege: open gates if siege is exposed and fight as a field force.
- Preserve Veterans: veteran formations withdraw earlier to avoid destruction.
- Brace For Breach: infantry and pikes prepare for post-breach fighting.

Tactics should interact with formation advantages:

- Pikemen punish cavalry unless cavalry catches an exposed flank.
- Cavalry punishes exposed ranged and siege.
- Crossbows pressure armored infantry.
- Heavy infantry excels in breach fighting.
- Siege damages walls but is vulnerable without escorts.
- Scouts improve detection, targeting, and report quality.

### Event-Driven Command Changes

Major battlefield events can create new command opportunities without turning combat into real-time micromanagement.

Examples of major events:

- A new army reaches the battlefield
- A defending city launches a Sally Forth
- A breach opens
- A gate collapses
- A relief force attacks the siege perimeter
- A Fighting Withdrawal begins
- A formation routs or is destroyed
- Weather, terrain control, or field control changes significantly

When a major event affects a participant, that commander receives a notification and may:

- Keep both current tactics
- Replace one tactic
- Replace both tactics

Combat does not pause while the player decides. Existing tactics remain active until new orders are issued and the communication or reorganization delay completes.

This creates a command rhythm:

1. Choose formations and tactics.
2. Commit the army.
3. Battle resolves continuously.
4. A major battlefield event occurs.
5. Affected commanders are notified.
6. Commanders may revise tactics.
7. New orders propagate after delay.
8. Battle continues under the revised plan.

The goal is strategic decision-making, not reflex clicking.

## City Sieges

City assaults are not simple blob fights.

### Pre-Breach

Before a breach, melee garrison formations do not fully fight across the wall.

Active defense mainly comes from:

- Walls
- Gates
- Towers/bastions
- Scouts/spotters
- Ranged
- ShortBow
- LongBow
- CrossBow
- Defensive catapults/trebuchets

Only siege engines generate meaningful wall and breach damage:

- Battering Ram
- Trebuchet
- Catapult

Knights, cavalry, infantry, pikes, militia, and ordinary ranged formations contribute no meaningful wall pressure before breach.

Only defensive ranged formations and defensive siege engines can act from behind the wall before breach. Melee garrison formations wait until breach or Sally Forth.

This prevents a single player with a large ordinary army from solo-breaking a defended city. Breaking a city structurally requires multiple battlefield roles at once:

- Engineers to create breach pressure
- Cavalry to screen, intercept, and punish exposed forces
- Rangers and scouts to reveal the city and field situation
- Ranged formations to contest wall defenders and exposed troops
- Knights and Man-At-Arms to decide the breach fight

No single doctrine should cover every required siege role.

### Breach

Once walls or gates are breached, the city garrison fully joins.

Important post-breach formations include:

- Militia
- Light Infantry
- Heavy Infantry
- Pikemen
- Ranged support
- Limited cavalry depending on breach/gate conditions

### Sally Forth

Defenders may open the gates and sally into the field.

- The selected sally force is limited to up to `5 troop types`.
- The fight resolves as a field clash.
- This gives defenders agency but risks exposing valuable formations.
- Sally Forth is the main pre-breach moment where melee and cavalry doctrine bonuses matter during a siege.

## Alliance Warfare

Breaking a defended city should require alliance coordination.

Possible roles:

- Screening armies protect siege.
- Siege armies create breach pressure.
- Cavalry armies intercept reinforcements.
- Ranged armies support field control.
- Scouts reveal city composition and field movement.
- Defenders contest the field instead of stacking infinite reinforcements inside the city.

Friendly alliance reinforcements generally deploy to the field around the city, not directly into the city garrison.

### Independent Contingents

A reinforcing army is not added to an allied power total as a faceless stat blob.

Every incoming army retains:

- Owner
- Commander
- Formations
- Formation histories
- Doctrine
- Selected tactics
- Morale
- Readiness
- Casualty record
- Battlefield objective
- Entry route

A reinforcing force enters through a physical route and begins executing its own plan inside the shared battle.

Example:

- Rosewatch defenders use `Hold Walls` and `Counter-Battery`
- An allied cavalry relief force uses `Fast Strike` and `Flank Attack`

The cavalry does not inherit the wall defense plan. It threatens the enemy rear, disrupts siege, pressures exposed ranged formations, and forces the attacker to react.

Multiple contingents may cooperate without becoming one army.

### Open Intervention

An ongoing siege is a physical event in the world. It is not owned exclusively by the original attacker and defender.

Any player capable of reaching the battlefield may attempt to intervene.

They may:

- Support the attacker
- Support the defender
- Attack an existing participant
- Protect a friend
- Honor an informal agreement
- Betray an alliance
- Weaken a rival
- Exploit an exposed army
- Pursue an independent objective

The game does not require every participant to fit into one clean red-versus-blue structure.

Example escalation:

1. Kingdom A attacks Kingdom B.
2. Kingdom C supports A.
3. Kingdom D supports B.
4. Kingdom E attacks C.
5. Kingdom F attacks A without formally supporting B.

Every new participant creates a battlefield event and may give affected commanders a chance to revise tactics.

Guiding rule:

`Nobody owns exclusive rights to a war.`

Open intervention at a siege perimeter is field combat. An outside player does not teleport into the city garrison and does not need city access permissions to fight outside the walls.

An outsider can:

- Attack the besieging screen
- Attack exposed siege support
- Harass relief forces
- Contest field control around the city
- Open pressure that helps a true relief force arrive
- Create a corridor for a Fighting Withdrawal

An outsider cannot directly appear inside the defending city unless they were already garrisoned before the siege began or later physically reaches a valid city entry route after the siege situation changes.

A stranger may not "save" a city directly. They usually weaken, break, distract, or reposition the forces around the siege. That can create the conditions for the city, its allies, or a withdrawing garrison to survive.

This uses ordinary field-battle rules applied to a siege perimeter.

Siege and fortress PvP should be one of the strongest formation XP sources in the game. This gives third parties selfish reasons to intervene:

- XP from fighting exposed screens
- XP from attacking siege support
- XP from defending or disrupting breach operations
- Favorable battles against committed enemies
- Reputation and title opportunities

Sieges should attract attention because they create valuable, risky, time-sensitive battles, not only because people are being noble.

### Opportunity Warfare

Long battles allow smaller forces to matter by arriving at the decisive place and time.

A small cavalry force hitting exposed siege engines during a defender's Sally Forth may matter more than a larger army that arrives too late or attacks the wrong target.

The battle engine should eventually track causal battlefield impact, not only raw damage.

Important questions:

- Did this intervention force enemy formations to reposition?
- Did it expose or protect siege engines?
- Did it change breach pressure?
- Did it shift morale, cohesion, or field control?
- Would the battle probably have ended differently without this intervention?

This is how a player can earn a reputation for saving a city without being the largest army on the field.

### Field Battle Escalation

A siege-perimeter skirmish can snowball into a larger multi-army fight through normal field-combat rules.

Example escalation:

1. A player marches on the besieging screen.
2. The screen owner's allies counter-march to defend.
3. The attacker's allies join the active engagement.
4. Additional third parties commit for XP, loyalty, revenge, reputation, or opportunism.

Joining an already active engagement is not pre-positioning. Normal shield-breaking rules apply.

This uncertainty discourages reckless attacks. A "safe" strike against an exposed screen can become a larger fight as soon as nearby players decide the battle is worth joining.

Expected player behavior:

- Scout before committing
- Bring escorts
- Watch who is active nearby
- Time attacks around march distance
- Consider whether a small opportunity could become a large war

### Alliances Are Agreements

Alliance membership provides cooperation systems, not magical friendly-fire immunity.

Alliances may provide:

- Shared communication
- Shared intelligence
- Reinforcement permissions
- Garrison access
- Coordinated operations
- Alliance ranks
- Political obligations

Alliance members may still attack one another.

The game should warn the player clearly:

`WARNING: ALLIED FORCES. These formations belong to a member of your alliance. Attacking will be permanently recorded as an act of betrayal. Continue?`

The action remains possible because civil wars, political disputes, secret agreements, competing loyalties, retaliation, and betrayal should be playable events.

The game records the action. Players decide what it means.

### Betrayal And Garrisoned Forces

Allied formations garrisoned inside another player's city are already behind the walls.

If political relationships collapse, those troops do not need to conduct a normal external siege. The walls were bypassed through trust.

If the host city betrays the alliance:

- Allied garrison formations remain loyal to their owners
- They may become hostile forces inside the city
- Internal combat may begin
- The external walls do not prevent engagement
- Outside alliance forces may coordinate with the internal garrison

If the owner of garrisoned troops betrays the alliance:

- Those formations may become hostile forces already inside an allied city
- They may attack internal objectives
- They may contest gates
- They may disrupt defenses
- They may coordinate with outside forces

Trusted access creates both military power and vulnerability.

`External enemies must breach the walls. Trusted armies were invited beyond them.`

### Allied Garrison Commitment

A player who expects to be absent may reinforce an allied city before hostile forces arrive or an active siege begins.

After the player activates a Peace Shield:

- Their home city is protected
- Their gathering formations stop gathering
- They cannot participate in new offensive or contested actions
- Their formations already stationed inside the allied city remain part of that city's defensive garrison
- Those garrisoned formations are not protected by the owner's Peace Shield
- Those formations remain subject to the normal combat rules of the city where they are stationed

The Peace Shield protects the player's own kingdom. It does not extend protection to formations stationed inside another kingdom.

Reinforcing after combat begins is different. Once an enemy attack, field battle, or siege is already underway, sending new reinforcements into the contested area is an offensive field intervention.

Therefore:

- Reinforcing an allied city before a siege begins is permitted
- Sending formations into an active field battle breaks the Peace Shield
- Sending formations through an established siege to reinforce the city breaks the Peace Shield
- Joining an active relief operation breaks the Peace Shield
- Intervening after seeing where the enemy committed forces breaks the Peace Shield
- The full Divine Wrath effect associated with the broken shield applies

Pre-positioned defense is a commitment made before the battle. Entering an active contested area is military power projection.

### Besieged Garrison Commitment

Once an allied city is under siege, allied formations already stationed inside cannot simply be recalled.

The city is physically surrounded, blockaded, or actively contested. Formation ownership does not provide teleportation.

Garrisoned allied formations:

- Remain committed to the city defense
- Participate in defensive combat
- Can suffer wounds
- Can suffer permanent casualties
- Can lose strength
- Can lose morale
- Can gain formation XP
- Can gain veterancy
- Can earn battle honors
- Can develop permanent battle history
- Cannot instantly return home through a normal recall command
- Do not become protected because their owner activates a Peace Shield elsewhere

### Fighting Withdrawal

Garrisoned allied formations may attempt to escape a besieged city through a Fighting Withdrawal.

Fighting Withdrawal is always an available option for garrisoned allied reinforcements trapped in a siege. It is not only for shielded players.

A Fighting Withdrawal is not a normal recall command and does not teleport formations home. It is a physical attempt to disengage from the besieged city and move through hostile or contested territory toward friendly, uncontested territory.

The withdrawing force may need to:

- Exit through an intact gate
- Exit through a usable breach
- Move through a partially controlled route
- Break through enemy screening forces
- Disengage while under pressure
- Abandon equipment or supplies
- Accept reduced offensive effectiveness
- Accept reduced formation cohesion
- Risk casualties, permanent losses, morale damage, pursuit, encirclement, capture, destruction, or being forced back into the besieged city

Ordering a Fighting Withdrawal is classified as defensive disengagement, not an offensive action.

Therefore:

- A shielded player may order garrisoned formations to attempt a Fighting Withdrawal
- Issuing the order does not break the player's Peace Shield
- No shield lockout is triggered
- The player's home kingdom remains protected
- The withdrawing formations receive no protection from the owner's Peace Shield
- The withdrawing formations remain fully vulnerable while escaping
- Enemy forces may detect, intercept, pursue, capture, rout, or destroy them
- The withdrawal may fail
- Surviving formations may be forced back into the besieged city

A Fighting Withdrawal permits an attempted extraction, not a protected extraction.

A Fighting Withdrawal cannot be used as disguised offensive movement because it has no optional redirect. The permitted and only objective is to disengage from the besieged city and return toward the owner's home city or friendly uncontested territory on the way home.

A withdrawing force cannot be redirected to:

- Attack an unrelated enemy target
- Capture hostile territory
- Capture contested territory
- Claim contested goods or resources
- Reinforce another active battle
- Join an offensive rally
- Join a siege
- Enter an enemy city
- Reposition into an offensive operation

If the withdrawing force belongs to a shielded player and successfully breaks free of the siege perimeter, it falls under the owner's sanctuary as Divine Intervention for the purpose of ending pursuit and preventing further combat against that force. The withdrawal battle still happened: wounds, morale damage, equipment loss, XP, honors, capture outcomes, and history remain. Permanent losses from the final interrupted withdrawal engagement are converted to wounded under the normal Divine Intervention rule.

If the withdrawing force belongs to an unshielded player, a successful Fighting Withdrawal simply returns the surviving formations toward home or to the nearest valid friendly uncontested recovery point under normal movement and pursuit rules.

In either case, the player does not get to steer the freed force into a new operation. It continues home or to the nearest valid friendly uncontested recovery point.

Fighting Withdrawal success may depend on:

- Enemy encirclement strength
- Enemy field control
- Enemy screening formations
- Enemy cavalry presence
- Enemy scout coverage
- Detection of breakout preparations
- Controlled escape routes
- Gate and breach condition
- Withdrawing formation strength, morale, veterancy, current-tier mastery, cohesion, movement speed, and fatigue
- Commander traits
- Selected withdrawal tactics
- Terrain and weather
- Whether the host city coordinates a sally
- Whether allied relief forces create an escape corridor

Possible outcomes:

- Clean withdrawal
- Successful withdrawal with minor casualties
- Successful withdrawal with heavy casualties
- Partial escape
- Some formations escape while others return to the city
- Equipment or supplies abandoned
- Formation cohesion damaged
- Formation routed
- Formation captured
- Formation destroyed
- Withdrawal fails and surviving formations return to the besieged city

### Coordinated Breakout And Relief

A Fighting Withdrawal may be supported by allied military action.

Possible support actions:

- The host city launches a coordinated sally
- Allied field armies attack part of the siege perimeter
- Cavalry creates a temporary escape corridor
- Ranged formations suppress enemy screening forces
- Scouts identify a weak section of the encirclement
- Rangers conceal breakout preparations
- Engineers create or stabilize an alternate exit
- Diversionary attacks pull enemy formations away from the withdrawal route

These actions may increase withdrawal success, but supporting players are conducting active military operations and are subject to normal shield rules.

The withdrawing player's order remains defensive disengagement and does not break their shield. Any other shielded player who launches an attack, joins a relief force, or enters contested territory breaks their own shield normally.

### Shield And Siege Design Intent

The system should avoid magical recalls, consequence-free troop extraction, and protected military power projection.

Core principles:

- Geography matters.
- Protection prevents future losses but does not reverse existing consequences.
- A shield protects a kingdom; it does not make every formation owned by that player invulnerable.
- Pre-positioned allied reinforcements are meaningful commitments.
- Entering an active contested battle is power projection.
- Leaving an active contested battle is defensive disengagement.
- Fighting Withdrawal allows an attempt to escape; it does not guarantee escape.
- Armies trapped inside a besieged city must remain, receive outside relief, coordinate a sally, or physically fight their way out.

This preserves player agency without removing military consequences. A player who reinforced an ally before leaving may return to find that their formation survived, suffered losses, gained experience, earned honors, or developed lasting history.

## Reputation And Historical Titles

Reputation is not a single morality score.

The game does not reduce history into:

- `Traitor: -100`
- `Savior: +150`
- `Net reputation: +50`

Instead, titles are chronological records of deeds.

Player titles should be:

- Automatically awarded from actual actions and outcomes
- Permanent
- Non-removable
- Non-hideable
- Displayed in the order earned
- Visible during alliance applications
- Impossible to buy, equip, reroll, or erase with money

A player can hold contradictory titles because history can be contradictory.

Example:

- `Traitor of the Iron Pact`
- `Savior of Rosewatch`

Both may come from the same battle. The player betrayed one alliance by attacking allied forces and saved another city by being the only outside force to arrive in time.

The game does not decide which interpretation is morally correct.

### Alliance Applications

When a player applies to an alliance, leadership sees the player's earned titles in chronological order.

Example:

- `Defender of Blackvale`
- `Traitor of the Iron Pact`
- `Savior of Rosewatch`
- `Shield of Greyhaven`

Titles cannot be hidden or reordered.

Context changes interpretation. One officer may see a traitor. Another may know the title was earned by turning against an army that was attacking an innocent ally.

The game provides history. Players make judgments.

### Defender And Savior Titles

Most meaningful voluntary siege responders may receive:

`Defender of [City]`

This recognizes meaningful defensive commitment without requiring victory. A player may earn `Defender` even if the city falls.

`Savior of [City]` is rarer.

A Savior title should require that the player:

- Responded to an ongoing siege without obligation
- Was the only outside intervention, or the uniquely decisive outside intervention
- Entered when the city was losing, collapsing, or likely to fall
- Materially changed the battle trajectory
- Contributed causally to the city surviving

Savior should not be awarded merely for:

- Joining a winning defense
- Being one of many routine responders
- Dealing the most raw damage
- Having the largest army
- Arriving shortly before victory
- Meeting a visible checklist

Design principle:

`When a city was likely to fall and nobody else came, this player arrived and changed history.`

### Hidden Title Requirements

Exact title requirements should not be published in-game.

There should be no achievement checklist showing exact thresholds like defender win probability, battle impact percentage, or contribution cutoffs.

Players discover titles through events and community discussion. This keeps titles from becoming optimized farming objectives.

Broad patterns may eventually be understood. Exact calculations remain hidden.

## Formation Legacy Titles

Persistent formations can earn titles just as players can.

Formation titles are based on:

- Battlefield behavior
- Extraordinary survival
- Repeated tactical use
- Victories
- Defeats
- Withdrawals
- Last stands
- Unit culture
- The way commanders repeatedly employ that formation

Formation titles are attached to the specific formation.

They cannot be:

- Manually assigned
- Transferred
- Purchased
- Selected from a menu
- Equipped onto another formation

Player titles answer:

`What kind of ruler has this player been?`

Formation titles answer:

`What has this military institution experienced, and what has it learned to be?`

Formation titles may have:

- Visible effects that represent known reputation
- Hidden traits that represent deeper institutional behavior

Hidden effects are not disclosed in tooltips. Players may notice patterns through battle reports and community theory.

### Example: The Bulwark

A Heavy Infantry formation may earn:

`The Bulwark`

Possible earning context:

- It was the only surviving formation in a major siege
- It remained after allied formations were destroyed, routed, captured, or removed
- It continued holding under catastrophic conditions

Possible visible effects:

- Increased morale resistance while isolated
- Increased defense when it is the final friendly formation holding
- Reduced permanent-loss share when it is the final friendly formation holding

Possible hidden effect:

- While truly isolated as the last holding formation, casualty resolution preserves enough institutional core for the formation to survive as a shattered cadre instead of being erased

The enemy may still win, capture the objective, take the city, overwhelm the formation, reduce it to negligible strength, and force a long recovery. The title protects legacy, not victory.

This effect should be capped and carefully tested before implementation.

### Example: The Aggressive

Light Cavalry or Heavy Cavalry may earn:

`The Aggressive`

Possible earning behavior:

- Repeated aggressive commitments
- Rapid exploitation of exposed flanks
- Frequent pursuit
- Willingness to engage dangerous matchups
- Repeated charges
- Consistently choosing contact over disengagement

Possible visible effects:

- Increased attack while advancing
- Increased charge effectiveness
- Increased pursuit effectiveness
- Reduced withdrawal efficiency

Possible hidden effect:

- Reduced damage from counter-units because the formation has learned how to commit hard without fully exposing itself

This should never fully erase counterplay. It should make the formation distinctive, not unbeatable.

## Morale And Debuffs

Meaningful PvP outcomes affect both the player and alliance.

Failed attack example:

`Stalled Offensive`

- `-2%` troop movement
- `+0.5%` fatigue gained from offensive marches
- `-2%` attack
- `-2%` defense
- `+2%` permanently killed troops on future offensive losses

The debuff should stack with caps and decay over time. A successful meaningful attack can remove stalled momentum or add offensive momentum.

## Casualties

Offensive losses are harsher than defensive losses.

General principle:

- Defenders usually suffer more wounded than permanent deaths.
- Attackers suffer a higher permanent death share.
- Siege failures are expensive.
- Veteran formations can reduce permanent loss rates slightly.

A formation can survive with reduced strength and be replenished rather than deleted.

## Experience And Tiering

All new formations start at `Tier I`.

Tier-up requires:

- Formation XP
- Research unlocks
- Refit resources
- Refit time
- Formation being home and sufficiently intact
- Field experience from ruins, monsters, PvP, or other combat activity

Current XP curve:

| Refit | XP |
| --- | ---: |
| I -> II | 100 |
| II -> III | 250 |
| III -> IV | 500 |
| IV -> V | 900 |
| V -> VI | 1,400 |
| VI -> VII | 2,100 |
| VII -> VIII | 3,000 |
| VIII -> IX | 4,200 |
| IX -> X | 5,800 |

PvE can season units, but should not easily create top-tier war formations.

Players cannot meaningfully tier up formations through safe internal city production alone. The resources for refits can be supported by the economy, but the experience and mastery needed to advance comes from exposure: ruins, monsters, PvP, alliance PvE, defense, sieges, and other field activity.

Daily PvE limits:

- Ruins: capped around `4` runs per day
- Monsters: capped around `100` kills per day

These caps prevent infinite safe grinding while still giving active players daily progression routes.

PvP is the primary source of meaningful formation experience. PvE provides controlled progression, but should not replace war experience.

PvE XP scaling:

- Ruins grant roughly `60%` of the expected XP for their tier
- Monsters grant roughly `40%` of the expected XP for their tier
- PvP, sieges, defenses, and alliance war actions grant the strongest experience because they carry real risk

PvE XP sources include:

- Patrols and small monsters
- Standard monsters
- Elite monsters
- Ruins scouting
- Ruins combat rooms
- Ruins gates and obstacles
- Ruins bosses
- Horde events
- World bosses
- Alliance PvE raids
- Alliance fortress sieges

Siege XP is intentionally hard to earn. Siege gets poor XP from ordinary monsters and better XP from ruins gates, obstacles, fortress sieges, and alliance siege events.

## Current Prototype

The current combat simulator lives in:

- `combat-simulator/index.html`
- `combat-simulator/src/model.js`
- `combat-simulator/src/combat.js`
- `combat-simulator/src/app.js`
- `combat-simulator/styles.css`

It currently supports:

- Formation-scale armies
- 14 troop classes
- Tiers I-X
- Veterancy levels
- Formation roster names
- 5-type march limits
- City, field, resource, and rally battle types
- City bombardment and breach checks
- Defender sally option
- Morale/debuff display
- PvE XP and tier XP tables
